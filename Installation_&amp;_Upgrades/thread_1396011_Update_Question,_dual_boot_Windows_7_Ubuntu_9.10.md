---
title: "Update Question, dual boot Windows 7 Ubuntu 9.10"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by android73 on 2010-02-01
Hello,

I have been running a dual boot system with Windows xp and Ubuntu 9.04 installed for the past year. I have each OS installed on separate hard drives. I recently upgraded my windows operating system to 7, and dual booting is still working fine with legacy grub handling the bootup. I would now like to upgrade my Ubuntu to 9.10. The first question I have is, do I do a network upgrade(which I have read in the forums can be problematic) or do a clean install? If so, how does grub2 differ in how you set it up? I keep reading in these forums that it can be more difficult to set up. Can anyone point me to some threads that explain how to install a dual boot with grub2 with windows 7 already installed? Any help would be greatly appreciated! Thanks.

---

### Post by darkod on 2010-02-01
Clean install is always better than upgrade. There is nothing special you need to do for grub2, in fact, it's the same.
The main thing to remember when using more than one drive, is this:
During install in step 4 remember the name of your ubuntu disk (/dev/sda, /dev/sdb, etc). In the last screen, before clicking Install, click on Advanced and make sure grub2 goes to the same disk.
That's it. In fact, you should always check where grub goes with multiple drives, even for grub1.
That will leave windows bootloader on your win7 disk, and grub2 on the ubuntu disk. If the win7 disk is first in BIOS hdd boot order, obviously win7 will boot straight away. If the ubuntu disk is first, you get the grub2 menu.

---

### Post by android73 on 2010-02-01
Hey, thanks Darkod for the advice! Good to know. Also, when I originally installed Ubuntu for the dual boot, I simply unplugged the windows drive altogether so I didn't mess anything up. I'm assuming I could still do that when I upgrade? I also wanted to ask about the /home partition of my existing Unbuntu install. I have heard that you can keep this partition the same and not lose any of your data or settings. Is this true? Thanks again!

---

