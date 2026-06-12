---
title: "Sound Config and FAT32 mounting"
date: 2004-12-13
forum: Installation &amp; Upgrades
---

### Post by gdeswardt on 2004-12-13
The last time I installed ubuntu was back in October and I ended up removing it due to the fact that it was  too cutting edge (preview release) and still bleeding to much. 

But now only 2 months later i found that this is best distro I have ever installed. This is actually the first time in 2 years that i installed a distro without having to manually configure or compile something (as yet). Well done this is fantastic. Even my network is automatically configured and I am up and running in no time what so ever. 

I did however run into 2 small problems. I am running a DELL Inspiron 8200 laptop and during installation it did not pickup my sound card settings. Tells me my sound card is not configured.

When i try and mount a FAT32 partition on my local hard drive I can view the root folder, which gives me a list of all the folders but list them as Type "unknown type" MIME Type application/octet-stream. Therefore the partition is not browseable. Here is the command I am using the mount the filesystem

$ mount -t vfat /dev/hda3 /mnt/c
$ chmod 777 /mnt/c

Any help would be much appreciated

---

### Post by taygan on 2004-12-13
You can't chmod a vfat filesystem after it's mounted.  You have to set the umask in the mount command.

See this thread:

[http://www.ubuntuforums.org/showthread.php?t=5534&highlight=vfat+permissions](http://www.ubuntuforums.org/showthread.php?t=5534&highlight=vfat+permissions)

or this thread:

[http://www.ubuntuforums.org/showthread.php?t=2837&highlight=vfat+permissions](http://www.ubuntuforums.org/showthread.php?t=2837&highlight=vfat+permissions)

You can add either a umask=000 and/or set yourself as the owner (gid=1000 uid=1000)

Good Luck!

---

### Post by gdeswardt on 2004-12-14
First of all I want to apologize for not finding the other post. Now that is over I want to say many thanks taygan that helped. 

I also found another post about the sound on a Dell Inspiron 8200 laptop here is the link if anybody finds this post:

[http://ubuntuforums.org/showthread.php?t=486](http://ubuntuforums.org/showthread.php?t=486)

---

