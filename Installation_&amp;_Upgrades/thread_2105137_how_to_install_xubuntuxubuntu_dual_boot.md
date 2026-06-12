---
title: "how to install xubuntu/xubuntu dual boot"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-01-15
How do I install Xubuntu in one harddrive partition and another xubuntu in another harddrive partition????

All the dual boot questions I could find in this forum and with google only addressed dual boot installs as windows/ubuntu......but nothing I could find addresses ubuntu/ubuntu dual boot.

TY.

Art

---

### Post by offgridguy on 2013-01-15
> **goodbye-windows(tm) said:**
> How do I install Xubuntu in one harddrive partition and another xubuntu in another harddrive partition????

All the dual boot questions I could find in this forum and with google only addressed dual boot installs as windows/ubuntu......but nothing I could find addresses ubuntu/ubuntu dual boot.

TY.

Art
There is info in this thread.

[http://ubuntuforums.org/showthread.php?t=2075214](http://ubuntuforums.org/showthread.php?t=2075214)

This regards triple boot, same principles apply, i currently have a quad boot on
one laptop.  It is very easy to install one linux OS beside another, and very
easy to remove one if you want to change.

Do you already have xubuntu installed, and why would you want another
xubuntu?
Also it helps to attach a screenshot of your partition table, when asking questions about partitioning. :D

edit; Currently i have ubuntu 12.04, kubuntu, xubuntu and Sabayon 10, installed
alongside each other.  The "buntu" versions allow me to try the default DE, along with
the default software and dependencies that come with each one.

---

### Post by goodbye-windows(tm) on 2013-01-16
> **offgridguy said:**
> 

Do you already have xubuntu installed, and why would you want another
xubuntu?

I actually want 3 independent versions of Xubuntu installed.

One will be my everyday xubuntu (12.10), the one I'm running now.

The second will be an old 10.04 Xubuntu because it will run my garmin gps-newer versions won't.

The third will be an experimental Xubuntu 12.10. I do not (and will not) use facebook due to it's violation of privacy.  I need to set up a separate Xubuntu so I can stay 'anonymous' and not give up personal info to facebook.

I do have an interest in running unity, but haven't tried the new version yet. Previous versions were not very customizable, so might want to see if improvements have been made in the latest unity. So, I might actually want 4 separate installs.

Regards,

Art



5

---

### Post by Elfy on 2013-01-16
If you have sufficient RAM then maybe using virtual machines for the odd ones might work, I do that here - have one for testing, one for running the test forum etc

However if you want to use real partitions, set them up for each OS you want, I'd not bother with seperate homes for the extra's (I don't use seperate /home for any personally) so you would just need one partition for each. 

Existing swap will be recognised and used.

When you are installing - use the Something Else option to specify the partition to install to AND also install grub to that partition for the 'extra's' - keep the everyday install having the grub that the system boots from - so for instance of the 10.04 is on sda6, install grub to sda6, but your everyday install would have grub at sda. 

Once you've got them all installed - you can update grub from the main install and it will pick up the other ones.

---

### Post by goodbye-windows(tm) on 2013-01-21
I did the partitioning and installed another version of Ubuntu into that partition. There were no errors.

I did a:

```
sudo update-grub
```from my everyday Xubuntu.

The the terminal indicated it had found my new install in sda3, so I thought I was home free::>

However, when I rebooted, there was no way to choose the sda3 partition, so I can't log into it.

I can only log into my everyday install on sda1.

I have attached a screenshot of the harddrive (which is actually a small SSD). 

Do I need to do other things before grub will recognize both buntu's and allow me to choose which one I want to log into????

Thanks,

Art

---

