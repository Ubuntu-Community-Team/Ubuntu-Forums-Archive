---
title: "2 drives, Vista on one, Ubuntu the other"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by jwright444 on 2008-03-11
Here's my problem & I hope someone can help.

I had Vista installed on drive0 then installed a larger drive at drive1 and did a fresh Vista install to drive1.  I then installed Ubuntu over the disabled Vista installation on drive0 figuring I could control the boot sequence somehow.  Now I boot straight to Ubuntu and can't boot to Vista.  Even if I disconnect drive0, Vista is not found on drive1.  Seems installing Ubuntu on drive0 messed with the MBR.  Is there a way for me to recover access to Vista on drive1?

I'm really hoping I won't have to reinstall Vista.

Thanks in advance!

---

### Post by confused57 on 2008-03-12
> **jwright444 said:**
> Here's my problem & I hope someone can help.

I had Vista installed on drive0 then installed a larger drive at drive1 and did a fresh Vista install to drive1.  I then installed Ubuntu over the disabled Vista installation on drive0 figuring I could control the boot sequence somehow.  Now I boot straight to Ubuntu and can't boot to Vista.  Even if I disconnect drive0, Vista is not found on drive1.  Seems installing Ubuntu on drive0 messed with the MBR.  Is there a way for me to recover access to Vista on drive1?

I'm really hoping I won't have to reinstall Vista.

Thanks in advance!
You could try using your Vista install DVD to restore your mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Then you could try installing grub to Ubuntu's root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once you install grub to the root partition, you could try EasyBCD to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by undecidable on 2008-03-12
1.  did you ever use Vista on drive 1?
W/XP and W2000 for example don't like to be booted from other than drive 0,
even if you have set up you bootloader etc correctly.

But assuming 1., is OK:

2.  You want Grub to give you the choice of booting to Ub on drive 0 or Wz Vista on drive 1.
This is usually most easily accomplished by editing  /boot/grub/menu.lst.

3.  However can I suggest that what you are doing is complicated,
especially any attempt to move Vista,
and double especially moving it to drive 1
then you need serious backgrond knowledge to do it properly.
and are unlikely to luck into a shortcut.  

If confused57's method does not work for you,
or you are not up to editing the menu.lst file
and understanding the boot process
then you might be better off re-installing Vista - 
it could be a faster route than trying to become a guru of booting.

Hope this helps.

mc

---

### Post by confused57 on 2008-03-12
Undecidable has a good point, I believe it may be more complicated than I initially thought, since you still had the old Vista on the 1st hard drive when you installed the new Vista on the 2nd.  It's possible the new Vista installed it's IPL to the 1st drive's mbr and the boatloader to the old Vista.  You can try the suggestions I gave you earlier, definitely nothing to lose by doing so.

---

### Post by Computer Guru on 2008-03-13
Recover the Vista MBR to whatever drive you'd like by following the instructions at [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Once that's done, you'll be able to boot into Vista. From there you should be able to use EasyBCD to add an Ubuntu entry to the Vista menu quite easily.

Cheers!

---

