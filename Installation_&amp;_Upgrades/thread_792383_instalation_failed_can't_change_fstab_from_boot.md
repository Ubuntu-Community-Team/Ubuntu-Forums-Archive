---
title: "instalation failed can't change fstab from boot"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by benjo18 on 2008-05-12
Hi everyone, 
I'm a recent kubuntu user (one month). To make a long story short, I started with kubuntu 6.04, and progressively upgrade it until the latest version: kubuntu 8.04.
Everything was running perfectly until I tried, like many other people in here, to fix this cdrom problem (DVD not detected during installation). Before I did anything weird, I remember that the partitions after installation were: one for xp, one for kubuntu and two small that I never understood why they appear after the first kunbuntu installation.
Anyway, then I made a stupid and irresponsible mistake: I set one of this small partition as being the DVD... I just messed it up... 

Now I can get to the panel which allow me to select between xp and Kunbuntu. But kunbuntu crashed when it try to access to a file in ../sbin (permission denied). I think that I link the DVD to the partition sta4... I don't really understand why but I cannot boot from the live cd (the dvd doesn't run, even in xp).
I obtained can see the wrong line in fstab using cat /etc/fstab, but I don't know how to modify it from grub.
I hope you can help me, I'm getting crazy with this problem... I cannot run any more Kunbuntu...
Ben
P.S: remember I'm a newbie to linux

---

### Post by JC Cheloven on 2008-05-12
Are you able to boot from a live cd? 
If so, you can repair fstab or whatever from there.

---

### Post by benjo18 on 2008-05-12
No I'm not... I already tried, but even if I set the boot from the bios toward the cdrom, nothing happen. It's like if the dvd is disconnected...

---

### Post by VMC on 2008-05-12
> **benjo18 said:**
> .... I think that I link the DVD to the partition sta4... I don't really understand why but I cannot boot from the live cd (the dvd doesn't run, even in xp)....If you power off and then back on with any bootable cd/dvd media it won't boot? Is that correct. At least that's what I'm hearing from you message. Something in you BIOS got messed up.

Put in one of the mini-cds like slax or puppy (do you have any of those?), and see if you can boot up that way. Maybe I misunderstood you, but you stated that even in XP the dvd doesn't work.

---

### Post by benjo18 on 2008-05-12
Hi, 
yes in xp the Ihave two dvd now...!! one is the rel dvd that doesn't detect the cd/dvd, and the other one is something else with a strange name (sti....).
What are those small cd that you speak about: puppy? I don't know it.
Thanks for your help, 
Ben

---

### Post by VMC on 2008-05-12
> **benjo18 said:**
> Hi, 
yes in xp the Ihave two dvd now...!! one is the rel dvd that doesn't detect the cd/dvd, and the other one is something else with a strange name (sti....).
What are those small cd that you speak about: puppy? I don't know it.
Thanks for your help, 
Ben
It sounds like you have a virtual DVD in XP. Maybe DaemonTools or UltraDVD, or Nero. Somthing like that. That's all software.

Try this. Do you have any bootable cd/dvd disk that you can put into your optical disk drive? If so, then put it in, reboot and see if it boots to the cd/dvd drive. Do that first, then we can go from there. You said your new to Linux, I'm assuming your experienced with Windows.

[The Puppy, Slax, KNOPPIX are what's referred to as mini Linux distros. They are mainly used for repair.]

---

### Post by JC Cheloven on 2008-05-12
Mhhh... so you can't boot from cd, even when you just told the bios to start from there. Also the unit doesn't work on xp...

Let's see: changes what you made on fstab (or whatever, except partitioning) souldn't affect other operating systems, or live cd startup.

Sorry, that's beyond me. Perhaps your hardware (cd/dvd unit) is damaged in a permanent way. I didn't think that this would be possible, but I actually don't know what to say. I hope someone else can help you, and that your dvd can work again. Not an easy problem, I think.
Regards

---

### Post by benjo18 on 2008-05-12
vmc,
I tried run kubuntu from dvd at boot (download iso DVD) but the boot failed an says: couldn't boot.
Those mini linux distro should permit to rewrite the fstab file?
 Thanks, 
Ben

---

### Post by JC Cheloven on 2008-05-12
Yes, I've used Puppy sometimes for similar things. You loose nothing to give it a try, but with a working cd-unit, should be equally possible to startup from a big distro or from a smal one. 
BTW, if your hardware is able to boot from usb stick, these minimal distros will start from there. You can have a look on [http://www.puppylinux.com/](http://www.puppylinux.com/) , or googling for "damn small linux", among other minimal distros.
Greetings

---

### Post by VMC on 2008-05-13
> **benjo18 said:**
> vmc,
I tried run kubuntu from dvd at boot (download iso DVD) but the boot failed an says: couldn't boot.
Those mini linux distro should permit to rewrite the fstab file?
 Thanks, 
Ben

Ben,

How adept are you on hardware? If you feel confident, open up your case unplug the  IDE or SATA cable from the hard drive and power connector. Make sure no other hard drive in connected. Then with a bootable CD/DVD in the DVD drive see now if your able to boot up. I know this may seem drastic, but in the past  my hard drive has caused problems with operations. Also, this way the interface connection from the CD/DVD is uninterrupted. Also make sure the connection from back of the CD/DVD drive is secure. If you do that, does the light on the CD/DVD drive light up and do you hear it spin up?

---

### Post by benjo18 on 2008-05-13
Ok, 
I could install a USB cd drive... I think that part of the problem is that the onboard cddrive insn't recognized anymore, I don't really understand why, but anyway now I can boot from cd live. I 'll try some stuff I saw in other threads and let you know about this topic.
Thank a lot for your help guys, 
Ben

---

### Post by benjo18 on 2008-05-13
Hi evrybody, 
well I reach to boot from an DVD iso image of kubuntu 8.04. But, the problem is that it start to install, and then stop:

/install/vmlinuz.gz
/install/intial.gz

an then a black screen with cursor appears... I can't do anything, but reboot again.

I tried other mode like rescue mode. When I write boot: rescue, it appears that the kernel doesn't exist. I understand that the syntax is not correct.
Is there anyone, to help me and reboot from iso kunbuntu 8.04 dvd.
Let's notice that the dvd is an external dvd drive, and that there is already a borken installation of kubuntu 8.04 on this computer.
Thanks for your help, 
Ben

---

