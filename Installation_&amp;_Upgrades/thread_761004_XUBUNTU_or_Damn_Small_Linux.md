---
title: "XUBUNTU or Damn Small Linux?"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by tommys5 on 2008-04-20
I have an old old Dell Latitude LT, the kind with the PCMCIA CD Rom that the bios doesn't allow me to boot from. (So, in order to replace Win 95 with a new distro, I have to take the HDD off the Latitude, install it on a Thinkpad that lets me install from an install disk, run the install and let the system get configured. Then I'll take the HDD and put it back into the Latitude; I can't figure any other way to install.)

Question is:  with 128 Megs Memory and not much CPU and 4 gigs of hard drive, is the better choice something like Xbuntu, or Damn Small Linux?

Thanks for the advice..

---

### Post by GSZX1337 on 2008-04-20
I found that Damn Small is mainly useful for booting off a flash drive. Your PC seems to be enough for Xubuntu (if you use the alternate CD). Have you considered Fluxbuntu?

---

### Post by iaculallad on 2008-04-20
I would recommend you install DSL on you laptop considering that you only have 128MB of RAM. Xubuntu (Alternate CD) works fine but still lags in performance due to your limited RAM. Another option would be to install Puppy.

---

### Post by Shazaam on 2008-04-20
Another consideration is hard drive size. If you have a smallish drive either strip down Xubuntu, or install something the size of dsl.

---

### Post by CREEPING DEATH on 2008-04-20
I have a third suggestion, Debian Lenny XFCE.  It's similar to Xubuntu but not as bloated.  I've run it on lesser equipment than your specs with rather good results!

CD

---

### Post by tommys5 on 2008-04-21
I"m likely, based on answers here, to try out Debian Lenny XFCE.
I'm mostly eager to have very basic online activity: email, some browsing. Not using Open Office, since I can use online docs..

If XBuntu would work on this machine, I'd go that way

Thanks.

---

### Post by kerry_s on 2008-04-21
with your setup debian, would be a great choice, you install it once and it can always be updated to the latest from the net. if you run etch/lenny you will be fairly up to date.
a custom install would be best, but if you lack the knowledge, debian xfce4 is fine and you can rework it from there.

[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

---

### Post by tommys5 on 2008-06-11
Catching back up on this same issue... So far, no good. 
I know this is a topic for Debian Forums, I still wanted to leave this message here to see if anyone has advice (and to offer my example for others).

Not being able to install Debian on an older minimal Dell Latitude LT (the one with the external CD ROM that connects via a PCMCIA card), I decided to remove the Dell HDD, place it into an an IBM THinkpad, install Debian, then swap it back into the Dell ... which has 256K RAM and a minimal processor.

I installed 
Debian GNU/Linux 4.0 r3 "Etch" - Official i386 xfce-CD Binary-1 20080217-12:10

That install on the IBM went fine. But then I swapped back the drive into the Dell. 

The boot sequence starts and it starts to load Debian, but it runs about five lines and halts. Then it reloops and I can't finish it. 

Is there some line-edit that might fix the problem?  Is the install worthless since it was performed on a more modern notebook? 
Ideas, anyone?

---

### Post by blazercist on 2008-06-11
I don't think the HDD swap method will work, I'm guessing the installer checks the hardware and loads the specific drivers for install etc...  try DSL, if you can boot from a USB stick that would be perfect.   You could install DSL on the USB stick and boot from there, I think they have some instructions on the DSL site about installing from a USB stick.

---

### Post by SuperStuff on 2008-06-11
I would try Puppy Linux. The 'grubflop' attachment contains an image of a bootable diskette that serves two purposes.
1. It can launch the Puppy CD (or any other Live CD) on machines where the optical drive is not bootable.
2. It can boot a frugal install of Puppy off the hard drive. 

[http://www.murga-linux.com/puppy/viewtopic.php?t=16950]("http://www.murga-linux.com/puppy/viewtopic.php?t=16950")

I'm sure that old computer will not allow you to boot from a CD or USB, but the BIOS should have the option of booting a floppy drive. Boot that first to mount a CD or USB drive to install Linux.

---

### Post by blazercist on 2008-06-11
superstuff makes a good point, i didn't think of it but the USB boot option is probably exclusive to newer BIOS in newer machines, while the floppy should almost always be a boot option.

---

