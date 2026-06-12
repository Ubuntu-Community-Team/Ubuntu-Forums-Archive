---
title: "Installation stops at &quot;select and install software&quot;"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by reghuram on 2006-10-31
Hello,

I've been trying to install 6.10. I just downloaded 6.10 Alternate. Checked the Hash and then burnt onto CD.

Tried to install onto my notebook using the CD. Ran the text mode install with the irqpoll option. Everything was going fine until it hit the "Select and Install software" it keeps going to 85% then stops saying theres an installation error.

I've tried to burn the CD twice and tried but keep getting the same error. Could someone please help? Thank you.

---

### Post by reghuram on 2006-10-31
Given up. Tried mostly everything. Going back to Fedora at least that installs. Might try Ubuntu 6.0.6 if that ever finishes downloading.](*,)

---

### Post by yatesy on 2006-10-31
I had exactly the same problem.
If you select the "continue" option the system will complete the install and you should be able to boot into the new system.
You then have to install the "missing" packages from the cdrom by doing apt-get on the "ubuntu-desktop" package which seems to install the rest of the system.
Hope this helps !

---

### Post by redpotty on 2006-10-31
Thanks yatesy

I have been trying for a week to get first Dapper and now Edgy onto my box.  My installation always crashes a different points during the "select and install software" stage. I continue on and install GRUB and finish up.  After rebooting I end up at a prompt where I enter root username and password and run:

1 #apt-get update
2 #apt-get upgrade

It asks for the installation CDROM and installs a load of software.  It tells me there are unmet dependencies.

3 #apt-get -f install

This loads a bunch of software from the repos and the CDROM.

4 #apt-get install ubuntu-desktop

This loads yet more files from the CDROM.

Steps 1 to 4 are repeated several times each time adding more files and getting a alittle further along the path to full install (I think).

How long did it take your machine to settle down and start doing what it's meant to?

I have tried 6.06 live and alternate, 5.10 live and now 6.10 live and alternate and have had the same problems in every install.  I have checked all md5sums and the discs are OK.

The live CDs seem to crash installing python2.4 and the error message mention something about "ubiquity".

As I type the wannabe ubuntu box is unpacking and installing let's see what happens.  Your suggestion worked but I'd like to know what else you experience during the install.

---

### Post by __InFeRnO__ on 2006-10-31
Keeping this topic alive as I have the same problem.](*,)

---

### Post by yatesy on 2006-11-01
From memory the initial install failed in "software install" with an error in configuring "gnome-applets" which is part of the ubuntu-desktop.

After the reboot into the new system ALL the desktop packages were missing.

Perhaps the easiest way to install the missing packages is to use the Synaptic Package Manager to install JUST the "ubuntu-desktop" package which will install ALL the needed packages as they are dependencies of this.

After doing the above I found that the system appeared to be complete.
It's strange that I also suffered from the same problem as you with the live-cd install , which is why I used the Alternate CD.

This is the first time that I've had problems with any Ubuntu release on my systems !
Hope you manage to fix it.

---

### Post by Cup of Squirrels on 2006-11-14
I have this same problem.

Using the livecd, it froze when loading the livecd system.

Because my pc is quite low in memory terms (About 128MB) I downloaded and burnt the Xubuntu Edgy package. Everything is fine until I hit the "Select and install software" option.

It gets to 6% of the initial loading bar before freezing for about a minute. It then informs me that there was an error.

I can load into the new Xubuntu system command-line. As I am a linux newbie, I have no idea how to extract the files from the CD-ROM manually and run the GUI desktop (GNOME, KDE etc).



I will try out the methods stated above when I get home (At work atm ;)) and post whatever results I get.

For now, any extra help would be appreciated.




(And sorry for bumping a fairly old thread)

---

### Post by unisol on 2006-11-14
this happened to me i believe it was a hardware problem. anyway if you have the alternate-installcd you could try this,sudo apt-cdrom add, this will add the cdrom as a repository,  then when at the command prompt apt-get install linux-386 to have the right kernel for the desktop then do a sudo apt-get install ubuntu-desktop you also may have to do a dpkg -reconfigure - phigh xserver-xorg then hit init2 you should have desktop. hope all goes well if it doesnt you may have a hardware problem

---

### Post by Cup of Squirrels on 2006-11-14
another edit:

Yep, did "sudo apt-cdrom add", then "apt-get install linux-386" at the command prompt.


I then did "sudp apt-get install ubuntu-desktop" and get a "Couldn't find package ubuntu-desktop"


Is there an alternative command to install the ubuntu-desktop? I assume it is installed directly from the cd to the system.

---

### Post by 7creature on 2007-02-12
Same problem here. This is 5th distro of Ubuntu I am trying to install (various live cds and AMD64 alternate cds). Finally I've at least achieved to have base system and boot loader working...

Is somewhere list of packages which are installed during "select and install software" step of Ubuntu installation? Would be handy...

P.S. I am/was installing from ubuntu-6.10-alternate-i386.iso, hash check was ok, and I've checked burned CD (and even compared to ISO) twice - there were no errors.

---

### Post by 7creature on 2007-02-12
Hmm, well, there were definitely some errors but seems that aptitude install ubuntu-desktop (from ubuntu alternative cd as repository) did it. I am in Ubuntu and so far no problems.

Now to solve those graphic problems...

I wonder what was the problem with the installation anyway...

---

### Post by Dave / Mosaic on 2007-02-23
If anybody is interested, I've had the same problem here with the installer gagging somewhere during "Select and Install Software"...  I'm pretty sure it's a bug in the installer; not your bad CD, not your hardware, not your BIOS (I'm on a PowerMac / PPC platform and it does the exact same thing others notice).

I've tried maybe four or five different CD images, for Ubuntu, Kubuntu, Xubuntu, of desktop and alternate varieties...  Trying to install everything at once always fails, no matter what ISO I use.  If I just install a base / CLI system from CD it always works flawlessly; going back with apt-get to get the rest of ubuntu-desktop, or xubuntu-desktop, or whatever, also always works too...

(I haven't tried the mini ISO, but in any case i don't want it; I like the everything-on-one-CD approach, so I can go back and install the same identical OS a second time in the future, if things get messed up somehow.)

Just my two cents...

---

### Post by catfishy on 2007-03-13
I had the same problem, right at 6% at "select and install software" with the alternative 6.10.... I was ready to get frustrated when, after it gave up, I told it to try again and this time it went all the way through.  Funny.  But try a second or third time and see if it goes through.  Good luck!

---

### Post by Enginer on 2007-03-21
After speending 3 agonizing days trying to get a Ubuntu server (6.10) OR desktop OR anything I am experiencing a repeating failure 85% on the way thru the LAMP section of "Select and intall software."  I am not a software engineer (only a PE Chemical Engineer) with experience dating from KayPro days.  I have to say this is some of the roughest error-correction coding I have exver experienced.

The computer is a plain-Jane Tekram P5M4-M+ socket 7 with a new Hitachi 164 GB DeskStar hardrive.
I let Ubuntu format and partition it, and started out with GRUB error 18 (the BIOS was set for LBA, which is a no-no.)  Then, I got two days of GRUB Error 17, which I resolved by re-partioning.  Then I was back to GRUB Error 18, which I could not get rid off.

To top it off, when ever I get one of the live CD's up, I end up with multiple Ubuntu screen images which are hard to read.  From WIN 3.1 days I recognized that as a video crd issue.  I used a good hardrive from an identiacal computer runnig W98 to boot an reset the motherboard graphics to CGA.  Didn't help.  Still got multiple images.

Tried going to text mode.  Couldn't find out how to force that from BASH in terminal mode. Wanted text mode so I could learn how to re-format and partition HD from Live CD.

Gave up.  Uses an XP Pro disk to boot and format (NTFS) and partition (150 GB + swap), then managed to finish 6.10 server install.  It is booting even as I type.

Getting a screen full of 99 99 99 99 9... with a message that "Boot from ATAPI CD_ROM: Failure ....)   According to the BIOS settings it should have then tried C, and then A.   Ubuntu can't seem to follow BIOS sequences.

Questions:  How do I force Ubuntu to text mode, I cannot seem to find the much discussed "Alternate CD" images... and,  wish me luck with a Windows server or Gentoo, my next try.:(

---

### Post by Enginer on 2007-03-21
Well, I tried an old copy of SUSE 9.3 with no better success.  I then downloaded the iso for SUSE 10.2, and it crashed try to unpack some "Catalogs"      

I was still staring past multiple images of a bad graphics choice. (I read somewhere that NV cards are not well supported.)    If I could see clearly with one of the Live CD's, I might be able to do a better partitioning job than Ubuntu or Windows XP Pro did.

I wonder if part of the prolem might not be the Hitachi DeskStar 164 GB drive?

---

### Post by Dave / Mosaic on 2007-03-21
Enginer--

I had a very similar flavor of troubles with installation,,,  I never could get the normal live CDs to install, ever, on either the PC or Mac (PPC) platforms that I have here.

I've had good success with the "Alternate" CDs though.  As for where they are,  look here:

[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)

and click on any of the links for "Other installation options", and there you will find the alternate CDs a little way down.

Another useful thing I found is the "Installation guide for the alternate CD", available in i386, PPC, and other flavors.  You can get to it from:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

It's fairly detailed, and you can make the installer very interactive by using things like the "priority=low" or "priority=medium" kernel parameters that you'll find documented in there.  I got the installer to stop incorrectly autodetecting video cards, among other things...

Also:  I've always found that I need to do a minimal install, which in the alternate CD seems to be called "cli", which I assume means command line interface, because it doesn't install X or anything.  If I try to do a more complete install, even from the text-based alternate CD installer, it always crashes somewhere during "select and install software" and makes a horrible mess...  (BTW, same weird problems on both my mac and PC platforms, so it's a pretty high level installer problem)

If you're lucky enough that you get a base / cli system booted, then you can do

sudo apt-get install ubuntu-desktop

(if my memory serves me right; this is documented in some other places in these forums)  and if it all works, after an hour or so you will end up with the same result as the full installation.

There's also this step:

dpkg-reconfigure xserver-xorg

(again, I'm going from possibly faulty memory, but you'll find references to these keywords in the forum archives) that does much of the video and other configuration for X,,,,  such as a lot of weird graphics problems that I was having...

Hope this helps--

--dave

---

### Post by Enginer on 2007-03-21
Although my monitor still shows multiple images of the Ubuntu screen graphics I have managed to get past the software install glitch several times now, and am now doing a Alternate CD install of 6.10 thanks to Dave/Mosaic and the Mirror list.

My monitor (on the target machine) is an old PS/1 but mI tried resetting the motherboard garphics, then went to a Mad Dog NV card and even tried substituting a higher resolution monitor to no avail.

I have checked "Receive eMail from forum members" in my profile.  I'd like to correspond with a Linux Guru in the Lithia-Brandon-Tampa (FL) area if someone would be good enoughto contact me.  I'm anticitpating an on-site help session, with ye ole pizza and beer or whathaveyou.  Maybe even better....

I told my wife that I was not gonna let the Penguin beat me!  I need to get this server up and running.

---

### Post by Enginer on 2007-03-21
OK.   (Not OK).    Although I did a fresh burn of ubuntu-6.10-alternate-i386.iso, I could see NO difference in the install process compared to the live CD.    There was a minor glitch installing software, and when it finished (3 minutes ago) it failed to boot with ye ole GRUB Error 17.   This on the same harddrive that booted 6.10 live after installation.

There must be more to GRUB Error 17 than meets the eye.  Why can't Ubunto (Debian) prepare it's own partitioning so that it is happy with it?

I had hoped the Alternate install would be more interactive than it was, and now I don't even know if it would leave me with the multiple graphic images after install.

Please, someone give me an eMail shout....Saturday.  I'm going camping at Rainbow Springs Thursday and Friday.

---

### Post by josel777 on 2007-06-13
> **catfishy said:**
> I had the same problem, right at 6% at "select and install software" with the alternative 6.10.... I was ready to get frustrated when, after it gave up, I told it to try again and this time it went all the way through.  Funny.  But try a second or third time and see if it goes through.  Good luck!

I am having the exact same problem with 7.04 AMD 64 alternate CD. It will not go past 6%!

---

### Post by Dave / Mosaic on 2007-06-13
This happened to me, very consistently, numerous times, with all different configurations of CDs, options, etc...  I wonder if what works for me, would work for you...?  What finally worked consistently for me, was this:  Use the Alternate CD; do a minimal (CLI, or whatever they call it) installation; once the minimal system boots after installation, configure the internet connection, and then do "sudo apt-get install ubuntu-desktop", or something similar, on which subject there are many references in the archives of this list.

Hope this helps...

--dave

---

