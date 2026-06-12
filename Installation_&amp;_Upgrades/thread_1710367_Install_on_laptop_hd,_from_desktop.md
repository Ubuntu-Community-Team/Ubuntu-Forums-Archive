---
title: "Install on laptop hd, from desktop"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by jpcode on 2011-03-19
OK I have seen similar threads with people trying to install on usb drives or externals but they don't fit (at least to me) what I think I want to do.

I have an older sony laptop that won't boot from CD becuase it is broken, and it is too old to have the option to boot from usb. I have the SATA adapter to connect my laptop HD to my desktop via usb and I think I can install ubuntu on it making sure the mbr is on the laptop drive, but which version should I use? Will I have hardware/driver issues? 

I am very good at following the various tutorials that have been posted so if there is one I can be pointed to that would be great as well. 

Or am just crazy naive that this might work?

---

### Post by Hedgehog1 on 2011-03-19
I believe that will work based on my experience building USB bootable "Pocket PC's".

The steps are like this:

1) Remove Laptop hard drive
2) disconnect desktop hard drive(s)
3) temporary attach laptop hard drive to desktop (USB to SATA is OK)
4) Boot off liveCD and install on laptop hard drive.
5) When the install completes it's first pass and wants to reboot, go until it wants you to remove the CD, remove the CD but power down the desktop completely instead.
6) Relocate the laptop hard disk into the laptop
7) Power up the laptop and complete the 'update' phase of the install from the laptop.

It is a little convoluted, but should work.

***The Hedge***

:KS

---

### Post by jpcode on 2011-03-20
Ok first try: I was able to get ubuntu installed on the laptop drive, but at the very end there was an io error after it asked me to reboot, I don't know if this had anything to do with it but the laptop would not boot so I am trying it again. I have removed all other drives from the desktop to prevent any confusion what was going where, but I do have one mbr question. Just before the install when you have the option of choosing the mbr location I still have 2 options, SDA and SDA1 I am going with default for now, and if that does not work I will try the other.

---

### Post by Quackers on 2011-03-20
The I/O error is normal for some systems. Mine does it.
What do you mean by it wouldn't boot? What happened exactly?
If you re-install with no other HDD's attached the default (sda) would be the correct place for grub to be installed. 
I suspect that re-installing will not be necessary just yet though.

---

### Post by jpcode on 2011-03-20
OK Good news. 
This worked:
1. connected laptop hd to desktop via usb (one of those hd cases that you can buy for $5)
2. removed all drives from desktop except cd drive and laptop hd. I did not want there to be any confusion about where the mbr would be installed.
3. installed 10.4 with the normal procedure without changing any of the settings, just clicking next.
4. restarted the computer without unpluging the laptop hd allowing the desktop to boot from cd. I ran a couple of checks to make sure grub was installed etc. but I did not change anything.
5. Saftly removed the laptop hd and reinstalled it in the laptop. On first boot the disc was checked for errors and then booted fine. It has booted fine several times now and everything seems to be working fine.

---

### Post by Quackers on 2011-03-20
Excellent :-)  Enjoy!

---

### Post by Hedgehog1 on 2011-03-20
> **jpcode said:**
> OK Good news...It has booted fine several times now and everything seems to be working fine.

WAY*YYY* COOL!!!

I am amazed at the workarounds that can be found if you look for them!

Good job working outside the box (or laptop, in your case)...

***The Hedge***

:KS

---

