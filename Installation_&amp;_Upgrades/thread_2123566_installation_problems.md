---
title: "installation problems"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by johnsg on 2013-03-08
Hi all,
I'm trying to install Ubuntu 12.10 (64 bit) on a Dell T7600 (with PERC H310 controller for 4 hard drive RAID) using the Linux-Secure-Remix with BootRepair.  The BootRepair url is:

[http://paste.ubuntu.com/5596165/](http://paste.ubuntu.com/5596165/)

I've checked that my BIOS boots in UEFI mode and it appears to be pointing to ubuntu. When I restart my computer I get to the GNU GRUB menu list. When I select either 'Ubuntu' or 'Advanced options for Ubuntu' I get taken to a screen that says:

  error: attempt to read/write outside of disk 'hd0'
  error: you need to load the kernel first.

  Press any key to continue...

Also concerning is that when I change to legacy boot and try to run the live-usb to access "Try Ubuntu", I"m no longer able to...just get to a hanging dark screen.
 
Any help getting past this greatly appreciated!

---

### Post by Garcon001 on 2013-04-22
johnsg I am having a similiar problem with my install of Ubuntu 12.10 (64x) on a Dell T620 (with a PERC H310 RAID Controller). were you able to find a solution to your problem and did you do a software raid from Ubuntu or use a hardware Raid?  Using the hardware RAID I'm unable to install GRUB2, using a software RAID it will install but boot only to the grub rescue prompt.

Any insight on your install would be helpful.

---

