---
title: "Fails to boot after 1st install"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Myboyjim on 2010-05-20
Hi,

I have Vista on my Samsung R60 + and have installed Ubuntu.
On start up I get the dual boot option, select Ubuntu which then goes to completeing install etc, get some HD activity then nothing.

Hope someone can help or point me in the right direction.

Thanks

Rich

---

### Post by oldfred on 2010-05-20
to get your system to work for the install did you make any special settings?

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

Above applies to many video cards but total solution may be different.

Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

