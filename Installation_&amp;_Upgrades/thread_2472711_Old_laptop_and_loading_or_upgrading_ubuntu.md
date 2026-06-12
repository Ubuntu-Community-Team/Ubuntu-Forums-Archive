---
title: "Old laptop and loading or upgrading ubuntu"
date: 2022-03-09
forum: Installation &amp; Upgrades
---

### Post by pesilat-2000 on 2022-03-09
Hello,
    I have an old laptop (Dell Inspiron 3520 intel i3) that is setup to with windows and to boot ubuntu 16.04 from a usb.   Can I just create a new usb with ubuntu 20.04 and boot that?   Will my old files from Libre and mp3's etc under ubuntu 16.04 still be safe or will they get wiped out?   I may be getting a ahead of myself because I don't see Dell Inspiron 3520 as a supported device for 20.04.  The hard drive is partitioned already but I still need to boot ubuntu using a usb.  I appreciate your input.

Thanks,
Travis

---

### Post by TheFu on 2022-03-09
**Backup anything you don't want to lose.** This is always required before any OS upgrade. Assume they will be wiped, because *_if you are asking the question, it means you are likely to make a not-so-great setup choice which does wipe everything._* If you haven't setup separate LVs or partitions for your personal data, then it will be wiped ... unless you choose to install over an existing install. Doing that from 16.04 ---> 20.04 will leave a number of crufty config files behind which are incompatible with the way that 20.04 manages many things. Not recommended.

Best to wipe the install and start fresh.

16.04 standard support ended about a year ago. There are plenty of nasty bugs known to the world in the wild waiting to take advantage of unsupported Ubuntu.   Beware.

Just because Dell doesn't support an OS, that doesn't mean it doesn't work.

---

### Post by guiverc on 2022-03-10
I'm using a 2009 dell & using Ubuntu *jammy*. My box is so old it's from intel's range of CPUs the pre-dated the i-series ones (ie. it's *core2 era*!). It's a desktop thankfully (*I find them less annoying them laptops*).

I regularly re-install newer systems over old, in fact with Lubuntu it's a QA (*Quality Assurance*) [testcase]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") called "*Install using existing partition*"  (though personally I prefer thinking of as "*Upgrade via re-install*").  FYI:  The link I provided was intended for QA-testers & not end-users, but the process works for Ubuntu Desktop & all *flavors of Ubuntu *too. TheFu's prior reply did sort of mention it & why it's *not ideal*, but personally I *love* that it's an option with Ubuntu systems.

**Problems with *Upgrade via reinstall* approach.**

Ubuntu 16.04 **had** two upgrade paths; to the next release, ie Ubuntu 16.10  **or **to the next LTS which was Ubuntu 18.04 LTS.  So both 16.10 & 18.04 programs could handle the datafiles of earlier 16.04 programs...  But you're skipping those releases, thus the it's up to you to ensure the programs you use can handle the data files from the versions that came with 16.04; as you're going outside of what Ubuntu QA tests for (ie. *skipping releases*).

Issues can occur; I've had programs that couldn't read prior datafiles (*due to change in database used*) however in my case it was only a RSS news database that wasn't important to me, so I didn't worry about it. I've also had issues when going backwards (*to earlier releases*), but as you know what apps you use & what data matters to you, you'll have to verify it's not going to impact your data.  Problems can occur, but are rare.

I use the *upgrade via re-install* procedure 50+ times a year mostly for *Quality Assurance *purposes, but also as a fast means to *release-upgrade* my own machines when I'm impatient (*usually I'm using my own machine  as a QA-test, ie. with my real data!*) so I know it works; but it's been a long time since I've dealt with *xenial* or a 16.04 system so I'd not likely recall many of the pitfalls you could encounter (*my last xenial installs where [16.04.7]("https://fridge.ubuntu.com/2020/08/14/ubuntu-16-04-7-lts-released/") but that was too long ago to remember*)

Addendum:  You mention *Libre* (*loads of apps use libre in their name*) & MP3s; you'll note I use music in how I describe the Lubuntu Testcase for *Quality Assurance *as an example (*as it's nice to be able to start some music as you verify the install was perfect!*), so I'm using music as an easy way to validate installs very regularly and don't lose any.

---

### Post by ks-alexandr on 2022-03-10
Tell me - how much RAM on a laptop?
This is a very important component on older computers, which determines what needs to be installed.

Next I advise the following:
1. If the RAM is 2 GB or less, find a way to add it. Today, the comfortable minimum is 8 GB of RAM. You can work with 4 GB, but 8 GB is better)))

2. In general, your hardware is quite powerful to use Ubuntu 20.04, but there are 2 comments:

- I advise you to wait for the release of Ubuntu on April 22 (end of April this year) and install it already;

- I advise you to install Xubuntu 22.04 (Ubuntu from HFCE). This will allow you to work with more comfort on this hardware (especially - graphics card).

3. I advise you to make a backup of important files before installing the OS. This should always be done.

4. If you have previously done separate partitions "/" and "/home", then during the installation, do the following:
- partition "/" specify what needs **to be** formatted
- section "/home" specify that you **do not need** to format, specify the login and password are the same as before. this will allow you to use the same user profile as before. But, as noted above, this approach can lead to errors in some programs.

---

### Post by grahammechanical on 2022-03-10
If you install Ubuntu 20.04 on the same USB stick as the one holding Ubuntu 16.04 then will will most certainly lose any files/documents on that USB stick. Do you have two USB ports? If so, then buy a second USB stick, install Ubuntu 20.04 with persistence on it and boot from the 20.04 USB and plug in the 16.04 USB and transfer your files.

Regards

---

### Post by pesilat-2000 on 2022-03-10
The laptop has 8gb of RAM.  The old partition for ubuntu is 100gb.  I've got three usb 2.0 ports.  I lost my original usb stick with 16.04 but created anther to boot from so I can run the old release.  I could save my old files to a different usb then install a new version of ubuntu but I need advice on how not to wipe out my windows partition. 

Thanks

---

### Post by tea for one on 2022-03-11
> **pesilat-2000 said:**
>  I need advice on how not to wipe out my windows partition.

As you have a dual boot system, it is always advisable:-

Back up your personal data from Ubuntu **and** Windows.
Have a supported version of Ubuntu on a USB stick.
Also have a Windows ISO on a USB stick.

Which version of Windows do you have?

---

### Post by ks-alexandr on 2022-03-11
Can you the output from the command terminal from your Ubuntu 16.04?
```
sudo fdisk -l
```

---

### Post by pesilat-2000 on 2022-03-13
I'll do it once I boot up Ubuntu.  I want to backup my Win 10 partition before but I need to get a big enough USB first.  I'll keep you posted once I do.

Thanks.

---

### Post by pesilat-2000 on 2022-04-01
[/home/ubuntu/Pictures/Screenshot from 2022-04-01 16-34-53.png]("https://ubuntuforums.org/home/ubuntu/Pictures/Screenshot from 2022-04-01 16-34-53.png")

---

