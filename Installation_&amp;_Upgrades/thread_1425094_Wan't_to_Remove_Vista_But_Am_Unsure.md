---
title: "Wan't to Remove Vista But Am Unsure"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by kliffs on 2010-03-08
Hi, 
I have vista currently installed on my Acer Aspire 5220 laptop and am thinking about removing it for ubuntu. I just need a little bit of convincing to make the switch. Also i have a 2nd generation iPod touch running 3.13 firmware. Is there a way to put music and videos on it using ubuntu. I am open to any suggestions and appreciate your help.

---

### Post by helblaze on 2010-03-08
I believe that there is some software in the software manager that lets Ubuntu read your ipod (10.04 will read your ipod from installation)  Unfortunatly not everyone can make a total switch to linux.  Since I got a lot of stuff that won't work in Ubuntu or other distrobutions, and my Printer only works with Windows and Mac OS X. To be honest I would still dual boot, though maybe upgrade Vista to Win7, since it  has vast improvements.

---

### Post by anoop999 on 2010-03-08
If you want to keep Vista you can shrink your Vista partition and install Ubuntu in the empty space, creating a dual boot system. You should shrink the Vista partition from within Windows before installing Ubuntu.

---

### Post by presence1960 on 2010-03-08
> **kliffs said:**
>  **_I just need a little bit of convincing to make the switch._**

If you are not ***_"convinced"_*** of your own accord do not make the switch.

---

### Post by Mark Phelps on 2010-03-09
> **kliffs said:**
> ...I am open to any suggestions and appreciate your help.

In that case, I would strongly suggest you work in dual-boot mode for a while, focusing on getting your iPod touch to work, before you make any permanent switch.

If you are successful using your iPod, and you have installed in a true dual-boot (not inside Windows using Wubi), it's a pretty straightforward effort to THEN remove Vista and move over to using Ubuntu full-time.

---

### Post by Choragos on 2010-03-09
Absolutely.  The dual boot (usually) works brilliantly.  

Why do you suggest re-partitioning from windows first?  I've always (personally) had better luck letting the installer do it.  I am, however, kind of a hack and it's better to be lucky than good in my case.

---

### Post by coffeecat on 2010-03-09
> **Choragos said:**
> Why do you suggest re-partitioning from windows first?

I don't think the earlier poster was suggesting re-partitioning with Vista. They were specifically advising shrinking the Vista C: partition using the Vista resizing utility. This is good advice. There have been many reports of people making their Vista partitions unbootable by shrinking them with Gparted. [See here, for example]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"). That link airily asserts that the problem is easily fixed with the Vista install DVD. Trouble is, this has to be the Microsoft install DVD, not an OEM image disc.

This was not a problem with XP. Perhaps your experience was with XP.

---

### Post by presence1960 on 2010-03-09
> **coffeecat said:**
> I don't think the earlier poster was suggesting re-partitioning with Vista. They were specifically advising shrinking the Vista C: partition using the Vista resizing utility. This is good advice. There have been many reports of people making their Vista partitions unbootable by shrinking them with Gparted. [See here, for example]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"). That link airily asserts that the problem is easily fixed with the Vista install DVD. Trouble is, this has to be the Microsoft install DVD, not an OEM image disc.

This was not a problem with XP. Perhaps your experience was with XP.

+1

Here is a link to the as yet unresolved bug report: [http://bugzilla.gnome.org/show_bug.cgi?id=379482](http://bugzilla.gnome.org/show_bug.cgi?id=379482)

---

### Post by coffeecat on 2010-03-09
Just to add. I believe that you can avoid this unbootable Vista issue by unticking the "Round to cylinders" box in the Resize/Move utility of Gparted - but I can't be 100% sure. So if anyone wants to try this - on your own head be it.

All I can do is to record my own experience fwiw. On my main desktop I have (a seldom used) Vista on sda1. I wanted to shrink this partition and re-arrange all my Linux partitions. The Vista resize utility hung on me. (:rolleyes:) So, not particularly perturbed if I made Vista unbootable - I have the Vista DVD for repair and was prepared to reinstall if necessary - I booted from the Karmic live CD and shrunk sda1 remembering to untick the "round to cylinders" box.

When I then booted into Vista it had a bit of a moan and insisted on doing a chkdsk, but apart from that it was fine, and has behaved normally ever since. Normal for Vista, that is. :wink:

---

### Post by uRock on 2010-03-09
> **presence1960 said:**
> If you are not ***_"convinced"_*** of your own accord do not make the switch.

+1
Dual boot, install via thumb drive, or lastly install via Wubi (not recommended)

---

### Post by uRock on 2010-03-09
> **coffeecat said:**
>  That link airily asserts that the problem is easily fixed with the Vista install DVD. Trouble is, this has to be the Microsoft install DVD, not an OEM image disc.

This was not a problem with XP. Perhaps your experience was with XP.

In the start menu (Vista and 7) there is a selection to make a backup. Once opened that menu will allow you to make a repair disk, which has the capability of fixing the MBR.

---

### Post by presence1960 on 2010-03-09
> **coffeecat said:**
> Just to add. I believe that you can avoid this unbootable Vista issue by unticking the "Round to cylinders" box in the Resize/Move utility of Gparted - but I can't be 100% sure. So if anyone wants to try this - on your own head be it.

All I can do is to record my own experience fwiw. On my main desktop I have (a seldom used) Vista on sda1. I wanted to shrink this partition and re-arrange all my Linux partitions. The Vista resize utility hung on me. (:rolleyes:) So, not particularly perturbed if I made Vista unbootable - I have the Vista DVD for repair and was prepared to reinstall if necessary - I booted from the Karmic live CD and shrunk sda1 remembering to untick the "round to cylinders" box.

When I then booted into Vista it had a bit of a moan and insisted on doing a chkdsk, but apart from that it was fine, and has behaved normally ever since. Normal for Vista, that is. :wink:

With gparted resizing Vista/7 sometimes it works fine & other times it does not. herman reported about the unchecking the "round to cylinders" but when I tried it Vista still was unbootable. We had a nice discussion about it in a thread over last summer. But I tend to believe it is like the original method of resizing Vista/7 with gparted- maybe it will work and maybe it will not.

The level of the person's knowledge/expertise should determine which path to choose. If inexperienced I would err on the side of caution and shrink windows Vista/7 with it's own disk management utility after defragging & turning off System restore and page file.

---

### Post by presence1960 on 2010-03-09
> **iRock said:**
> In the start menu (Vista and 7) there is a selection to make a backup. Once opened that menu will allow you to make a repair disk, which has the capability of fixing the MBR.

You can repair the MBR to a windows MBR from ubuntu or the ubuntu live CD. Install lilo by running in terminal ```
sudo apt-get install lilo
```Ignore the warning and next run in terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your disk/device, i.e. sda, sdb,sdc, etc

---

### Post by uRock on 2010-03-09
^^^^That's good to know.

---

### Post by coffeecat on 2010-03-09
> **iRock said:**
> In the start menu (Vista and 7) there is a selection to make a backup. Once opened that menu will allow you to make a repair disk, which has the capability of fixing the MBR.

Windows 7, yes. Vista, no. In the backup and restore utility of W7, there is an option, "create a system repair disc", but not in the Vista backup and restore utility. Sorry. I'm posting from Vista now (:oops:) and I've checked.

Also, [see here]("http://www.istartedsomething.com/20070929/vista-sp1-recovery-disc/"), which also describes a hack to be able to make a recovery disc in Vista. But not for the faint-hearted. And, if anyone is reading this thread and needs a Vista recovery disc, you can download it [here.]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (And Windows 7 repair discs too.)

> **presence1960 said:**
> With gparted resizing Vista/7 sometimes it works fine & other times it does not.

It's sod's law, isn't it? I had a proper Microsoft Vista DVD which I could use to do repairs and/or reinstall and my Vista survived Gparted. But some poor soul with an OEM installation and no DVD might have their Vista borked by Gparted.

Life ain't fair. :neutral:

---

### Post by uRock on 2010-03-09
> **coffeecat said:**
> Windows 7, yes. Vista, no. In the backup and restore utility of W7, there is an option, "create a system repair disc", but not in the Vista backup and restore utility. Sorry. I'm posting from Vista now (:oops:) and I've checked.

I'll take your word for it. I have only spent about 20 minutes of my life messing with Vista and that time was spent backing up data to trash the install and write over it with a Windows 7 Pro/Ubuntu dual boot.

---

