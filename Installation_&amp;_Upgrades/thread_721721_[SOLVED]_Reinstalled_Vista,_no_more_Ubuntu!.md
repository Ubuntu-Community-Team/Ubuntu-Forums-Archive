---
title: "[SOLVED] Reinstalled Vista, no more Ubuntu!"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by ndrone1 on 2008-03-11
Hey everybody,

I know it will pain everyone to hear, but on my Dell xps m1330, this is my THIRD reinstall of Windows vista since november (windows updates keep crashing it, I love it)....

Regardless, all is well again except for my precious ubuntu partition no longer loading!

I don't even get the boot options through GRUB anymore so I can no longer boot into Ubuntu (7.10 feisty fawn fyi)... the computer boots straight into Vista.

What do I do?

Note:
As a hopeful quick fix, I downloaded EasyBCD and tried to just add a -new Linux/GRUB/picked the right partition- loader but that didn't work either... I get the GRUB-like operating system chooser when I start the computer now, but I get a "Please insert systemdisk" when I choose Ubuntu along with some generic error...

I also tried to insert the system disk to no avail. And upon starting the computer from the cd drive, all I get is the installation options again or to run as a live user...

Someone help? Please?
I miss Feisty already.

Thanks,
Nate

---

### Post by Pumalite on 2008-03-11
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by beansdad on 2008-03-11
Can't solve this one other than to suggest you bin Vista and go Ubuntu alone!

---

### Post by patrickaupperle on 2008-03-11
> **ndrone1 said:**
> Hey everybody,

I know it will pain everyone to hear, but on my Dell xps m1330, this is my THIRD reinstall of Windows vista since november (windows updates keep crashing it, I love it)....

Regardless, all is well again except for my precious ubuntu partition no longer loading!

I don't even get the boot options through GRUB anymore so I can no longer boot into Ubuntu (**7.10 feisty fawn fyi**)... the computer boots straight into Vista.

What do I do?

Note:
As a hopeful quick fix, I downloaded EasyBCD and tried to just add a -new Linux/GRUB/picked the right partition- loader but that didn't work either... I get the GRUB-like operating system chooser when I start the computer now, but I get a "Please insert systemdisk" when I choose Ubuntu along with some generic error...

I also tried to insert the system disk to no avail. And upon starting the computer from the cd drive, all I get is the installation options again or to run as a live user...

Someone help? Please?
I miss Feisty already.

Thanks,
Nate

I think 7.10 is gutsy, am i wrong?

---

### Post by Bölvaður on 2008-03-11
Am I right that Vista is changing the MBR (master boot record)?


7.04 is Feisty and 7.10 is Gusty (8.04 will be Hardy)

---

### Post by Pumalite on 2008-03-11
Keep in mind this too:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by ndrone1 on 2008-03-11
Alright. Thanks to all of your geniusness, everything is up and running just fine. (for now - until vista crashes inevitably soon)

THANKS!

I'm not sure how to mark this as closed... but it can be!

---

