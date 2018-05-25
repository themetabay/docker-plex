## Forked from: https://github.com/plexinc/pms-docker

# Information:
More information can be found here: https://github.com/plexinc/pms-docker

This fork exands on the healthcheck for verifying media folders are mounted, more to come.

# Requirements
- The healthcheck file should exist somewhere in the /data folder with your media files and be present only when your folders are mounted correctly. Docker will be checking to see that the file exists and mark Plex as Unhealthy when your media is missing.

# Run example:
```
docker run -d \
  --name plex \
  --network=host \
  --cap-add SYS_ADMIN \
  --privileged \
  --restart unless-stopped \
  -e TZ="<timezone>" \
  -e PLEX_CLAIM="<claimToken>" \
  -e HEALTHCHECK_FILE="/data/healthcheck.file" \
  --volumes-from plex.config \
  --volumes-from plex.transcode \
  --volumes-from rclone:rw \
  themetabay/plex:latest
```
