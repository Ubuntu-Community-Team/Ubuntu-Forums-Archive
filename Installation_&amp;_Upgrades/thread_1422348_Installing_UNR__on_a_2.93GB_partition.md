---
title: "Installing UNR  on a 2.93GB partition"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by brain frog on 2010-03-05
I have a netbook i am quite sure it is based on the msi wind which came with windows XP installed.

I noticed that on the hard drive there is a partition called recovery EISA Configuration. I am not 100% sure what it contains but I am quite sure it is todo with the image saying "the tec guys" that comes up when I boot up, this is software I am never going to use if I have any critical problems I will reformat or be able to fix it myself.

Would it be possible to install Ubuntu netbook remix on this partition that has a total size of 2.93GBs? I know it is slightly below the minimum requirement, however i am thinking that I could simply prevent some software that I am not likely to use from being installed with the operating system.

---

### Post by raymondh on 2010-03-05
> **brain frog said:**
> I have a netbook i am quite sure it is based on the msi wind which came with windows XP installed.

I noticed that on the hard drive there is a partition called recovery EISA Configuration. I am not 100% sure what it contains but I am quite sure it is todo with the image saying "the tec guys" that comes up when I boot up, this is software I am never going to use if I have any critical problems I will reformat or be able to fix it myself.

Would it be possible to install Ubuntu netbook remix on this partition that has a total size of 2.93GBs? I know it is slightly below the minimum requirement, however i am thinking that I could simply prevent some software that I am not likely to use from being installed with the operating system.

Your system, does it require that you make recovery CD''s?  If so, do.  Also check the manuals if to recover winXP, you are required to use the recovery cd AND the built-in recovery partition.  Of course, it would not matter if you have an original XP install disc.

At any rate .... 2.9GB is too small for a ubuntu install. Not even for the first update after install. UNR is really Ubuntu optimized for the netbook (screen size).  At minimum, I would give ubuntu at least 15GB.  Even at that, I would remember that figure once I start saving media files :)

Best,

raymond

---

### Post by brain frog on 2010-03-05
I have managed to get hold of a windows xp oem disk as you can guess microsoft chose not to supply it with the netbook. I managed to download it from a website that to my knowledge was trustworthy and it was advertised as untouched version of the oem disk but can not be 100% sure but all tests on it say it is good and maleware free. When used with a genuine CD key it is perfectly legal.

I have been considering getting myself a new laptop hard drive I have seen good 320GB ones for under £40.

---

### Post by raymondh on 2010-03-06
I have an MSI wind (U100).  It performs well for what I use it for (email, browsing, word processing).  It has the RTL8187se wifi card.  I placed a 2GB RAM and a 320GB, 7200 RPM HD.  Just for the heck of it, I 3-boot this wind with Ubuntu 9.04, Win7 Pro and OSX.  My Ubuntu install started with 8.10 and had to source drivers for the wifi to work.  9.04 works out-of-the-box.  I had problems with X when I tried karmic hence decided to downgrade it to Jaunty in the meantime.  For a while (in 8.10), I experimented with UNR which lasted only about 2 weeks.  I don't know if the switcher works well in more recent UNR versions. Note that I have always been either a regular, gnome desktop user or, a minimal install user with either LXDE or XFCE.  That said, my wind is gnome with AWN as the navigator.  I have had no problems to date with this set-up.

Having 320GB ... my partitions are set-up in this manner (actual numbers have been rounded-off):

60gb Win7 - primary
200gb OSX - primary
60gb - Extended
2gb - swap, logical
15gb- root, logical
40gb- /home , logical

Being 3-boot, I am able to read/write into/from linux.  HFS (OSx) has journaling turned off prior to mounting.  Of course, win7 and nTFS is reda/written by/from by linux.

Am sorry, I don't know about 'that' web-based XP download.

Best,

Raymond

---

