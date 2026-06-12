---
title: "Bootloader never installed"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by BobSock on 2007-06-02
I'm somewhat new to linux and have dual-booted XP with SUSE for around a year now. I decided to try Ubuntu for it's famous, user friendly package manager. 

I downloaded Kubuntu 7.04 (i386), booted it, installed it from the live cd, everything seemed to go fine. I was told to remove the cd and restart the computer; I did this but when it boots there is no bootloader, it just boots straight into Windows.

My Windows XP is on my ~300GB sata drive and I installed ubuntu on a partition on my secondary IDE drive (6.5 GB free for the ubuntu installation). I also removed the suse and it's  bootloader before installing ubuntu.

Any suggestions? :???:

---

### Post by Herman on 2007-06-02
Hello BobSock,
I wonder if the IPL for Grub has installed in (hd1), your second hard disk,instead of in (hd0), you first hard disk?
The computer will normally only look in the first hard disk's MBR unless you tell it different.
Try tapping your 'F8' or your 'F12' key during bootup and see if your computer has a manual boot menu, most do nowadays. A manual boot menu from the BIOS allows you to select any disk and boot it.
Here's what that looks like when I do it, link: [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs.

Try that and see if it works,
Regards, Herman :D

---

### Post by BobSock on 2007-06-02
[FONT="Comic Sans MS"][SIZE="3"][COLOR="SeaGreen"]Thank-you very much Herman. Solved my problem completely.[/COLOR][/SIZE][/FONT] :D

I just switched my hard drive boot order and the grub menu came up. What really surprised me was that the menu also had the option to boot Windows XP which I didn't think it would look for/recognize. Now I can just leave my hard drive boot order the way it is in the bios and can pick what I want to boot.

---

### Post by Herman on 2007-06-02
Hey good for you!, I'm happy too, to have been any help. Thanks for the feedback.

If you get tired of booting that way some day, you can also make a backup of your first hard disk's MBR with the Ubuntu Live CD and a 'dd' command, like this,  [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").
Then you can install the IPL for Ubuntu's Grub to your first hard disk's MBR as well like this, [                                                                  Re-install Grub with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.

It's up to you, just do whatever works and whatever makes you happy. The option is there to have Grub in both MBRs if you want it.

My computer has the ability to change the hard disk boot priority in the BIOS as well, [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority"). That's another way around it if you have a BIOS that can do that. You could make your Ubuntu disk act as if it's disk 1 but that may confuse Grub, I can't remember for sure but I think it gave me grub error 18 when I tried it. That may be able to be fixed by editing the Grub menu or maybe re-installing Grub. There are lots of things that can be played around with to make computers boot up the way you like. It can get confusing if you make it too complicated though.

Regards, Herman :D

---

