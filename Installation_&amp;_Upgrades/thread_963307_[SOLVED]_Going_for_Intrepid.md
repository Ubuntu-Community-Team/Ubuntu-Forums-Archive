---
title: "[SOLVED] Going for Intrepid?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-10-30
I have two questions regarding upgrading from 8.0.4.1 to 8.10. First of all I got an email from getdeb saying:

> It is with great pleasure that we inform you that a new Ubuntu Linux version will be available tomorrow. Ubuntu 8.10 brings hardware support improvements, new features and problem fixes.
Please note that upgrading your system with getdeb packages installed is not supported by Ubuntu and is strongly discouraged by the GetDeb team.

In order to perform a smooth upgrade please make sure you remove all getdeb packages BEFORE starting the upgrade, you can use the following procedure:
[http://www.getdeb.net/docs/uninstall.pdf](http://www.getdeb.net/docs/uninstall.pdf)

If you need upgrade instructions read [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Why is this so? It's kinda strange i  think to remove software because you have to upgrade the system. I remember I did an upgrade from Gutsy to Hardy on two machines. It all went smooth without removing any .debs. Anyway, of course I'll do it. It just seems very strange to remove --> upgrade --> then reinstall the apps again.

**Second:** can anyone tell me how ATI are doing on Intrepid Ibex? And what will happen to my current ATI driver version 8.9 (downloaded from AMD) if I upgrade to Intrepid?

---

### Post by Partyboi2 on 2008-10-30
> Why is this so? It's kinda strange i think to remove software because you have to upgrade the system. I remember I did an upgrade from Gutsy to Hardy on two machines. It all went smooth without removing any .debs. Anyway, of course I'll do it. It just seems very strange to remove --> upgrade --> then reinstall the apps again. Its just to void any possible breakage.

---

### Post by peakshysteria on 2008-10-31
Hmm, not sure if I'm supposed to uninstall the current working ATI driver (version 8.9) before upgrading from Hardy Heron (8.0.4.1) to Intrepid Ibex (8.10) or not. I can't find any documentation on how to handle graphics driver during upgrading from one release to another. Anyways:

Some positive old news regarding we the ATI-people: [Canonical Publishes ATI Catalyst 8.10 Beta]("http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1")

Is the 8.10 version of the ATI driver compatible with Intrepid Ibex or should I wait for the 8.11 version?

---

### Post by peakshysteria on 2008-11-01
Hate to do it but;

*BUMP*

---

### Post by markbuntu on 2008-11-02
You will most likely have very real problems upgrading if you have installed unsupported packages, like those from getdeb of drivers from ati. Your best bet would be to first run the live version of intrepid to make sure it will work with your hardware, and then install it in a separate partition.

Anyway, if you have finally gotten your hardy install working smoothly, why rush into an uneccesary upgrade. If you just look in the forums you can see that a lot of people are having serious problems with Intrepid upgrades. Just wait a few weeks or months until these are cleared up.

I have been trying to install Intrepid from alpha5 to the current release without a successful boot but I have a separate hard drive dedicated to this so it is not a big deal to me if it does not work. I have two other stable installations I can use. 

Unless you have some compelling reason to upgrade now, like hardware problems that are for sure fixed in Intrepid, there is no real reason to upgrade immediately.

---

### Post by peakshysteria on 2008-11-02
Nono, my ATI driver are from the [AMD pages]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") (not from getdeb). I hear you man. Just a few things in Intrepid I would really like to check out. But like you say there is no hurry. So I'm still on Hardy (and enjoy it very much).

Phoronix tells us:
[Canonical Publishes ATI Catalyst 8.10 Beta]("http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1")

[X.Org 7.4, Mesa 7.1 In Ubuntu 8.10]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_xorg&num=1")

WHich seems very promising if you ask me. My main concern is Intrepid handles my graphics driver when I eventually upgrade. If I understand Phoronix right it will just skip my current 8.9 version of the driver and install the 8.10 version which seem to support the latest Xorg coming with Intrepid.

Anyways, like you recommend I'll wait a few more weeks if I can handle it :)

---

### Post by markbuntu on 2008-11-03
I just installed Mandriva One 2009 on my "experimental" hard drive and it works just fine with the 2.6.27 kernel and fglrx 8.10 and my HD3650 card so the problem is not unsolvable. We can hope that Intrepid is not too far behind with this issue. 

If Intrepid can get my realtek ethernet card working I might have a chance to figure out what is going on and actually get Intrepid to run someday but without graphics and no internet connection, it is really not worth bothering with at the moment.

---

### Post by peakshysteria on 2008-11-11
How can I update my current ATI driver (on Hardy)? It would be nice if there were an option for autoupdating the driver. And it would be nice to be able to roll-back the driver as well.

On my current Hardy install I used the [Method 2: Manual Install Method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") right after a clean install. It worked very smooth. But there really should be an update section in the wiki. Neither of the two guides (Hardy, Intrepid) have this. And I can't find anything on it.

The [Ubuntu Intrepid Installation Guide's]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") equivalent seem to be: [4: Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually") if I'm not mistaken.

And I'm still not sure if I update (or not); will Intrepid keep my current ATI driver or will it not?? [The release notes for Intrepid]("http://www.ubuntu.com/getubuntu/releasenotes/810#ATI%20%22fglrx%22%20video%20support") says to disable the driver in the Hardware drivers manager if your within the range of Radeon 9500 - X600 Series of cards. I have also seen threads were people have disabled the driver and then enabled it after an upgrade with luck. I'm just outside the mentioned series of cards. Any experiences from other people would be welcome :)

---

### Post by peakshysteria on 2008-11-13
Hate to do it but: *BUMP*

AMD has released [version 8.11]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") now. The release notes states:> Driver version: 8.552 NEW FEATURES: (1) RHEL 4.7 support. (2) Display scaling to HDTV timings/resolutions. (3) Control Center option to display an ATI CrossFireX logo when ATI CrossFireX is enabled. (4) Xorg 7.4 (Xserver 1.5) support ISSUES RESOLVED: (1) Automatic power state changes when unplugging or plugging AC power. (2) Segmentation fault in amdcccle when launched as root under SuSE 11. (3) Corruption when playing videos using XvMC with mplayer. (4) X startup failure in dual-head mode with only one monitor connected. KNOWN ISSUE: (1) Installing the driver on Ubuntu systems using the community-supported Ubuntu packaging mechanism leads to a failure to load the kernel module resulting in 3D acceleration being disabled. Please install this driver release using the interactive installer instead.

Can anyone give some hints their experiences on the latest driver and Intrepid?

---

### Post by peakshysteria on 2008-11-18
After an irritating trouble with recurring problems with sound in Flash I decided to make the jump and upgrade to Intrepid. After the upgrade I also got the black screen of death. Rebooting gave me low graphics mode (strangely enough with perfect aspect ratio). Had some trouble with getting my ATI driver up and running. But after following: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") After a restart everything booted fine and dandy. Smooth as ever. With working flash, java, ATI CCC, Compiz, SAMBA, NTFS, Google Earth, Mozilla Firefox, Mozilla Thunderbird, Deluge etc.

```
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.1.8087 Release

Intrepid seem stable as a rock (but I guess it's still early coming from a fresh upgrade). Yay for now anyways :)

Not sure which version of the driver I am running since my last success was with a manual install of the 8.9 driver. Have never made it before when I've tried the *Ubuntu way*. AMD CCC says: version 8.543. Is this the so called 8.10 driver? The release notes heading for 8.11 (pdf) is named 8.552. But the notes itself says 8.452!? Kinda makes my head spin....can anyone clear up this mess?

---

### Post by markbuntu on 2008-11-20
8.543 is Catalyst 8.10.

---

### Post by peakshysteria on 2008-11-20
Thanks man. All is working very smooth. So I'm going for this one as long as there's no apparent regressions.

But you being an expert and all markbuntu :) When upgrading, if I choose to do so, is it enough to just download the latest driver from AMD and install it? Will this replace the current one without problems?

---

