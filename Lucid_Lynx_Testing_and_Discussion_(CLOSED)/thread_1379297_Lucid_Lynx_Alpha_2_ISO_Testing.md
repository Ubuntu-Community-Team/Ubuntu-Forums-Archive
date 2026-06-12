---
title: "Lucid Lynx Alpha 2 ISO Testing"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-01-12
Alpha 2, which will be the second milestone release of the Lucid Lynx development cycle, will be out in two days. Like every milestone release, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the release candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for Lucid Lynx Alpha 2 are now available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

You may want to [use rsync]("https://help.ubuntu.com/community/RsyncCdImage") to update your existing disc images. A good way to download a testing image and keep it up to date is the dl-ubuntu-test-iso script, which is part of the very handy ubuntu-qa-tools package ([click to install]("apt:ubuntu-qa-tools")).

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. You can also follow [the #ubuntutesting tag on Twitter]("http://search.twitter.com/search.atom?q=%23ubuntutesting"), and feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-01-12
Thanks for putting this up.

I can hardly believe this is an Alpha 2.

Xorg is now stable enough that I removed the xorg edgers repo from my installed Lucid. I don't need that fresh X crack anymore :D

I only encountered one tiny bug, the cd-checker still fails. Pretty awesome IMHO.

---

### Post by MacUntu on 2010-01-12
Man, the download is slow. Next time I'll use zsync/rsync for sure.

---

### Post by ranch hand on 2010-01-12
On mine when restarting the CD did not eject nor did I get the message to remove the CD.  When I had done that and het enter the ISO did not shut down.

While this is serious I am sure it will be fixed before A2 release.

Other than that (I always forget to try the CD integrity check) everything just worked great.  Installer, partitioner.

The only other "bug" is that disgusting slide show is still there with no way to opt out.

---

### Post by ronacc on 2010-01-12
use my method for opting out , the installer is fast just go have a cup of coffee while it does its thing .

---

### Post by ranch hand on 2010-01-12
Well there is that option but I actually like to watch the install and would really like to have the old, small progress bar as an option.  I screen as big as the slide show uses would also be a great place for terminal output during install.

Besides that, I don't really drink much coffee.

---

### Post by ronacc on 2010-01-12
well bourbon then :D I had to give that up , my liver was drowning :(

---

### Post by ranch hand on 2010-01-12
I forgot to ad that I am not getting any errors when booting and it boots pretty fast.

I was just over there and checked because I do have the "edgers" ppa on that one.  Haven't played with it yet.  Have more stuff to dump over there.

Will go over and play a little on it later.  I did take time to change the theme need to change the xsplash/gdm background image.  That particular brown is not attractive.

---

### Post by VMC on 2010-01-12
> **ranch hand said:**
> ... I actually like to watch the install and would really like to have the old, small progress bar as an option.  I screen as big as the slide show uses would also be a great place for terminal output during install.That's one of the benefits on Kubuntu. Just the progress bar. I really like that part of Kubuntu...One problem though. It doesn't work](*,) At least manual partition doesn't. It crashes no matter what I do. I've resorted to the debian-installer, aka alternate.

> **MacUntu said:**
> Man, the download is slow. Next time I'll use zsync/rsync for sure.That's what I've been using now. zsync. Much faster, after I figured it out.

---

### Post by MacUntu on 2010-01-12
Ha! The best part was the wrong md5 sum -> re-downloaded the CD with 150kb/sec. 

YAY! :D

Doing some server installs now (looking at a precious progress bar). :P

---

### Post by Ibidem on 2010-01-12
I'm downloading the alternate install now; I'll try it in VirtualBox (none of the ISOs except netboot are small enough for me to install).
It may wait till tomorrow, though; Firefox says I have a few hours left.
Netboot probably hasn't broken recently, and worked last I knew.
I might see about tweaking the CD...or might not.
Ibidem

---

### Post by vishalrao on 2010-01-12
> **VMC said:**
> Kubuntu...One problem though. It doesn't work](*,) At least manual partition doesn't. It crashes no matter what I do.

Any chance this could get fixed for Alpha 2 itself? By the time I download candidate ISO on my slow broadband it will be Beta1 time already :loflag:

How can we gather info from VMC about the crash to report for bug fix?

---

### Post by vishalrao on 2010-01-12
> **VMC said:**
> That's one of the benefits on Kubuntu. Just the progress bar. I really like that part of Kubuntu...

ahaha, not any more it seems: [https://launchpad.net/ubuntu/lucid/+source/ubiquity/2.1.10](https://launchpad.net/ubuntu/lucid/+source/ubiquity/2.1.10)

> 
Bring the KDE frontend slideshow handling into line with GTK frontend.


---

### Post by phillw on 2010-01-12
I'm guessing that bringing my A1 upto A2 will not be suitable for testing on :(

I'm on a laptop, so am limited with hard drive (80GB) As I still have legacy Vista, 9.10 for my fall back O/S and 10.04 A1 .. things are getting a bit tight !!

Whilst others can do tests for installation, I'd be more than happy to do the laptop stuff of suspend, play with external usb keyboard etc.

If it is a case of having to do a complete fresh install of A2, would it be cheating to rsync my /home to safety & then rsync it back ?

Don't get me wrong, I'll do it - Just it will take me a while to get my LAMP back, install FileZilla, BlueFish editor etc. back onto 10.04 A2

Just asking 

Regards,

Phill.

---

### Post by ranch hand on 2010-01-12
I, personally, would loose the MS crap as a backup and put in a 10GB / and 10Gb /home for 9.04 or 9.10 as backup and then you would have lots of room for 2 Lounge Lizard installs.

You also wouldn't have that crappy OS on there insulting your box.

---

### Post by PaulInBHC on 2010-01-12
When the games that I play actually work in wine or native, I will do that. In the meantime, I'm stuck with Windows.

---

### Post by ranch hand on 2010-01-12
Ah, that would be it then.

I do not play games on the computer so I do not think of it.

I do play games with the box (testing for instance).

---

### Post by MacUntu on 2010-01-13
Woohoo, new candidate images! Thanks to rsync I just had to download 47.09MB. :D

---

### Post by phillw on 2010-01-13
> **ranch hand said:**
> I, personally, would loose the MS crap as a backup 

You also wouldn't have that crappy OS on there insulting your box.

I wish, also - but the accounts software runs on a Mac - As piglet is a backup machine in case the accounts computer & its backup one both die, and the account s/ware is Mac or Win I'm stuck with Win :-(

Phill.

---

### Post by VMC on 2010-01-13
> **MacUntu said:**
> Woohoo, new candidate images! Thanks to rsync I just had to download 47.09MB. :D

Yea I know, that's nice. I'll ever go back to downloading full again(only once, of course). I use zsync. I guess rsync is similar, ones client side ones server, from what I gathered.

---

### Post by ronacc on 2010-01-13
for some reason I can't get zsync to work on the ISO .
```
ron@ron-desktop2:~/tmp/iso/a2$ zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
failed on url http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
could not read control file from URL http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
ron@ron-desktop2:~/tmp/iso/a2$ 

```
the .zsync file is visible at the URL and I can d/l it manualy .

EDIT  the problem was I CAN'T SPELL

---

### Post by jerrylamos on 2010-01-13
Can't wait for Alpha 2!  Due tomorrow??

As of today's updates, Jan 13, with 2.6.32-10, both intel video graphics and ati radeon graphics are busted on 2.6.32-10.  Launchpad bugs #520594, #507000.

Hmmm.

Jerry

---

### Post by VMC on 2010-01-13
> **ronacc said:**
> for some reason I can't get zsync to work on the ISO .
```
ron@ron-desktop2:~/tmp/iso/a2$ zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
failed on url http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
could not read control file from URL http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zysnc
ron@ron-desktop2:~/tmp/iso/a2$ 

```
the .zsync file is visible at the URL and I can d/l it manualy .

EDIT  the problem was I CAN'T SPELL

I spelled alright, but the wrong distro?! I was happily zsync'ing Kubuntu when I realized it had an ETA of 2 hours! Woa. Then I noticed I was using the Ubuntu zsync. Won't make that mistake again.

---

### Post by ronacc on 2010-01-13
how do I query a drive for its uuid ? it is no longer shown in "properties" and I need to get the uuid so I can edit my grub.cfg to boot the A2 candidate .

---

### Post by ranch hand on 2010-01-13
Try this;
```

sudo blkid

```

---

### Post by ronacc on 2010-01-13
that did it , thanks .

---

### Post by kansasnoob on 2010-01-13
Possibly a bug in parted in the 1386 Live CD. 

Choosing to use the Manual (advanced) partitioning option, without pre-partitioning, parted wouldn't allow me to remove one of two SWAP partitions which I'd no longer need because I was formatting it's / partition.

Further explanation: I have a small 30GB drive that I use for iso testing. I always begin with use the whole disc.

Second I choose the auto-resize (side by side) and third I use manual partitioning to see if parted will allow me to change things as I wish.

Sometimes I repeat the manual install, once without pre-partitioning, and again using Gparted first.

This is the first time I've had parted fail to delete whatever I tell it to. Anyway I need to try and duplicate but had to get on with other stuff.

Hopefully this PM I can give it another try and see if I can duplicate. Oh, I was able to complete by selecting "Quit" which took me to the Live Desktop.

I then used Gparted and got-r-done so it's a minor bug at worst. I'd think anyone using the manual option has some basic knowledge so they can review their changes before applying ;)

---

### Post by Ibidem on 2010-01-13
Alternate install ISO (Ubuntu) installs in VirtualBox (repository version).
I'll see about low-ram...
What's the official target for minimum ram?  I recall it was a bug when Hardy failed in less than 64 MB, and I see "32 megabytes" quoted here and there.
Ibidem

---

### Post by Ibidem on 2010-01-13
32 MB--WILL NOT BOOT. (Kernel panic-out of memory and no processes to kill)
64 MB-Working right now...
Ibidem

---

### Post by Ibidem on 2010-01-13
> **Ibidem said:**
> 
64 MB-Working right now...
Ibidem

Well, sort of.. You must select Expert mode at boot, select the lowram installer package (run it regularly),
and MANUALLY PARTITION the HD.  Automatic partitioning will fail.  
Where do I file the bug reports?

Bug 1: Kernel will not boot in 32 MB ram
Bug 2: Autopartitioner will not run in 64 MB ram
Ibidem

---

### Post by VMC on 2010-01-13
> **kansasnoob said:**
> Possibly a bug in parted in the 1386 Live CD. 

Choosing to use the Manual (advanced) partitioning option, without pre-partitioning, parted wouldn't allow me to remove one of two SWAP partitions which I'd no longer need because I was formatting it's / partition.

... If this is from Ubiquity, then yes, it probably is a bug. I was able to fanagle it around in ubuntu and finally get the manual install to work, but in Kubuntu, the manual method fails miserably, so I opted for Alternate install.

---

### Post by kansasnoob on 2010-01-13
> **VMC said:**
> If this is from Ubiquity, then yes, it probably is a bug. I was able to fanagle it around in ubuntu and finally get the manual install to work, but in Kubuntu, the manual method fails miserably, so I opted for Alternate install.

I can almost guarantee you it's a bug in parted. And it's not only in the Live CD.

I was trying things: deleting, creating, resizing partitions etc. when this happened:

[http://ubuntuforums.org/showthread.php?t=1380451](http://ubuntuforums.org/showthread.php?t=1380451)

So I'm a bit worn out!

Believe me parted/Gparted has a problem in Lucid. It needs more testing and some good bug reporting.

Sadly I must get busy with filing some homestead exemption tax forms for people and I'm only one person.

---

### Post by Psumi on 2010-01-14
Too bad the release notes aren't up yet: [http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

---

### Post by Resu on 2010-01-14
> **Psumi said:**
> Too bad the release notes aren't up yet: [http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

Well it says "Acces denied". Most likely they're finishing it up and will put it live when they're done.

---

### Post by Usufruct on 2010-01-14
Aye, there was nothing there this morning, now it's access denied.  Change = good.

I haven't installed Alpha 2 because (sigh) my thumb drive is full of windows ISOs for work and I'm having a brasero bug in Alpha 1 that's preventing me from burning a cd.  I know there are other ways, but I can just wait until I get home :-p

---

### Post by VMC on 2010-01-14
The alternate-daily's have now reported the 14th. So it looks like A-2 anytime soon.

---

### Post by jerrylamos on 2010-01-14
MD5SUM is the same for i386 as the daily build on Jan 13.  

CD does NOT BOOT on IBM THINK CENTRE A30 with i845G video graphics.  Period.  Freezes at the point enter is hit on the initial CD boot frame.

Tried all the usual tricks, none work.  

Even the latest from canonical:
sudo apt-get install --reinstall xserver-xorg-core 
cannot be done because recovery mode won't work at all so can't sudo.

Hmpf.

Jerry

p.s., release notes refer to bug #506418 which says there's a problem however very unclear; what they suggest doesn't work for me.  Guess I'll wait a few days....

---

