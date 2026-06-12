---
title: "Ubuntu is installed, but is MIA during boot"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by johnnywad on 2008-04-15
Okkkkkk,

I have a PC with 6 hard drives in it.

Under Windows, Disk 0, Partition 0 is formatted as NTFS and is the boot primary boot partition that contains Win XP.

I installed Ubuntu on Disk 4 Partition 0 and during setup I had the installer put grub on hd0.

Installation finished and I rebooted the PC, expecting to see the boot menu to load either XP or Ubuntu.

What I got was the usual XP boot menu... Ubuntu was nowhere to be found.

As I said, XP is on what it considers Disk 0, Partition 0.  During setup of Ubuntu, however, the XP boot partition was identified by Ubuntu as /dev/sdd1.  I dunno if that's causing my problem or not.  Shouldn't grub have been placed on /dev/sdd1?  

Anyone have any suggestions?  Feel free to talk to me as if I'm a moron who doesn't know jack schitt about Linux, because I don't.

---

### Post by tvtech on 2008-04-16
you need to set your bios.  efi boot loader *thing that boots your machine*   to point to the disk that you think you have grub installed on.  from what you've said you didn't overwrite your MBR with grub.  so perhaps it's landed some place else.  just keep pointing it at drives until you find it.

I had a similar problem when I was installing on an unusual config.  2 ide on 1 chain 2 scsi on an adaptech controller and 2 sata on a 3ware controller.

---

### Post by wolfen69 on 2008-04-16
yeah, in laymans terms just make sure the computer is set up to boot to the windows drive where grub is installed.

---

### Post by johnnywad on 2008-04-17
Ahhhh.... now I get it.

I found the correct boot drive on the 3rd try

I will admit I wasn't sure what you guys were telling me to do.  I kept saying to myself "How's it going to boot if I set a different drive to be the boot drive?"

My confusion was that I mistakenly thought NTLDR had to run and provide the option to boot into Ubuntu, but it's the other way around... grub has to load so it can provide the option to load WinXP.


**EDIT:**

I spoke too soon.  I now get the grub menu to boot into the various Ubuntu configurations, along with Windows XP listed at the bottom.

If I choose to boot Ubuntu, everything proceeds normally.

However, if I choose Windows XP from the grub menu, I get something like: 

NTLDR is missing
Press Ctrl Alt Del to Restart

The only way I can boot into XP is to go into the BIOS setup and change the boot disk back to the disk where XP is installed.

Any suggestions?

---

### Post by 222fbj on 2008-04-17
My twist on this.... I installed Ubuntu on a secondary IDE disk..and now I realize my bios has no option to specify which IDE drive to boot from - only "HDD".  Is the solution to play with IDE cables/pins to make the 'ubuntu' drive my primary IDE boot device?

I'm guessing that would let me boot Ubuntu (pls confirm;=)... but how does GRUB then know where the Windows IDE drive is (since I moved it after installing ubuntu)?

Or - as is often the case - maybe I've made this more complicated than it is - that would be good to hear.

thanks for any advice.

---

