---
title: "Tricky Installation Trouble"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by James_Cracknell on 2013-09-27
Hi all, I have always heard good things about Ubuntu and so decided to  try it out. I got it to work (sort of) and I really liked it and now I'm  stuck without it trying to re-install it.
My problem is fairly long winded and complex so here goes:

1. I first started downloading Ubuntu 13.04 at 5pm (GMT +/-0) yesterday,  waited for it to download (I am stuck with a mobile broadband  connection and it's slow, like 0.1 MB/s slow...) after about an hr it  had finished and I burnt the downloaded ISO to a DVD using Nero. All was  well and good

2. I inserted the DVD back into the DVD drive after Nero spat it out and  rebooted, went into the boot menu (which happens to be F12 on this  machine) and chose the DVD drive (D:\) Ubuntu started to load and I felt  an over-whelming sensation of happiness (could this be the end of my  long and painful win-doze days)

3. I followed the on-screen instructions and the DVD happily 'whirred' away in the drive as it installed

4. System rebooted and all was well and good until I tried to download  and install wine. I couldn't get it to work (after hours) I kept getting  error messages despite following the terminal instructions posted at [www.winehq.com]("http://www.winehq.com").  I also seemed to have some sort of boot error that would only let me  boot into Ubuntu if the DVD with the ISO on it was in the DVD drive -  details of that are here: [http://paste.ubuntu.com/6161312/](http://paste.ubuntu.com/6161312/) 

5. Stupidly I thought 'I know what I'll do! I will re-install Ubuntu  with a fresh copy and start over thinking I had messed up the system  somehow with so many failed install attempts. This is when I started to  run into bigger problems. Ubuntu refused to install again and I was  stuck with a corrupted mbr. I booted the Ubuntu DVD into 'try it' mode  and found a set of mbr repair terminal command line commands. did them,  and it worked, my computer rebooted and windows started to load. 

6. I thought I would have another attempt at installing Ubuntu so I  popped the Ubuntu DVD back into the DVD drive and restarted my system.  This time I got to the 3 choices menu; 1. Install INSIDE windows 7 (I'm  sure it said alongside the first time around) 2. Replace Windows 7 3.  Something else and I chose the first option despite thinking 'hmmm  something's not right'; I wasn't ready to wipe all my Windows files and I  did try the 3rd option but it wouldn't let me change anything, so I  chose the 1st option again and almost straight away the system spat out  the DVD, Ubuntu told me to remove the DVD, close the tray and hit enter.  So I did.

7. The next thing I know I get a screen that shows the following :

Completing the Ubuntu installation.
For more installation boot options press 'ESC' now...
0

Busy Box v.1.20.2 (Ubuntu 1:1.20.0-8ubuntu1) built-in shell (ash)

(initramfs) unable to find a medium containing a live file system

(initramfs) _ //Flashing underscore (I have dabbled with C++ years ago so that double forwards slash is a note marker)

8. so basically I was stuck with a prompt that says (initramfs) followed by a flashing underscore

9. whenever i reboot my machine I get the option to install Ubuntu and  if I choose that, option steps 5 through 7 happen again. I have tried  inserting the DVD after pressing ESC when it says and it loads right  back to step 6

10. I have tried downloading a fresh copy of the previous version on the  ubuntu website and using that. (I would prefer to have the  12.(something) version anyway because I intend to use ubuntu long-term.  (and yes my system is 64 bit and yes I downloaded the 64 bit version  BOTH times - I made very sure of this)

11. I'm sure there are no Linux partitions on my HDD because I have been  into computer management to check disk usage and there are 4 partitions  on there all of which are windows or windows related (1 recovery 2 main  partition 3 main partition and 4 sytem reserved)

12. Now I'm totally stuck after 19 hours almost non stop attempting to  get this thing to work, but I'm not one to give up so easily as I have  seen it sort of work I know it has the potential to work and to quote  Nickleback 'What's worth the prize is always worth the fight' :smile:

please help me!

- A confused yet determined Ubuntu newbie !

---

### Post by oldfred on 2013-09-27
The install inside Windows is wubi which is just a file in the NTFS partition. Fine for a longer test then just running DVD or flash drive version. But wubi now does not work with gpt partitioned drives which all new UEFI systems have. Wubi is being discontinued.
       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

If you have Ubuntu installed in separate partition and want to over install, you have to either delete partition(s) so you have unallocated space or just use Something Else or manual install and choose your existing / (root) as the new /. If you had a separate /home you would choose it also but DO NOT format it. And it would auto find an existing swap.

If you never had a Linux partition then you must have had wubi. And if all 4 primary partitions are used then you have to delete one to make the extended partition for an unlimited number of logical partitions. Windows only boots from primary partitions, but Linux works in logical partitions just fine. Do not ever create new partitions with Windows, it cannot create Linux formatted partitions and may convert to dynamic from basic and that does not work with Linux or even some Windows tools.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by James_Cracknell on 2013-09-27
Hi again, wubi did the trick as I'm on win 7 all it was was a faulty or partial install of ubuntu which wubi fixed (choose to download windows INSTALLER from Ubuntu website then run it (wubi) and it will uninstall anything there before you need to run it again to install Ubuntu) <--- posting for other newbies to read :) THANK YOU :D

---

