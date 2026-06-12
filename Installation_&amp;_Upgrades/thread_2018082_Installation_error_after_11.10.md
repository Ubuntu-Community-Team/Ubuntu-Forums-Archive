---
title: "Installation error after 11.10"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by BlackWolfe on 2012-07-05
Noob who knows very, very little about Ubuntu first.

Have been having install errors on a WD Passport HD.

I completely formated the drive to wipe out anything (including old installations) that were on there (I had been using Ubuntu just fine until the last update) per another thread that helped me find out how to do that. Done.

Installed 11.10 from the LiveCD (which is the version I was running prior to all this). 
After installation and reboot I get this error:

error: invalid extent
grub rescue:

Still don't quite understand what 'grub' is or how it works but I am getting there.
Anyone have any suggestions on what steps to take next? I have no idea what grub rescue is or how to take advantage of it. 

Thanks ahead of time.

---

### Post by dino99 on 2012-07-06
grub is the boot loader :p
seems you have not it installed. It can be installed from livecd:

sudo grub-install /dev/sda

but maybe you need to check about installation first:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

more info below ):P

---

### Post by BlackWolfe on 2012-07-06
Thanks for the advice. WIll do.

---

