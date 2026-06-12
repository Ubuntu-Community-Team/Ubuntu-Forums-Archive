---
title: "Menu.1st overwritten with no ubuntu boot option"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by stefcep on 2009-12-06
Hi All

Been dual booting 9.04 and Vista happily until I did a kernel update to 2.6.28.17 to day.  I was asked to update menu.1st after the update.  But I didn't know what this might do to my boot menu I said no.  Probably was the wrong thing.  Now the only boot option I have is Vista.  I booted with the livecd and was able to read the menu.1st in boot/grub and found that all my previous Linux kernel boot options were removed and there is only an entry for Vista.

Can anyone advise on how I can re-instate Ubuntu as a boot option?

---

### Post by tom4everitt on 2009-12-06
Your ubuntu entry should look like this:

title    Ubuntu
root     (hdX,Y)
kernel   kernelpath ro quiet splash
initrd   some-intird.img


A really good grub guide:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by phillw on 2009-12-06
Hi,

Head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you're on 9.04, unless you have specifically upgraded your Grub, you'll be on Grub legacy.

That'll get you up & running in no time.

Regards,

Phill.

---

### Post by lswb on 2009-12-06
Usually when an update changes menu.lst it saves a copy first to a file named menu.lst~
Boot from your live CD again and check for menu.lst~ and see if it contains the boot lines for linux. They will probably be for the kernel you were running before the update. 

Save the "bad" menu.lst just in case, then rename (mv) menu.lst~ to menu.lst. You should be able to boot and then from a terminal "sudo update-grub" should add the new kernel.

---

### Post by stefcep on 2009-12-07
Thank you, I got it working again.

Not sure why it didn't back-up menu,1st before over-writing it though.

---

