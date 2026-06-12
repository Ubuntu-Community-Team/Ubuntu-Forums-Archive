---
title: "Won't install on Dell Inspiron 3000"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by thebigb on 2006-06-03
I am unable to install Ubuntu 6.06 on a Dell Inspiron 3000. This is a P1 w/MMX system at 233MHz and with 80 MB RAM. I would really appreciate any help on this as my current Linux install (RedHat 5.1) is old and outdated (and I like Gnome)

---

### Post by kufford on 2006-06-03
You might want to think about using xubuntu, as your system specs are a bit low for gnome. However, a more descriptive explanation of your problem is necessary to help you.

---

### Post by thebigb on 2006-06-03
[QUOTE=kufford]You might want to think about using xubuntu, as your system specs are a bit low for gnome. However, a more descriptive explanation of your problem is necessary to help you.[/QUOTE]
OK I'll try that. I doubt, though, that it would help. It simply freezes while loading the installer. It gets past the "Looking for CD" screen and then the installer just stays with a blank screen.

---

### Post by llamakc on 2006-06-03
The alternate install cd is perfect for this:

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

**Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  [LIST]
[*]creating pre-configured OEM systems;
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]<b>installs on systems with less than about 192MB of RAM.</b>[/LIST]

---

### Post by thebigb on 2006-06-04
> **llamakc]The alternate install cd is perfect for this:

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

**Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  [LIST]
[*]creating pre-configured OEM systems said:**
> setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]<b>installs on systems with less than about 192MB of RAM.</b>[/LIST]
Sorry, I forgot to say I was using the Alternate Install CD, actually.

---

### Post by rcarring on 2006-06-04
You are going to have to seriously consider adding more ram to your system.

Breezy may be a halfway house until you can do this.

---

### Post by thebigb on 2006-06-05
Well after looking in I guess the system logs (i did Alt+F4) I saw it said ```
ide-cd: cmd 0x20 timed out
hdc: DMA interrupt recovery
hdc: lost interrupt
``` over and over so I tried doing Alt+F2, pressing enter to start the shell, and typing ```
mount /dev/hdc /cdrom
``` and it froze. I know it's not from a dirty CD because I used the same CD to install on my PC, which installed it fine. If anyone can help, I would appreciate it greatly. Also, I may get some more RAM later on, but I don't want to invest too much money in this computer when for $400 (after some rebates) I can get a brand new laptop from Tigerdirect. I don't mean to sound like a spam email but I do have to say it is a good deal.

---

### Post by thebigb on 2006-06-06
Sorry for bumping, but I really want to use Ubuntu. If I have no chance of using it on my laptop, I will just install fedora, but Ubuntu is by far less bloated.

---

### Post by ludob on 2006-06-07
I'm having a similar problem with 160MB on a Dell Inspiron 3000 trying to run Xubuntu 6.06 Desktop. Console messages (repeating indefinitely) are:

  ide-cd: cmd 0x28 timed out 
  hdc: DMA interrupt recovery
  hdc: lost interrupt

The system hangs when mounting fs (just after "Loading essential drivers").
Tried different boot options (pci=noapci noapic nolapic) but always same result.

ISO is fine. Runs on another laptop (Targa XP210 500MB) without any problems.

---

### Post by ludob on 2006-06-07
Got it! Found a suggestion on the French Ubuntu forum. Added 
  hdc=noprobe hdc=cdrom
to the boot options and the Xubuntu Live CD starts without any further problems. It takes 10 minutes to boot the Live CD which is not so bad for a 233 MHz.

---

### Post by thebigb on 2006-06-08
Thanks a lot, I'll try this!

EDIT:I did and though it's been installing for well over an hour, at least it's installing (and it didn't freeze because the progress bar is moving.) Thanks!

---

### Post by gtwilliams on 2006-07-25
Hey All,

I can't get ubuntu to work on my inspiron 3000. First of all it loads up in 'low memory' mode (which i expect, since the model has maybe 32MB ram). I have tried almost 8 different discs to install from Xandros / Damn Small / Ubuntu. 

The most common problem i run into is after choosing the keyboard layout it 'scans' the cdrom properly, goes to 'load installer components from cd' screen, of which i select all, it loads the additional components.... then goes to the ubuntu installer main menu....

1)I try to 'prepare for end installation instructions' *i can't remember what it exactly is called because i selected it and now it is frozen in a blue screen, Control-Z escapes back to installer window.

2) I click on detect disk drives - stuck on blue screen

HELP!!!!

It may be easy to talk online in which case, AIM is g t will socrates         no spaces in there, just wanted to break it up. also, email is g t w illiams at wustl.edu , again, no spaces.

Comments appreciated. All i wanted to do was set up a digital picture frame for my girlfriend, but i can't get ANY linux to work on this damn model.

---

### Post by gtwilliams on 2006-07-26
What i've found, regarding the Dell Inspiron 3000 is that dapper drake does not want to install.

Pass the following boot parameters to breezy badger:

boot: server noapci pci=noapci nolapic noapic nodma hdc=cdrom hdc=noprobe

let me knwo how it works. I am about 35% through installation.

---

### Post by videodrome on 2006-07-27
No way on earth would I attempt installing it on a machine that slow. I have xubuntu running on a inspiron 5000 with 256mb of ram and it's slow. You need to install damn small linux instead IMO.

---

### Post by compuguy1088 on 2006-07-27
> **videodrome said:**
> No way on earth would I attempt installing it on a machine that slow. I have xubuntu running on a inspiron 5000 with 256mb of ram and it's slow. You need to install damn small linux instead IMO.

Well.... I have used ubuntu 5.10 on an old Inspirion 7000 with an 300 mhz pentium 2 and 384 megs of ram, with gnome, and it worked......ok, a tad slow though, but when I was doing that I didn't know about platform specific kernels, and xubuntu, so those things do help....

---

### Post by larryd85 on 2007-10-12
> **ludob said:**
> Got it! Found a suggestion on the French Ubuntu forum. Added 
  hdc=noprobe hdc=cdrom
to the boot options and the Xubuntu Live CD starts without any further problems. It takes 10 minutes to boot the Live CD which is not so bad for a 233 MHz.

i was having this exact same problem as the original poster, and this was the one that did it

(Dell inspiron 3000, xubuntu alternate desktop cd)

THANKS!

---

### Post by dimeotane on 2007-10-13
**For you critics out there:**
Even if this lowly Pentium 200mmx with 64 meg RAM and 4 gig HD, is ancient... Yes, I need a higher end system to put the full Ubuntu system on it.  
But I'm gonna put ubuntu-lite on it because I CAN!  I have something to prove I guess.  This amazing OS is versatile enough for all kinds of systems, old and new.  I remember paying $2000 for my first laptop and it  seemed pretty darn good then.  If I can update the OS to something better than win95, this legacy system can be given a new lease on life.   Udpating an old system with Ubuntu provides added security, more advanced networking, free software repositories, frequent updates, easy package installation... you name it. 

There seems to be increasingly more older systems that are being rejected, donated to charity, or 'in storage'.  They are useful systems that billions of people around the globe could benefit from access to, but instead millions of these machines are ending up in the landfill.    Its  the ultimate recycling project for the future.   


**My Installation :**

I tried adding these boot codes to the 'install command line system" on the Feisty alternate install CD:
>  hdc=cdrom hdc=noprobe

It gave me the error 'no common CDROM drive was detected" until I figured out to change /dev/cdrom to /dev/hdc

If I try to install without the boot codes, the CDROM just starts and stops for hours with the blue "Low Memory Mode"  screen.

I have a stack of PCMCIA cards for ethernet... we'll see which one works best ....

---

