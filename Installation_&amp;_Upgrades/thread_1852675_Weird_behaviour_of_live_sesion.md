---
title: "Weird behaviour of live sesion"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by david0892 on 2011-09-30
I'm trying to install Ubuntu 11.04 but something is not right.
I'm booting from cd, everything's fine till the menu:
[http://ubuntuforums.org/attachment.php?attachmentid=203250&stc=1&d=1317412653](http://ubuntuforums.org/attachment.php?attachmentid=203250&stc=1&d=1317412653)

After 10 seconds everything disappear like magic and I get a black screen with a blinking cursor in top left corner:
[http://ubuntuforums.org/attachment.php?attachmentid=203251&stc=1&d=1317412801](http://ubuntuforums.org/attachment.php?attachmentid=203251&stc=1&d=1317412801)

My PC config is:
AMD Athlon 3 GHz
1 GB DDR
Nvidia GeForce 8400GS 256 mb ddr2

Same thing happen to any version of Ubuntu I'm trying to install(I've also tried with a old version: Ubuntu 8.10)

Anyone can tell me what's happening?Is there anyway to solve this or should I wait till Ubuntu 11.10 is released?

---

### Post by MAFoElffen on 2011-09-30
> **david0892 said:**
> I'm trying to install Ubuntu 11.04 but something is not right.
I'm booting from cd, everything's fine till the menu:
[http://ubuntuforums.org/attachment.php?attachmentid=203250&stc=1&d=1317412653](http://ubuntuforums.org/attachment.php?attachmentid=203250&stc=1&d=1317412653)

After 10 seconds everything disappear like magic and I get a black screen with a blinking cursor in top left corner:
[http://ubuntuforums.org/attachment.php?attachmentid=203251&stc=1&d=1317412801](http://ubuntuforums.org/attachment.php?attachmentid=203251&stc=1&d=1317412801)

My PC config is:
AMD Athlon 3 GHz
1 GB DDR
Nvidia GeForce 8400GS 256 mb ddr2

Same thing happen to any version of Ubuntu I'm trying to install(I've also tried with a old version: Ubuntu 8.10)

Anyone can tell me what's happening?Is there anyway to solve this or should I wait till Ubuntu 11.10 is released?
You have an NVidia Card--> Look at the first half of Post             #[**3**]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3") of my graphics sticky...  You need to select the "nomodeset" option in the kernel boot option pulldown (shift or enter), then hit excape, then select the try or install to boot.

---

### Post by david0892 on 2011-10-01
Your nomodeset worked.
I've installed OS->Reboot->(and poof)black screen with blinking cursor in the top left corner.:confused:

What's going on?I didn't have any problems with Ubuntu before this video card.

---

### Post by 2F4U on 2011-10-01
Can you add the nomodeset again on the installed system? As far as I understand, it will not be carried over from the live session.

---

### Post by Rubi1200 on 2011-10-01
> **2F4U said:**
> Can you add the nomodeset again on the installed system? As far as I understand, it will not be carried over from the live session.
Correct; you need to use it on first boot and then install the drivers.

See the first post here for more details:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MAFoElffen on 2011-10-01
> **2F4U said:**
> Can you add the nomodeset again on the installed system? As far as I understand, it will not be carried over from the live session.
Which means hit the shift key repeatedly while booting up, the Grub Menu will come up.

At the grub menu press the "e" key to put it into an edit mode... Arrow down to the line starting with "linux"... Arrow right to where it says "quiet splash" and add "nomodeset".

Press <cntrl><x> to boot.

After start, go to the "Additional Drivers" under System Settings > Hardware... to install your video driver.

---

### Post by david0892 on 2011-10-04
Sorry for late typing but I've had some problems to solve first:D.

Today I've tried your advice but after rebooting(pressing ctrl+x) crashes and get a msg like this:

Booting a command list

alloc magic list is broken at 0x3fd50d10.
Aborted.Press any key to exit.

As I see that error can be:
1)a bad sector from HDD(solution:a new HDD);
2)sth on kernel(solution:reinstall Ubuntu);

So, new HDD or reinstall Ubuntu?

Or maybe if I could force Xorg to use vesa from grub, install driver.Could work?

Edit:I don't know what kind of error was that with grub menu but I've reinstalled both OS(Windows-<because I had xp sp2,needed to reinstall,moreover for some development tools is required sp3> and Ubuntu-<i've made separate partitions for /tmp and /opt>) and I've installed nvidia driver through LiveCD as MAFoElffen said in his tutorial.

Thank you all for help!

---

