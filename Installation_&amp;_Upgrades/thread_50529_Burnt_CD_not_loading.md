---
title: "Burnt CD not loading"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by sra136 on 2005-07-20
I burnt the ISO image of Ubuntu and Kubuntu on CD's and they wont install.  I explored the cd's and found .exe/setup file.  I dont know if there's a step missing after burning the iso's or what.  Also, there no autoplay feature.  Anyone with an idea?

---

### Post by dave9191 on 2005-07-20
These are bootable CD's. You put them into your CD drive and restart your computer. You bios needs to be setup to boot from CD first before booting from the hard drive, otherwise your cd will never be read and your computer will boot as normal. 
Dave

---

### Post by qwert231 on 2005-07-20
I'm not sure where your issue is, but I am having trouble installing from my install CD. I get the initial screen asking for the type of install, then it loads some files, and stops with a blinking cursor.

I have been trying just hitting 'Enter' (default). It loads these files:
/install/vmlinuz
/install/initrd.gz

Then gives me a blanks screen with a blinking cursor.

I've tried server install and expert install, to no avail.

---

### Post by sra136 on 2005-07-20
I know about booting from cd configuring from bios, that's what was not working as well.  Turns out that the program used to burn the iso, in my case which was Nero OEM, didn't burn correctly and created bad disks two times.  Used "Deepburner," and currently Ubuntu is being installed as i speak.

---

### Post by qwert231 on 2005-07-20
I used Nero also. Hmm... where can I get Deep burner?

---

### Post by dave9191 on 2005-07-20
[QUOTE=sra136]I know about booting from cd configuring from bios, that's what was not working as well.  Turns out that the program used to burn the iso, in my case which was Nero OEM, didn't burn correctly and created bad disks two times.  Used "Deepburner," and currently Ubuntu is being installed as i speak.[/QUOTE]


Sorry, it just sounds like you were trying to run the cd from inside windows when you mentioned exploring the cd and no autoplay feature. 

And although Ive never used deep burner, a good search turned up [http://www.deepburner.com/](http://www.deepburner.com/) , try looking there. 

Dave

---

### Post by sra136 on 2005-07-20
I wasn't trying to run the CD under windows.  I was just expecting the install CD to be similar to WinXP type CD where you would autoplay and that stuff.  However, the install didn't go through due to missing files on the CD, some intriz...something file and bootstrap is missing.  I created 4 CD's with no avail.

---

### Post by qwert231 on 2005-07-20
K, got Deepburner, still no good. So I took it off my KVM switch, plugged everything directly into the box, and got farther. It started the install and got to LVM. Tried that a couple of times, still the same, so I went back to the Nero burnt disk. It got to the point of selecting the Kernel.

None of the kernels go through. Says there was an error processing the source.

---

### Post by ozzie123 on 2005-07-20
Probably it's the file you downloaded is damaged? Try md5sum check for that.

I've downloaded Ubuntu several weeks ago and Kubuntu several days ago and that both works just fine.

Or probably it's your burner that's in question? I mean, I have the same problem with Gentoo Linux before

---

### Post by GTvulse on 2005-07-20
[QUOTE=qwert231]K, got Deepburner, still no good. So I took it off my KVM switch, plugged everything directly into the box, and got farther. It started the install and got to LVM. Tried that a couple of times, still the same, so I went back to the Nero burnt disk. It got to the point of selecting the Kernel.

None of the kernels go through. Says there was an error processing the source.[/QUOTE]
 The K/Ubuntu ISO images have a very complex filesystem and don't burn quite right at high speed. Burn the images again using **half the maximum speed** of your cd burner, yet that can still be too fast. I haven't got an Ubuntu installer CD coaster since I decided to use 4x as maximum speed (and I've burned a few lately).

---

### Post by qwert231 on 2005-07-21
[QUOTE=ozzie123]Probably it's the file you downloaded is damaged? Try md5sum check for that.[/QUOTE]

How can I do an md5sum check?

---

### Post by dave9191 on 2005-07-21
[QUOTE=qwert231]How can I do an md5sum check?[/QUOTE]

Have you looked it up on google first ?

---

### Post by qwert231 on 2005-07-21
Burnt at 24X instead of 52X, seems to be going fine. (I realize my CD-Rs are only rated to 48X.)

---

