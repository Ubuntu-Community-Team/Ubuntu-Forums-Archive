---
title: "Windows to Ubuntu  Lord help me...."
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by mrchaos101 on 2007-12-28
Here is my first Ubuntu noob post.

Not sure how this experiment is going to go. I have been a MS boy ever since dos 3.0.  I have used windows from 3.11 to Vista.  I have used lots of software I paid for... and lost I didn't over my windows life.

The direction MS going, i fear is not good.  Vista == Windows ME 2.

I am going to build a box using an AMD 64 +3200.  This will be seated in an MSI mobo.  Depending on what you all recommend, I will stick either 512mb or 1gig of ddr 2 memory in this thing.

I will go with an nVIDIA graphics card of some sort.  Not sure whta one, but it will be a low end model.

Few questions here...

If I use an SATA HDD and SATA CDROM drive... with this os see it?  Will I have issues to deal with raid drivers like you do in windows that I need to worry about during install?

Things I need help with:
Browser   Im gonna us firefox.  I been using it with windows for a few years.
Email client ?  What is good?   Anything out there like MS Out look   (not outlook express)
MP3 player
Photo viewer manager editor
Something to read .pdf
Java
Flash

I am told I don't need AV as there is no virus issue so I guess we skip this.
Same with spyware and malware.

I will load pidgin.  Seems that is the Linux big boy out there and will allow us communication with the messengers in windows land.

Offic type program.   I am gonna assume that Open office is the way to go.  Though, I ave been told that the  Base part of it  ( linux ver of MS Access) is not as good and kind of flaky.

Is there any games that are any good?  I know I cant run my EverQuest or WOW or anything like that.... so that is an auto matic  50 dkp minus to start with!!  Though, I have been told you can run a windows emulator or something.  That will be abit advanced for me at this point, as I am a noob to this.

Beryl  THIS has my attention.  The stuff I seen on the web.. this just looks cool.

I am kind of debating if I should take photo's and blog this...being I am a noob.... perhaps what I run into will help another out?

If you can give me any ideas on the stuff above i would appreciate it.

---

### Post by mikewhatever on 2007-12-28
You should try running the live cd first to check hardware compatibilities. If it does not work, then ... help you Lord. Otherwise, it's yourself, these forums and google search. The software you mentioned is all preinstalled apart from java and flash, but it's very easy to install those, provided you have internet connection.
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by mrchaos101 on 2007-12-28
Ok somebody said that Ubuntu keeps coming out with version after version and upgrading from one to other can be an hassle.  Is this true?

Thank you for the link for the isntall help. I bet that comes in handy.

Do you have a link to download this live cd so I can test it?

I guess my 64 bit cpu is an Dual Core on also.

---

### Post by Craigus on 2007-12-28
> and upgrading from one to other can be an hassle.

A couple of points here - for one, you don't have to upgrade. If your ubuntu system is running fine then no one will force an upgrade on you.

Of course, most of us want to run the latest and greatest though (hence the Vista sales / regrets). You can do a painless clean install in Linux by having all of your data on a separate /home partition - you can set this up easily in the installer. 

People's mileage varies with ubuntu upgrades. The last step up to Gutsy seems to have been particularly problematic for many.

---

### Post by Craigus on 2007-12-28
> Do you have a link to download this live cd so I can test it?

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by mikewhatever on 2007-12-29
> **mrchaos101 said:**
> Ok somebody said that Ubuntu keeps coming out with version after version and upgrading from one to other can be an hassle.  Is this true?

Every regular Ubuntu release is supported for 18 months so that you should not have to upgrade too often. A long term release (LTS) is supported for 3 years on desktops and 5 on servers. The drawback of staying with one release is that most of the software is not upgraded apart from security patches. I guess a lot of people would prefer newer programs and all the flashy things every new release brings. If you are one of those, upgrade or reinstall. Personally, I think every upgrade is a risky business and have yet to try one. It seems to work for some and break for others, but if you back up, nothing will be lost.

---

### Post by Partyboi2 on 2007-12-29
Here is a link to some program equivalents, (windows-Linux) might help you out alittle settling in.
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by lynxair on 2007-12-29
Similar position to that of the original poster - about to inflict Ubuntu on my laptop with a view to convert a main PC to it later :).

Just a clarification on the /home situation. Read about it, understand why and how (I think) but at a total loss with it's "normal" size. Same goes for / ("root"). Recommendations of "2-3GB - maybe even (gasp) 10-15" for the root I find very confusing. With storage as cheap as it is - why even bother with 2-3GB and a "possibility to resize later"? What is the usual size people leave for their root partition?

In all my MS builds I usually leave 35-50GB for System partition (Windows and installed programs) and store pics, music etc elsewhere. When the time comes to re-install I simply wipe the System clean and  reinstall without the nead for backing anything up (other then the Favourites and Email).

What are the sensible sizes for / (root) (which I understand to be like my System partition in Windows) and /home partitions?  :confused:

The laptop is running of a 120GB HDD with 1GB of memory and the main will have 2x400GB in RAID1 with 2GB of DDR2.

Thank you

---

### Post by Craigus on 2007-12-29
> What are the sensible sizes for / (root) (which I understand to be like my System partition in Windows) and /home partitions?

Well, as an indication, I have Linux Mint 4.0 installed (based on Gutsy, but with some nice extras) with Geubuntu, Virtualbox and VMware Workstation and my root partition is still using only 3.5 GB. Building kernels does require a bit more space during the kernel build.

If you made your root 20 GB, it should be more than enough. You could make it bigger if you wish, and steal some space back from it later if the space is never used. The rest of the drive could be /home (Edit: apart from /swap, that is)

---

### Post by zoe-scutterbug on 2007-12-30
hello

Speaking as one of countless windows & mac  refugees (I left because I kept breaking my many many windows set ups) the are ways to get your existing favourite windows applications to run under linux. 

But though I have WINE in my application menu ...and actually paid for Cross Over Office last year, I found I never ever used them.  Preferring  the native Linux apps. (If the was one non-linux  app I miss its prob dreamweaver... but have produced two ok websites using bluefish and kate.)

Firefox is good...you could also try two variants  swiftfox, swiftweasel ..so many choices

Email...if you are using firefox...have a look at Thunderbird ...work uses it on their windows machines because it is safer. I haven't personally tried Evolution, because I use  gmail anyway.

You can get Acrobat for linux, but with all applications the are often few other choices..try them all and you will hopefully find one that suits your taste.

I actually prefer open office (I dont use Base) but I have also been playing a bit with Google's simple online office suite.

zoe

---

