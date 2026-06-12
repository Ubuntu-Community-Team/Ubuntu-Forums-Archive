---
title: "GRUB error"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by gemmahenchmen on 2010-04-25
I accidentally deleted the GRUB partition on my machine from windows, and now when I restart the BIOS doesn't respond to commands and it then displays```
grub: no such partition.
grub restore>
```I tried using the command```
set root=(hd0,1)
```to make it boot from my windows partition, but when I restart the computer it does the same thing, and when I type ```
set
``` it displays ```
root=(hd0,5)
``` which is the old GRUB partition. 

How can I save the changes I have made for when I restart. Also, I know that a partition on my machine is a restore partition, either (hd0) or (hd0,1). How can I save my computer?

PS: I have already backed up all of my files. The computer also doesn't boot up from any disks I insert, such as the Ubuntu Live CD.

---

### Post by quixote on 2010-04-26
Windows doesn't play nice with other OSes, so I believe you need to fix that first and then fix your grub install.  But if your system isn't booting from CD either, I'm not sure how to tell you to proceed. :(

I'm also not sure what's going on in your system.  The BIOS is the bit at the very beginning, just after you turn on your computer, before you ever get to grub.  When you say "the BIOS doesn't respond to commands" which commands do you mean?  Give an example, because it doesn't sound to me like you really mean BIOS. 

After the BIOS you get the bootloader -- grub is one kind of bootloader -- which then gets the operating system to start up.  Grub is not usually in its own partition.  It's often in the Master Boot Record (MBR) which is also where the Windows bootloader lives.  Is it the MBR you deleted?  

The restore or recovery partition will relate only to Windows, and is accessible only through a Windows recovery disk.  If I remember right, it's only use is to put a factory default windows install back on your system and wipe everything else on your computer.

The way grub gets Windows to boot is it points to the Windows bootloader.  (That's what that "chainloader +1" stuff in the grub files is about.)  So even if grub was working, it couldn't boot windows by itself.  That's why the set root=(hd0,1) doesn't do anything.

The fact that your boot setup is messed up should not affect the ability to boot from a live CD, so 1) maybe that CD is bad.  Which other bootable CDs have you tried in that drive?  Or 2) The CD drive is bad.  Or 3) The problem is much bigger and more serious than just a blown up boot record. :( :(

Okay.  On to maybe some fixes. 

If you can get it to read other CDs, get a Windows Recovery CD or any Windows bootable media.  (A DOS floppy, if you had a floppy drive, would work!)  Once you have a command prompt, type "fixmbr" (without quotes) and that should fix the boot record for Windows and enable you to boot at least that OS.

Before trying to fix grub, we need to know which version of Ubuntu you're running because Karmic and Lucid use Grub2 which is very different from grub-legacy on older versions.

The thing to remember is that all your data and OSes are all still there.  It's just the booting, or maybe the CD, that doesn't work and those can be fixed.

---

