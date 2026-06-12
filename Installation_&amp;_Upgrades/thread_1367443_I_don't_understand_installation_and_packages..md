---
title: "I don't understand installation and packages."
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by MouseArm on 2009-12-29
Why can't I just double-click and install an application? Do I need special packages for every piece of software I want to install?  I saw somewhere that you are supposed to be able to install software while you test Ubuntu from the CD, is that possible?

---

### Post by doas777 on 2009-12-29
in terms of the liveCD, just pop it in, and reboot, booting off CD. 

ubuntu uses software "repositories" that contain huge amounts of software ready for install. you will find that 98% of the software you require will be avialable via the repos.

go to Applications -> software Center or to System -> Administration -> Synaptic Package Manager to view options and to install/uninstall whatever packages you require.

here is some info on installing apps in linux and in debian-based systems like ubuntu
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware).

just remember, Ubuntu is not windows. once you get used to it, you will probably really like the repo system. I sure prefer it.

oh, and BTW, if you end up with the right installer file (a .deb) you can actually doubleclick it to get it to install. are you clicking an exe? 

Welcome, Good luck, and Have fun. you know where to come when you have questions.
Franklin

---

### Post by avtolle on 2009-12-29
> **MouseArm said:**
> Why can't I just double-click and install an application? Do I need special packages for every piece of software I want to install?  I saw somewhere that you are supposed to be able to install software while you test Ubuntu from the CD, is that possible?
As to your final question, presuming I understand your comment, it is possible to "download and install" while testing the live CD, limited to how much RAM is on your system and the size and number of packages. Of course, these would "go away" on restart, as the same would not be saved to disk but would merely be in RAM. There is a way, I am sure, to make the installation permanent, so to speak, by mounting the HDD and saving the packages there; I just am unsure how would do this.

As to your first two questions, the facile answer is that Ubuntu isn't Windows. Using Synaptic to install desired packages takes some of the pain away, and IMHO provides a more secure way of doing things.

---

### Post by snowpine on 2009-12-29
Installing applications is *much* easier in Ubuntu than in Windows. Most packages you'll ever need are in a central "repository" of trusted and tested applications, maintained by the creators of Ubuntu. Installing from this repository requires only a couple of mouse clicks in the Software Center (or simple terminal commands, if you prefer doing it that way). Very stable, no need to surf the internet trying to find a particular app, and no viruses either. :)

---

### Post by MouseArm on 2009-12-29
> **doas777 said:**
>  oh, and BTW, if you end up with the right installer file (a .deb) you can actually doubleclick it to get it to install. are you clicking an exe? 

So software makers have to make their installers in .deb format for it to work?

---

### Post by snowpine on 2009-12-29
> **MouseArm said:**
> So software makers have to make their installers in .deb format for it to work?

It would be easier to help if you had a specific example of an application you are trying to install. :)

In general, installing from a .deb you downloaded from a website should only be a last resort, if the app you're looking for is not in the Ubuntu repository.

---

### Post by dougHines on 2009-12-29
> **MouseArm said:**
> So software makers have to make their installers in .deb format for it to work?
I'm new too, but yes, I believe a .deb package is the same as a windows .exe installer

---

### Post by doas777 on 2009-12-29
> **MouseArm said:**
> So software makers have to make their installers in .deb format for it to work?

yep. .rpm's are for RedHat based distros, .deb for debian's. other more primitive types are also used, like tarballs (.bz2) and compressed source packages (that you have to compile) usually end in .tar.gz (tar.gz is like .zip. the tar holds a bunch of files together in an archive, and gz is for the old GZip program). 

you can compile from source if you have a tar, or bz2, and if you have an RPM, you can use alien to generate a .deb from it. 

keep in mind though, in 3 years of sollid ubuntu, there have only been 3 packages that I have needed to compile myself (none of which are still in use) and a handful of trusted applications that just can't be contained in the repos because of legal licensing issues (like truecrypt). I'm quite serious when I say that 98-100% of the software you are likely to need are in the repos.

other than that, what are you trying to install?

---

### Post by MouseArm on 2009-12-29
> **snowpine said:**
> It would be easier to help if you had a specific example of an application you are trying to install. :)

I want to install 'Darwin Setup.exe' located here:  [http://www.darwinbots.com/Forum/index.php?showtopic=2820&st=15](http://www.darwinbots.com/Forum/index.php?showtopic=2820&st=15) 
 If someone is interested in compiling this for Ubuntu I would be mighty greatful.

---

### Post by snowpine on 2009-12-29
> **MouseArm said:**
> I want to install 'Darwin Setup.exe' located here:  [http://www.darwinbots.com/Forum/index.php?showtopic=2820&st=15](http://www.darwinbots.com/Forum/index.php?showtopic=2820&st=15)

Darwinbots is written for Windows, not Linux... that is why it's not easy to install (just as it's not easy to install a Linux application in Windows, or a Windows application on a Mac... wrong operating system!). :)

Check out these instructions though: [http://www.darwinbots.com/WikiManual/index.php?title=Installation_Instructions#Installing_DarwinBots_under_Linux](http://www.darwinbots.com/WikiManual/index.php?title=Installation_Instructions#Installing_DarwinBots_under_Linux)

If you check out the Software Center, you'll see there are lots of free, cool games that are native to Linux. :)

---

### Post by QIII on 2009-12-29
Linux is not Windows.

Without checking that out specifically, I rather suspect that anything ".exe" is not going to be executable in Linux.

You might have to try to find a Linux version of that App and install that.

Edit:  re: Snowpine's suggestion (I saw it after I posted), just be aware that WINE is not perfect and does not run all Windows programs equally well -- or at all.

---

### Post by MouseArm on 2009-12-29
Ok, thanks for your replies. I guess I didn't know how big the difference was between the systems. I've never looked at Linux before today. I've been a Windows user since PC's appeared. :-P

---

