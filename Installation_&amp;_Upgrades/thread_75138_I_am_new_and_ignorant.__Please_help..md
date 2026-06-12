---
title: "I am new and ignorant.  Please help."
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by TeeAhr1 on 2005-10-13
Okay, I don't know if this is in the right section, but anyways.

I read about ubuntu elsewhere, and I'm wondering if it's appropriate for me.  I am a lifelong Windows user, I know nothing about Linux (and I mean *nothing*), and I'm looking for a good "starter" distribution.  Preferably something that I can run parallel to Windows, at least during the "breaking in" process.  Yes, I'm nervous about this.  Obviously, I am a non-geek, I'm just looking for something functional, that's gonna work and not confuse the hell out of me.  Is ubuntu the answer for me?  If not, can anyone suggest something that might be more up my alley?  Any advice is greatly appreciated.

-love, dope, and happiness-
TeeAhr1

---

### Post by Emerzen on 2005-10-13
I suggest downloading the Live version of Ubuntu that runs off of a CD.  Download the live version.iso-> burn it as an iso using whatever burning software you have-> put the disk in your CD/DVD drive and reboot.  Nothing gets installed and you can get a feel for how Ubuntu works w/ your PC.  

I knew nothing about Linux only a couple of months ago.  I started w/ Fedora Core 3 that I got from a "Linux for Dummies" book out of interest...it was okay but tried Ubuntu shortly after and never looked back.  It's a learning process, but it's WELL worth the effort as the payback in fun, community, versatility, etc...is unbelievable.  And, btw, I'm in the medical field and have no special computer knowledge either.

---

### Post by aysiu on 2005-10-13
I'd start off by reading this:

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

It's everything I wish someone had told me when I first started using Linux.

Then, you can read this: [Is Ubuntu for you?](http://www.ubuntuforums.org/showthread.php?t=63315)

You may want to look at [The DistroWatch Top Ten](http://distrowatch.com/dwres.php?resource=major) or take [The Linux Distribution Chooser](http://www.zegeniestudios.net/ldc/) quiz.

---

### Post by yesplease on 2005-10-13
It is true that the live CD does not install or change anything on your computer. You can get an impression of Ubuntu with it and it has other uses too.

However, I would recommend to just install Ubuntu. Installation is easy, almost everything works immediately (you probably have to install a video-card driver but that is easy too). Removing Ubuntu is easy too (if you dont like it just tell windows to format the partition).  

Dont be afraid of Ubuntu is my answer. 

An important thing I learned from my short usage of the live CD was that it configured the internet connection automagically for me (which was a relief).

---

### Post by TeeAhr1 on 2005-10-13
Great.  Thanks a ton for the advice, guys, I will take it to heart.  This really is the week I finally kick Bill out of my damn house.

**Edit:** I took the quiz, and Ubuntu came up #1!  Did you rig this? :oP

---

### Post by toujours on 2005-10-13
I say go with a live CD for a few hours at least and see if you like what you see.

If you like it, free up some space on your hard drive for a second partition and then install Ubuntu as a second OS with Windows still on your hard drive. Get help if you don't feel safe with this. Then if you change your mind you can still switch back to William's Wonderful World of Windows.

Or if you're really scared : First of all try some open source / Linux compatible software in Windows.

Try out stuff like :

Open Office : [www.openoffice.org](www.openoffice.org)
Firefox and Thunderbird : [www.mozilla.org](www.mozilla.org)

There are I believe websites that list this kind of software that works in Windows. Try [www.framasoft.org](www.framasoft.org) for example.

---

### Post by tihom on 2006-01-17
pls help. i tried to install ubuntu both in live and install modes but my laptop just hangs. from the beginning this is what happens

as the computer starts

[B]this is the ubuntu live cd
press f1 for help and advanced options

for the default live system, press enter
boot:_[/B]

after i press enter

[B]loading /install/vmlinuz.........................
loading /install/initrd.gz...............................

ready.
uncompressing linux...ok, booting the kernel.
_[/B]

after this there is no response. i have waited for half an hour. i tried doing expert option and the normal install CD but the result is exactly the same.

need help....have read so much..and now really want to get into action.

---

### Post by Sef on 2006-01-17
A few questions:

1) When you downloaded Ubuntu, did you md5sum before burning to a CD?

2) Did you burn at a speed of 4x?  (Faster speeds can make the CD unreadable.)

3) What type of computer do you have?

4) What are the specs for it? (RAM, Motherboard, Video Card, etc.)

---

### Post by tihom on 2006-01-17
1)and 2) i got this live CD with the "linux for you"  magazine's december issue.
3) i have an acer laptop 4100 series
4) this is with 512 mb ram, ATi Radeon X700, toshiba HDD, pentium M processor 740 with 1.73 ghz 533 fsb board and dual layer dvd read/write

---

### Post by Sef on 2006-01-17
I found this on a website for an Acer TravelMat 4101 LMI installing Warty:

> Install Tips:

Use following parameter to start the installation via CD:

linux noapic nolapic acpi=off vga=771 pci=noacpi

For generic X11 use the X11 vesa driver.

Link: [http://www.seher-it.at/installationtravelmate4100.html]("http://www.seher-it.at/installationtravelmate4100.html")

This may or may not work, but it's worth a shot.

---

