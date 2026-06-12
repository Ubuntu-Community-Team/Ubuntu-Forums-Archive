---
title: "Upgrade failure 9.10-10.4"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Garnett on 2010-05-05
While upgrading (why did I do it?! 9.10 was working fine!) I got an lengthly error and now the computer won't boot.

Error and then boot screen:-

```
Could not install the upgrades

The upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg received a segmentation fault., E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2), E:Sub-process /usr/bin/dpkg returned an error code (2)

```

[IMG]http://i164.photobucket.com/albums/u32/garnettf/05052010056.jpg[/IMG]

Any recovery might prove hard since I have no CD burner but the one in that machine so I have no way of making a 10.4 liveCD.

Got a few other LiveCDs - a Mint Gloria, and some old Ubuntus...

Thanks for any help.

---

### Post by Garnett on 2010-05-05
Anyone got any suggestions? My system's unusable at the moment.

I've found that other people have got similar symptoms:

> **Neo2 said:**
> mine gets as far as 'checking battery  OK' before hanging. But fails to get out of 'DOS' mode!(posted mainly to help me log every possible avenue for a solution)

I've attached a picture of the error message I get before the screenshot above.

Message typed out (for google searches):

Mount: mounting none on /dev failed: No such device61c12c5d15
Starting up …

---

### Post by Garnett on 2010-05-05
Think I may have found a possible solution:

[Upgrade from 9.10 to 10.04 Failed - Help if Able !]("http://ubuntuforums.org/showthread.php?t=1468156")

Didn't ever get to click an option "Forward" Button to keep current Boot/Grub/Menu.lst file. The upgrade never got that far. So I'm dubious whether this will solve the problem.

---

### Post by Garnett on 2010-05-05
Can't follow the terminal instructions from the thread linked above.

Can anyone imagine the slating Microsoft would get if the next Windows was launched like this?

System's completely unusable as a result of clicking "Upgrade" when Update Manager did its automatic check. #-o

---

### Post by frantid on 2010-05-05
do you have a flash drive?  You could boot off a flash drive.  Use your other livecd to download lucid.

---

### Post by uRock on 2010-05-05
I hear Windows 7 still has killer upgrade issues. That said. You can try the option mentioned above using a LiveCD and a flash drive or take the 30 minutes to install an older version and use it to make a LiveCD for Lucid, so that you could test it before installing.
My way is assuming that you used a separate /home partition when you last installed. If not, now is a great time to do so. If you want help reinstalling and creating a new partition to use for installing and turning the old one, once shrunk a bit, into the /home so that you don't loose your data, then let me know.

---

### Post by Garnett on 2010-05-06
> **uRock said:**
> My way is assuming that you used a separate /home partition when you last installed. If not, now is a great time to do so. If you want help reinstalling and creating a new partition to use for installing and turning the old one, once shrunk a bit, into the /home so that you don't lose your data, then let me know.Gah! No separate /home partition! Looked into it but it seemed fairly complex for an Ubuntu amateur.

Even just a list of general steps would be great. I can google the details.

The machine has two HDDs installed so if I could get a LiveCD to allow me to makechanges to them I could move the /home directory over and start again (ie, do what you said: install an old version of Ubuntu or Mint and then download and burn a Lucid LiveCD and go from there).

---

### Post by uRock on 2010-05-06
> **Garnett said:**
> Gah! No separate /home partition! Looked into it but it seemed fairly complex for an Ubuntu amateur.

Even just a list of general steps would be great. I can google the details.

The machine has two HDDs installed so if I could get a LiveCD to allow me to makechanges to them I could move the /home directory over and start again (ie, do what you said: install an old version of Ubuntu or Mint and then download and burn a Lucid LiveCD and go from there).
That'll be the easiest way, if your system will let you move the files to the other drive.

To set up a separate /home partition, you just select the "select Partitions Manually" selection in the partitioning menu, then create the swap, a 5-10GB / partition which will contain the OS, then use the rest of the drive for your /home partition.

---

### Post by dino99 on 2010-05-06
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by Derek.Gildea on 2010-05-06
I have precisely this issue. Other people seem to do ok making a LiveCD - I run into trouble there. BOOTMGR is missing. Any ideas?

---

### Post by Garnett on 2010-05-07
Currently using Mint Gloria LiveCD to repartition my HDD and transfer my /home folder over to the new partition.

Given the relative frequency with which I seem to have to reinstall Ubuntu, will a separate /home partition allow me to retain all my extra programs and settings from one installation to another?

Getting tired of running through the (excellent, but) lengthly media setting howto and then setting up all my compiz and dock settings each time.

---

### Post by dino99 on 2010-05-07
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by Garnett on 2010-05-09
Thanks for all the help. In the end I used a Mint Gloria LiveCD to repartition my HDD, then move my /home directory to the new partition and then install Ubuntu 8.10 (the newest Ubuntu LiveCD I could find).

Then I downloaded 9.10 and 10.04 LiveCDs, checked for errors, and installed them one after the other.

They both worked and 10.04 was working well.

This all took a couple of days.

I then spent another couple of hours tweaking it back to how I had 9.10 set up. The last thing I did was to download and install the newest Nvidia drivers and restart.
[URL="http://ubuntuforums.org/showthread.php?t=1476426"]
Now I've got a new fundamental error[/URL].

Ubuntu use is proving a bit of a rollercoaster at the moment.

---

### Post by MorganJarl on 2010-05-09
I have a very similar problem. I don't mind going back to 9.10 but I need to copy the info from my home folder first (or can I just reinstall from the live CD without losing my files?).

Problem is that my home folder is locked, I can't get to it. What to do?

To explain a bit more: I am running a Ubuntu 9.10 live cd and can get to the file system, but I can't read the home folder, nor my root folder.

Updated

---

### Post by hafeedap on 2010-05-09
Well I will try to analyse.

---

