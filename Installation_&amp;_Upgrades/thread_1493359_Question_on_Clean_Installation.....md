---
title: "Question on Clean Installation...."
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by jrredho on 2010-05-25
Hey All,

I've finally come to grips with the fact that I need to install a 32-bit version of Ubuntu (I'm currently running 9.04/64-bit) to allow myself to use WebEx for which there is no 32-bit support.

Anyway, heaven knows how many packages/software sources I've got currently loaded. So, my question is: Is there a relatively painless way to do the fresh install I'm looking to do that allows me to retain all the packages/software sources/keys, etc?

many thanks,
john

---

### Post by oldfred on 2010-05-26
If you have a separate /home that saves your user settings.But if you have some special system settings you may need to copy those from /etc. I have separate /home and /data so my root partition is only about 6GB. I keep my last install, current install and a partition for the beta to test the next install. Each root is about 20-25GB.

this will list all the programs you have installed and then you can reinstall. If any are 64 bit I would assume they will not install.

I have had no problems with 64bit.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by jrredho on 2010-05-26
Hey oldfred,

Thanks for your helpful response.  I'm not looking forward to this since, over the past three or four years, I've added a number of non-official packages for which I'll have to re-track down the gpg keys one-by-one.  Sigh.

As for this...

> **oldfred said:**
> 
I have had no problems with 64bit.


...then I can only say that you haven't tried to use WebEx conferencing: The owners of WebEx do not support 64-bit linux.  The work-arounds I've tried have created a massive hornets nest of 32-bit  and 64-bit versions of firefox/flash/java/etc that I've now just hit the wall trying to manage.

Thanks again!

cheers,
john

---

