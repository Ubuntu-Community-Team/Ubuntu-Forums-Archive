---
title: "Install Problem... Please get me to the next screen"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by Imoen_tw on 2007-12-06
**The Computer Specs**
Model is a Compaq 7478 with the following specs:
• 533 MHz AMD K-6(r)
• 97 MHz system bus
• 512 MB 100 MHz SyncDRAM - 8 MB dedicated for video memory 
• 30.0 GB 1 UltraDMA hard drive
• DVD-ROM Drive1
• CD-RW Drive2 	
• 512KB L2 Pipeline Burst Cache
• Trident Graphics Integrated in the ViaChipset.
• ESS Allegro PCI Audio

**My Goal**
I play a game online with some friends and for this game I am looking to use this computer as a server to host a forum and some simple scripts. Some of these scripts will be dependent on databases of information. I would like to run SMF for the forum with the ability to add chat room option sometime in the future.

**The Problem**
Currently this computer has Red Hat 9 on it. I installed it from disks I bought at a store about 4 years ago. I can not get updates and worry about the security without them (this computer is on my home network) Secondly the version of mysql it has is too old to install SMF, adminmyphp etc. to. Thirdly, when it comes to Linux I am clueless. I have a college education in computer programming, but sadly it is all on Microsoft products and the Linux class I wanted to take when I was in school was canceled. Some of my friends whom I play this game with are a bit wiser then I and can give me some help but they need me to have an operating system that is up to date first. They first suggested I install CentOS 5.0, but that would not install. Next they suggested Ubuntu 7.10 Server and like the previous attempt it too failed. Then I tried Debian 4.0 and Fedora 8, both having the same result. 

**What it does (or isn't doing)**
This same problem occurs with all 4 Linux variations I tried. In each case I download the iso file(s) onto my Windows XP Pro computer. I run the winmd5sum on them and they all test good. I then right click the iso and select copy image to cd. When they complete I put them into the dvd drive on the Compaq and restart. I am then met with an install screen with install to hard drive (or some form of that) amongst the other options each of the variations have. I select install to the hard drive and press enter, it tells me loading Linux kernal the screen goes black and the computer restarts and I am right back to the install screen. 

I am getting very frustrated as I have been attempting to set this computer up for my gaming friends and I for over a month. I am a very determined person though, so the more this doesn't work the more I am determined I will get it to. Does anyone know what the problem is that would cause this problem to happen? Your help is greatly appreciated.

---

### Post by Pumalite on 2007-12-06
Try the Alternate CD from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Download'

---

### Post by Imoen_tw on 2007-12-06
I downloaded that one and burned it as I did the other ones and the same thing happens. :(

---

### Post by Pumalite on 2007-12-07
Clean the lens in your burner, try the CD's in a different computer.

---

### Post by Imoen_tw on 2007-12-07
I ran a lens cleaner CD in both of the CD drives then retried and still the same thing. I also tried to use the Live CD option as in [this](http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml) article and the same result occurs. A few questions that just occurred to me to ask:

As I said in my first post, the computer has Red Hat on it right now. When I installed that I did use the full hard drive in the partitions that were "suggested" by the installer. Would that cause this problem?

Also I burned these iso's to CD-RW's, does that make a difference?

Is it possible to make this work by putting the iso onto my external USB drive (NTFS formatted) and if so would there be a problem for the computer to read the hard drive since the motherboard itself won't read the hard drive due to size limits? I do also have a media card reader built into my printer and have 3 media cards from 512 mb to 2 gb. Would that work to install from there if the printer won't work on Red Hat?

If any of these are workable options can you maybe point me in the right direction for the procedure to follow to install in this way?

As I said before, when it comes to Linux I don't know much so I'm sorry if these are stupid questions and for being such a pain.

---

### Post by Pumalite on 2007-12-07
Try CD-R of good quality, at 4x

---

### Post by Imoen_tw on 2007-12-07
Burned at 4X on JVC CD-R and it made no difference.

---

### Post by Pumalite on 2007-12-07
See if you can install this:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Imoen_tw on 2007-12-07
I went into the edit the commands area to see if I could make it log where the problem occurs. I noticed it said --quiet on the line, so I took that off. Then I had a popup to load the kernal, I hit ok and the cd spun fast for some time then stopped. I figured it was stuck because I was still in this area to edit and was trying to back out so I hit esc and now it has gone to a screen that it black with only boot: _ and I can type there. Is this in any way helpful to be at this screen and if so what does it want me to type?

---

### Post by Pumalite on 2007-12-07
Had you finished the installation before you got to the command line? Installing what?

---

### Post by Imoen_tw on 2007-12-07
it didn't install anything, only loaded the vimlinz (something like that) kernal and then the cd spinned for awhile, then stopped. It remained at the install choices page until I hit esc.

---

### Post by Pumalite on 2007-12-07
If you haven't installed anything, there is nothing to do at the command line. What happened with the last link I gave you?

---

### Post by Imoen_tw on 2007-12-07
I tried both Start or install and start in graphics safe mode and both times the computer restarts and brings be back to the screen.

---

### Post by Pumalite on 2007-12-07
I would start checking my hardware. Or try something small, like DSL or Puppy.

---

### Post by Imoen_tw on 2007-12-07
I don't know what hardware could be causing a problem, it works fine running red hat 9 and I would be happy sticking with it if I could get updates. The only hardware that is not "onboard" is the Ethernet card anyway. 

What is DSL and Puppy? I'm 100% happy with anything that I can use to do what I said in my first post. I don't use the computer for anything else and as soon as I have it initially set up I likely won't even keep the monitor, keyboard or mouse hooked to it, instead just accessing it over filezilla. It's an old pc with a slow processor and limited ram so anything I don't need on it is better not being there for me.

---

### Post by Imoen_tw on 2007-12-07
What about installing from a DVD-RAM drive? I have one in my computer I use that I was going to swap out with one of the drives in it so I can run scheduled backups.

Is there a way to resize the redhat partitions so I can try the install from linux directions [here](https://help.ubuntu.com/community/Installation/FromLinux)?

---

### Post by Pumalite on 2007-12-07
Haven't done it myself, but if you know how to do it, go ahead and let me know.

---

