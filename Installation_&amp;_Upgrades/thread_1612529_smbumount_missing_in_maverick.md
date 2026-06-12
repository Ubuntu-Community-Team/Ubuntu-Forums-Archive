---
title: "smbumount missing in maverick"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by obley on 2010-11-03
Last night I upgraded from 10.04 to 10.10. I have a job that mounts an smb share, rsyncs, then unmounts but smbumount is no longer available. Anyone out there know what package I'm needing, or what has replaced smbumount?

```

#!/bin/bash
synclog=/home/mmoser/logs/rsync_$(date +%Y%m%d).log

#mount destination
smbmount //192.168.76.11/_darcyDump /media/dump -o username=xxx,password=xxx,uid=mmoser rw

#kick off sync
rsync -rltEvqz --del --log-file=$synclog /storage/ /media/dump

#clean up
smbumount /media/dump/

```

thanks!

---

### Post by pdc124 on 2011-01-07
did you fix this - ive got a bash scripts that mounts and unmounts windows shares and its stopped working . 
smbmount works but smbumount generates and error

---

### Post by obley on 2011-01-07
> **pdc124 said:**
> did you fiux this - ive got a bash scripts that mounts and unmounts windows shares and its stopped working . 
smbmount works but smbumount generates and error

oh yea, Sorry. I should have posted for posterity. 

You want to use: umount -f /mount/path

Here is my updated script:
```

#!/bin/bash

synclog=/home/mmoser/logs/rsync_$(date +%Y%m%d).log
dir=/media/dump/www

if [ ! -d "$dir" ]; then
  #mount destination
  smbmount //192.168.76.11/_darcyDump /media/dump -o username=xxx,password=xxx,uid=mmoser rw
fi

if [ -d "$dir" ]; then
  #kick off sync
  rsync -rltEvqz --del --log-file=$synclog /storage/ /media/dump
  #clean up
  umount -f /media/dump
else
  echo "mount failed, check IP"
fi
```

I've also thrown in some mount checks since my last post.

---

### Post by legendbb on 2012-11-22
Just to add on my ubuntu 10.10, $ sudo umount -f /mnt/SMBShared doesn't work.

I have to $ sudo su to do the same thing.

Don't understand why but it worked.

---

