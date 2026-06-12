---
title: "Ubuntu 12.04/Windows 7 dual boot. Black screen."
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by pranavbaitule on 2013-04-03
Hi. Yesterday I installed Ubuntu 12.04 on my notebook which had a pre-installed Windows 7 OS(64-bit).
My system config is - 320 GB HDD, 3 GB RAM, 1 GB ATI Mobility Radeon HD 4560
My notebook came with 4 existing primary partitions -
1)282 GB - OS and data.
2)16 GB - HP Recovery
3)100 MB - System
4)2 GB - HP Tools

So to install Ubuntu, I shrank the 282 GB to a 100 GB partition, deleted the HP Recovery and HP Tools, created a new NTFS 175 GB primary partition and another 22 GB extended partition on which I installed Ubuntu and I didn't touch the System partition.

After installation I rebooted my notebook and came to this screen -
[[IMG]http://lookpic.com/O/t2/184/ARkT4a3E.jpeg[/IMG]]("http://lookpic.com/O/i2/184/ARkT4a3E.jpeg")

By selecting the first option I successfully booted up into Ubuntu without any problems. Then I rebooted and selected the 'Windows 7(loader)' option to start Windows and after the Windows logo appeared, all I got was a black screen. After a few minutes the system automatically shut itself down due to over heating.

Again rebooting I now selected the 'Windows Recovery Environment' option and I got to this screen - 
[[IMG]http://lookpic.com/O/t2/428/o04soMUS.jpeg[/IMG]]("http://lookpic.com/O/i2/428/o04soMUS.jpeg")

Pressed Enter and I saw this screen -
[[IMG]http://lookpic.com/O/t2/775/c8HKKvUf.jpeg[/IMG]]("http://lookpic.com/O/i2/775/c8HKKvUf.jpeg")

Again pressed Enter, nothing happened. So I chose the 'Windows Memory Diagnostic' tool and ran it. During the tests my system again shut itself down due to overheating. My notebook did not come with a Windows 7 DVD but I created 4 recovery discs and a system repair disc. So I booted up using my system repair disc to try and repair the files but I got a BSOD saying "Fatal System Error. The system has been shut down."

I try pressing the F8 button to get additional boot options and boot into safe mode but I don't get any. I also installed and ran the boot-repair utility on Ubuntu but it didn't change anything I still get that black screen. I have my personal data backed up but I don't have a back up of the system image of Windows 7 and I have lots of software installed on that OS. Is there anyway to keep my software and get this damned OS to work again? The fan of my notebook is not blocked. Still I have this overheating problem. Even now when I am in Ubuntu, the fan is going crazy. Please help.

---

### Post by Mark Phelps on 2013-04-03
How did you SHRINK the Win7 OS partition -- the right way, using Windows filesystem utilities? Or, the wrong way, using Linux filesystem utilities?  If you did the second, that most likely corrupted the Win7 OS.

Did you bother to make a Win7 Repair CD while it was still working?  Since probably not, then you will have to PURCHASE an image to do that.  IF you're willing to spend money to get Win7 back working, then go to the site below, purchase the image, download and burn the CD, and run Startup Repair three times -- that's right, three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by pranavbaitule on 2013-04-03
> **Mark Phelps said:**
> How did you SHRINK the Win7 OS partition -- the right way, using Windows filesystem utilities? Or, the wrong way, using Linux filesystem utilities?  If you did the second, that most likely corrupted the Win7 OS.

Did you bother to make a Win7 Repair CD while it was still working?  Since probably not, then you will have to PURCHASE an image to do that.  IF you're willing to spend money to get Win7 back working, then go to the site below, purchase the image, download and burn the CD, and run Startup Repair three times -- that's right, three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)


I decreased the Windows 7 OS partition size using GParted utility during the LiveCD session and yes, I did make a Windows 7 repair CD while it was properly working, before partitioning.

---

### Post by pranavbaitule on 2013-04-03
Solved!
It was a bit carelessness from me. I hadn't mark the Windows 7 partition as active. Hence it was unable to boot from Windows. So I did that using GParted, booted using my system repair disc, let it do its job and it magically started in Windows!

Anyway, thank you Mark Phelps for replying.

---

