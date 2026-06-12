---
title: "&quot;Select and Install software: Installation step failed&quot;"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by taugust04 on 2008-05-02
Hi,

I'm having some issues installing Ubuntu 8.04 and Kubuntu 8.04.  Using the alternative x86 installer cd's for both.  Cleanly formated 60GB hard disk.  Install progresses normally, and then I receive a red screen during the "Select and install" software phase of the installation.  Error reads: installation step failed.  Gives me the option to go back and retry.  Fails again on retry.  Again this happens both the Ubuntu and Kubuntu alternative CD's I download.  Checked the CD's and they verify fine.

This is the first time I've seen this error during an installation.  I've installed previous versions of Ubuntu, Kubuntu, and Xubuntu on this laptop without issue.  Is anyone else seeing this?  I don't know how to get any more error messages that could be useful to the board.  Thanks for your help.

---

### Post by Pumalite on 2008-05-02
I can only advise you to burn a new CD at 4x or less after doing md5sum because I've used today both downloads without problems.(check your partitioning scheme)

---

### Post by taugust04 on 2008-05-02
> **Pumalite said:**
> I can only advise you to burn a new CD at 4x or less after doing md5sum because I've used today both downloads without problems.(check your partitioning scheme)

Thanks for the advise.  Both disks I tried were burned at 16x on a Pioneer DVR-105 drive, and the disks verified OK.  I will try a re-burn now at a lower speed, but I'm not expecting a different outcome.

---

### Post by Pumalite on 2008-05-02
Download ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install it. Go to Mode>ISO>Burn. Select 1x. Use good quality CD-R

---

### Post by taugust04 on 2008-05-02
> **Pumalite said:**
> Download ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install it. Go to Mode>ISO>Burn. Select 1x. Use good quality CD-R

Thanks Pumalite.  Unfortunately, the only computer I have access to right now is a Mac.  The laptop I'm installing on did have Windows, but I just blew that entire partition away trying to install Ubuntu and Kubuntu.  I have a new disk burning right now at 4x in Apple Disk Utility.

From your previous post, I also verified the partitioning scheme.  Both times I used the "Guided: Use entire disk" option, so it should be repartitioning/reformatting the drive each time I've tried to install.

Again, thanks for your help so far.

---

### Post by Pumalite on 2008-05-02
Good luck.

---

### Post by jepes on 2008-05-02
I have this similar problem, the difference is that i am installing  it to a virtual machine (*virtualbox*) and im using the downloaded image directly (*I have already verified the md5 sum*). So, I thinks its not just the way you burned the cd that cause the problem.

---

### Post by taugust04 on 2008-05-02
Well the CD I burned at 4x failed the checksum.  I'm suspecting the ISO I downloaded might be corrupted.  So I'm re-downloading the Ubuntu 8.04 alternative disk.  We'll see how it goes.  I tracked down a Windows PC to use so I will attempt to use the disk burning software earlier in this thread.

Thanks again to all who have responded so far.

---

### Post by taugust04 on 2008-05-02
This issue was resolved with a new download of the ISO and a re-burn.  Passed the verification and checksum tests.  Thanks again to everyone for all the suggestions.

---

### Post by Pumalite on 2008-05-02
You are welcome.

---

### Post by BHTX84 on 2008-05-06
I'm having this same problem..

Attempted to install Ubuntu well over a year ago I think (7.10 I think it was?), without success.  I remember having similar problems during the installation, but finally managed some how.  Then, after a week of fooling around with it, I was never able to set the correct screen resolution..

Yesterday, I spent ALL DAY trying to find a linux distro that works.  I first tried the newest Ubuntu by downloading the live cd and burning it.  After messing with that for over half the damn day, I finally gave up.  It kept screwing up and giving me strange errors half way through the installation.  So, then I tried Fedora 8, which gave me different errors as well.  So, then I tried the Xubuntu alternative iso, which actually installed completely after the THIRD try!  However, it was JUST like the situation over a year ago with my previous attempt at Ubuntu.. I couldn't get the screen resolution corrected.

So, here I am now trying to install Ubuntu again, but with the alternative iso instead of the live cd iso.  It's what most people seem to be using now, and I've come across a couple more suggestions regarding the resolution problem that I'd like to try.

I must be crazy, because this is ridiculous.
Same exact situation as a year ago (or however long ago it was)..
XP went nuts, forced to format/reinstall, decide to have a go at linux instead.

With Winblows, it might last a week.  Maybe a month.  Maybe even a year if you're lucky.
With Linux, goodluck even getting the damn thing installed.

I just keep telling myself not to give up.  But that's what I did last time, and I finally did after fooling with it all day and night for a week straight.

---

### Post by Pumalite on 2008-05-06
Posting your specs and being more specific with your problem would help people in this forum help you.

---

### Post by BHTX84 on 2008-05-07
Hi.  This pc that I've been trying to convert to a linux box for the last decade is an oldish HP Pavilion 750n.. 1.6p4, oem asus mobo, 845 chipset, tnt2-m64, 512mb, 80gb WD hdd, etc.

As for my specific problem, I assumed the title of this thread would answer that question.  As for being more specific about it, well.. unfortunately, due to these kinds of issues during every attempt to use the OS.. I'm new to Linux, so I can't be more specific about it than that.  I can't be too concerned with any potential future problems right now if it won't even complete the installation.

I threw the previous alternate disc in the trash and burned another one at 1x using your recommended ImgBurn software, only to end up with the same exact result.

I wonder how many hours I've spent all together.. both this time as well as last time.. attempting to run Linux (or simply complete an installation process) on just this machine alone.  Actually, I don't really care.  I just want it installed for gods sake.

This is unreal.  I would have never imagined anything like this.  Trying distribution after distribution, and none of them work!  It makes no sense to me.

---

### Post by Pumalite on 2008-05-07
Graphics?
Or post:
lshw

---

