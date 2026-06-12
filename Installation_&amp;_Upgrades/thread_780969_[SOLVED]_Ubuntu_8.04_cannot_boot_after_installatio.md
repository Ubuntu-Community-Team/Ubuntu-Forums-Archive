---
title: "[SOLVED] Ubuntu 8.04 cannot boot after installation with option acpi=off"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by tigerchan on 2008-05-03
Hi all,
    I installed Ubuntu 8.04 from hard disk with the alternative iso. For the first time the installation stopped after the following lines appeared:
"PNP: No PS/2 controller found. Probing ports directly."
"Serio: i8024 KBD port at 0x60,0x64 irq 1"
"Serio: i8024 AUX port at 0x60,0x64 irq 12"

    I added the installation option "acpi=off" according to suggestions from the forum. With the option, the installation ended successfully. But when rebooting, whichever I chose normal or safe mode from the grub menu list, the booting process stopped immediately. An uppercased "F" appeared at the head of a line, together with a blue block with the width of a character in the middle.
    The following are some info of my pc:
    BIOS: DELL OptiPlex 320
    CPU: Intel PentiumD 3G
    RAM: 512M
    Keyborad and Mouse: USB

    Can anybody give a hand? Thanks.

---

### Post by xyphur on 2008-05-03
Someone else correct me if I am wrong here, but I believe that if your machine required the acpi=off boot switch, you'll have to echo that switch in the /boot/grub/menu.lst file as well after installation... why the installer doesn't migrate the settings used to boot during installation is anyone's guess - if you ask me, it should.

The easiest method to do this is to boot up a LiveCD and edit the file from there. Alternatively, you could theoretically edit the file from a Windows machine with the Ext2 IFS driver installed enabling access to your Linux partition.

Again, this would be a non-issue had the installer passed the custom boot options/switches on to the menu.lst file after the install had finished successfully. Perhaps in the future we can hope for this to be fixed...

---

### Post by tigerchan on 2008-05-04
Thank xyphur for your reply.
I tried to boot the new installed Hardy with option "acpi=off", once by pressing "E" on choosing the grub menu, and for another, by editing the /boot/grub/menu.lst file from another OS. Unfortunately, the result was the same.

And, is it possible that my display driver,which is ATI Radeon Xpress 1100, causes this problem?

---

### Post by xyphur on 2008-05-04
...this is of course possible, especially if your installation is configured to use a different display driver. Unfortunately, I am not experienced in ATI hardware. I had an ATI Radeon Mobility M6 LY in my Dell laptop just long enough to search for an nVidia replacement on eBay. When it arrived, I swapped it out and continued hapily into 3D-accelerated linux, without issue.

I have heard though that ATI has spotty drivers under Linux and they cause more headaches, generally, than they are worth... of course, your mileage may vary, and truthfully as I said before, I'm not at all qualified to pass judgement on ATI drivers or products - I know enough to know that I wanted an nVidia card for this machine to evade any possible ATI driver issues I may have encountered under Linux - and in that regard, I suppose I succeeded :P

Sorry I couldn't be of more assistance... I'm sure someone else will pipe up and help you along to get this issue resolved. Best of luck.

---

### Post by zgoda on 2008-05-15
> **tigerchan said:**
> I added the installation option "acpi=off" according to suggestions from the forum. With the option, the installation ended successfully. But when rebooting, whichever I chose normal or safe mode from the grub menu list, the booting process stopped immediately. An uppercased "F" appeared at the head of a line, together with a blue block with the width of a character in the middle.
    The following are some info of my pc:
    BIOS: DELL OptiPlex 320
    CPU: Intel PentiumD 3G
    RAM: 512M
    Keyborad and Mouse: USB

    Can anybody give a hand? Thanks.

Optiplex 320 are known to be hostile to linux. Use either grub2 or LILO as your boot loader (LILO is easier to set up). Try with various combinations of hpet=disable, pci=nomsi and acpi=off boot options. Generally, better stay away from these machines if you want use linux. I am sure you'll find detailed instructions on this forum.

---

### Post by tigerchan on 2008-05-16
Thanks for zgoda's advice. I reinstalled Hardy with option "acpi=off", and skipped grub but installed lilo instead. Ubuntu boots successfully with the same boot option.
I just missed the keyword "OptiPlex 320" when searching the forum, and tried lots of bios options such as disabling the USB keyboard/mouse, and tried many others. Anyway, I am happy that ubuntu works at last. Much thanks to xyphur and zgoda!

---

