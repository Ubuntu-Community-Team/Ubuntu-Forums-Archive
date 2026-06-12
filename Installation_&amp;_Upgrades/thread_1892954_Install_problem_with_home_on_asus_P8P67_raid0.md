---
title: "Install problem with /home on asus P8P67 raid0"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by rbsbscrp on 2011-12-09
Hi all, ehem... AHHHHHHHHHHHH! I've run Ubuntu x64 on my laptop for years with few problems. Now I've bought a desktop with an Asus P8P67 mboard with a 64gig SSD and 2x2T sata drives config'd in a raid0. Win7 is on the SSD and works fine. I *tried* to install Ubuntu 11.10 amd64 with /boot, root on the SSD  and /home on the raid0 (many times, many ways) and have struck out with what seems like the system not being able to mount the /dev/mapper/xxx partitions. I end up with /dev/mapper/xxx_Volume0 and /dev/mapper/control only. At least I can still choose Win7 from the grub menu and have a computer. 

Ok, the live Cd doesn't load, just hangs. So I'm using ubuntu-11.10-alternate-amd64. I disconnected the network so there are no updates. I've tried several other linuxes and earlier releases but no joy.

Then I found boot-repair and ran it and it sent my info to paste.ubuntu.com/764648 . I tried again (this time choosing the softRAID choice) and the result is pasted on paste.ubuntu.com/764650. I think the problem is that the raid0 is not available. Do I need some kind of (extra/external) driver or something?

All of the info I could google so far deals with different issues except I saw that there used to be a bug (in 9.10 I think) that produced the /dev/mapper/xxx_Volume and /dev/mapper/control situation. 

Thanks in advance for any help.
-

---

### Post by darkod on 2011-12-09
If the script result is correct, it says there is no partition table on /dev/sdc (or is invalid). But this is way over my head to solve, don't want to play with your data.

If there is no important data on the raid, I would go into the raid options, delete the raid array, and using Gparted from ubuntu cd in live mode create new GPT tables on both /dev/sdb and /dev/sdc.
Then recreate the array again.

After that you will probably need to change the /etc/fstab, depends on the new layout.

If there is data on the raid that you don't want to lose, you will have to wait for someone to jump in if they can solve this.

---

### Post by rbsbscrp on 2011-12-09
Yeah I'd rather NOT lose the data as, although the important bits are backed up, there is A LOT of data there (like VDI drives, etc), maybe ~200gigs from an external NAS drive that is S L O W. 

Yeah, I saw that bit about the sdc but I too am not familiar enough with this. Everything was set up at the store for Win7 and that all runs fine (except for the "windoze" bit, but only so much can be done, eh? ;).

As an aside, originally I was going to try to make a go of it using Win7 as my host OS and putting Ubuntu or Mint into Virtualbox. However, I want to run the VirtualBox in Seamless mode (which hides the desktop and thus shows windows/apps from both OSes on the screen together) but the GUI change (to an OpenGL thing?) in both Ubuntu and Mint means that they won't work in Seamless mode. I even tried to use Virtual Desktop (tried a few implementations) to just put Ubuntu onto another virtual screen from win7 but the VirtualBox window is very naughty and refuses to be put aside (and thus shows up on each/every virtual desktop) thus making the exercise moot. Thus I give up. It's back to putting Windows into the VirtualBox and hosting everything under Linux... if I can get linux to work on this hardware, that is.

--
cheers

---

