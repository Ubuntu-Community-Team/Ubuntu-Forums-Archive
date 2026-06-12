---
title: "Lubuntu New Install Root / Is Already Full, Cannot Update"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by FaultedGeologist on 2016-02-12
I resolved a slew of issues relating to partitioning, and settled on a 5GB swap, 30GB root /, and the rest of a 200GB as /home.  I ran the System Tools > Software Updater, and it tells me there is not enough room to download the files.  

1) Under Accessories > Disks it indicates I do have enough space, but barely.  

2) Why would a fresh OS have nearly no space?  

As recommended in the Updater, I ran the cleanup code in Terminal, but it did not allow the updater.  I rebooted.  Same.    See images below.  TIA4daHELP!

Grumble, Grumble...

[ATTACH=CONFIG]267257[/ATTACH][ATTACH=CONFIG]267258[/ATTACH]

---

### Post by Bucky Ball on 2016-02-13
Have absolutely no idea what is going on there. How did you install? Just a regular Lubuntu ISO and chose 'Something Else'? You do not mention the release you went for. Please always include this bit of info. :) If you're running 16.04 LTS, be aware that it is not released, unexpected things may happen, and support threads for it don't belong anywhere but in the ***Ubuntu Development Version*** area. 

I'd open a file manager and see if I could find what's hogging all the space. Right click and 'Properties' through the folders in there. Find any folders inside / that are 20Gb or something absurd? You can also run:

> sudo apt-get autoremove

... and see if that shows anything it wants to get rid of, and also see if there's anything in trash, unlikely on a new install, and empty that if so.

So, try these things and see if they throw up more clues, let us know how you installed and which release please. ;)

---

### Post by FaultedGeologist on 2016-02-13
kernel: 3.19.0-15-generic
OS:
Name="Ubuntu"
Version="15.04 (Vivid Vervet)"

This shouldn't be.  Remember from my previous threads that I had Ubuntu installed on this HD.  After having tons of trouble doing the re-partitioning and Lubuntu install, I finally used Disks to write zeros over the first two partitions (25GB) of the HD (swap and / partitions_).  

When installing, I checked the [ ] Update while installing? since I was connected to the interwebs.

I ran the sudo apt-get autoremove last night before the restart, and still the same result.  Today it resopnded:
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.

The GUI is def not Ubuntu, it is the LXDE 2-D in oldskool Windows 98-esque style.

Below is a screen print of the Root Directory Tree sorted by file size.  Notice the bottom right, Free space: 0 bytes (Total 27.6GiB)

[ATTACH=CONFIG]267281[/ATTACH]

---

### Post by ubfan1 on 2016-02-14
Try running fsck on the filesystem.  Then look in the lost+found directory for anything.  Even if files from both distributions are present, that should be only around 5G, so either you have a badly damaged filesystem or a lot/big file(s) somewhere.  See what du -s -D /* produces to see the sizes of the top level directories and see which one is waay too big.

---

### Post by FaultedGeologist on 2016-02-14
> **ubfan1 said:**
> Try running fsck on the filesystem.  Then look in  the lost+found directory for anything.  Even if files from both  distributions are present, that should be only around 5G, so either you  have a badly damaged filesystem or a lot/big file(s) somewhere.

Just to make sure you see this part, there are 20 bad sectors on the drive per Disks.  See the image above.  Could this be the cause?  In the link below, there is an incomplete **Bad Blocks** header that has no information.

Per the search for fsck ubuntu, I read through this page:
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

It says to place this in the root of the file system:
```
**touch /forcefsck**
```

Options 1 and 2 of the Cheat Sheet seem like the right thing, but I am unsure how to trigger this. 
```
**fsck.ext4 -p /dev/sda1**
```

> **ubfan1 said:**
>  See what du -s -D /* produces to see the sizes of the top level directories and see which one is waay too big.

From a fresh reboot:
```
12720    /bin
39420    /boot
4    /cdrom
0    /dev
du: cannot read directory ‘/etc/polkit-1/localauthority’: Permission denied
du: cannot read directory ‘/etc/ssl/private’: Permission denied
8012    /etc
du: cannot read directory ‘/home/lost+found’: Permission denied
110284    /home
332588    /lib
4    /lib64
du: cannot read directory ‘/lost+found’: Permission denied
16    /lost+found
8    /media
4    /mnt
4    /opt
#APPROXIMATELY 1,350 /proc PERMISSION DENIED lines,
12720    /bin
39420    /boot
4    /cdrom
0    /dev
du: cannot read directory ‘/etc/polkit-1/localauthority’: Permission denied
du: cannot read directory ‘/etc/ssl/private’: Permission denied
8012    /etc
du: cannot read directory ‘/home/lost+found’: Permission denied
110284    /home
332588    /lib
4    /lib64
du: cannot read directory ‘/lost+found’: Permission denied
16    /lost+found
8    /media
4    /mnt
4    /opt

```

---

### Post by QIII on 2016-02-14
Could you also post the results of 

```
df -h
```

and

```
df -i
```

---

### Post by FaultedGeologist on 2016-02-14
For some reason it shows 9.4GB of space today.  I ran the Software Updater, it downloaded 200MB of data, ate 400MB of disk space, and completed.  What I am wondering is why so much updating needed to be done when I just installed it as Lubuntu a couple days ago and clicked the [ ] Download Updates While Installing option.  Did I just update to Ububntu, but kept the LXDE GUI?  Restarting the computer to complete the updates...

[ATTACH=CONFIG]267301[/ATTACH]

---

### Post by QIII on 2016-02-14
Clicking download updates never seems to be completely effective, nor do I think it is intended to be.

I always update immediately after installing from an image that is more than a few days old.

*Any* bad sectors can be a huge problem.

Hence, it would be good to look at df -i as a quick look at your inode structure.  Anything obvious there may take more investigation.

---

### Post by ubfan1 on 2016-02-14
Look in /lost+found with sudo ls -l /lost+found   If the directory size is really 16, there may be many files there, and it should be empty.

---

### Post by FaultedGeologist on 2016-02-14
OK, so the whole OS on the 'faulted' drive got botched from the attempted System Upgrader.  It went to a black screen on reboot, then to Grub on hard kill.

I am now on the 'oli' drive.  It shows the same kind of consumption of HD space.  This HD is not partitioned yet, I just let it do the full process unimpeded due to my issues with the other drive and the partitioning scheme.

The 'oli' disk shows OK in the assessment, so no bad sectors here.  I may do a live usb boot to see if I can pop some partitions out for swap and /home so I can run how I prefer things to be.  Just for crap and laughs... here is this drive.  See the /dev/sda1 entry. Size:  183G (200GB drive), Used 24G.  Avail: 150G

Why is 24GB used on a simple install?  With 20 bad sectors on the other HD, I figure it can go to the metal scrap pile.  This one shows the same bloated OS install.

> **QIII said:**
> Could you also post the results of 

```
df -h
```
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           396M   41M  355M  11% /run
/dev/sda1       183G   24G  150G  14% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           396M   12K  396M   1% /run/user/1000

```



> **QIII said:**
> and ```
df -i
```
```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             494813    517   494296    1% /dev
tmpfs            505838    625   505213    1% /run
/dev/sda1      12148736 124053 12024683    2% /
tmpfs            505838      1   505837    1% /dev/shm
tmpfs            505838      6   505832    1% /run/lock
tmpfs            505838     15   505823    1% /sys/fs/cgroup
tmpfs            505838      6   505832    1% /run/user/1000
```


P.S. On a side note, I thought I was on to something with the Vivid Vervet thing, but that is simply the current 15.04 Lubuntu flavor.  I thought it was doing something with upgrading to Ubuntu.

So what now?  Agree with scrapping the 'faulted' drive?

> **ubfan1 said:**
> Look in /lost+found with sudo ls -l /lost+found   If the directory size is really 16, there may be many files there, and it should be empty.

On this 'oli' HD, the unpartitioned one that is still working, it shows ```
total 0
```.

Still the same bloated 24GB install on the root.

---

### Post by ubfan1 on 2016-02-14
Some important directories were not in the previous du report (cut and paste error).  Try again dumping all the errors for a concise report:
du -s /* 2>/dev/null
If /var is out of site, then maybe look in /var/log for a log file getting out of hand.
The normal install should be 4-5G or so.  24-28G is really wrong.  I suppose a 20G swap file is a possibility, but I didn't think the installer can set one up, it uses partitions.

---

### Post by FaultedGeologist on 2016-02-14
> **ubfan1 said:**
> Some important directories were not in the previous du report (cut and paste error).  Try again dumping all the errors for a concise report:
du -s /* 2>/dev/null
If /var is out of site, then maybe look in /var/log for a log file getting out of hand.
The normal install should be 4-5G or so.  24-28G is really wrong.  I suppose a 20G swap file is a possibility, but I didn't think the installer can set one up, it uses partitions.

That is a pretty big /var file listed below.  Keep in mind we are on the no partitions 'oli' HD, but both HDs had nearly all 30GB used.  

**Q:  Should I be discarding the 'faulted' HD with the 20 bad sectors?**

```
12724    /bin
39412    /boot
4    /cdrom
0    /dev
7912    /etc
64004    /home
0    /initrd.img
339348    /lib
4    /lib64
16    /lost+found
8    /media
4    /mnt
4    /opt
0    /proc
4    /root
41520    /run
9156    /sbin
4    /srv
0    /sys
36    /tmp
1546920    /usr
25488324    /var
0    /vmlinuz

```

**How do I deal with the 25GB /var and what is the 1.5GB /usr for?**

---

### Post by FaultedGeologist on 2016-02-15
Per another thread found by searching keywords from this thread, I found and ran this to view files greater than 1GB:

```
sudo find / -name '*' -size +1G
```

It came back with my /var/log/syslog and /var/log/syslog.1 files.  Below is a pic of the offender in the file tree. 

**In the other thread, it said that merely deleting the file will not solve the problem.  **What should I be doing to solve it?

In other news, the Software & Updates popped up with a prompt to install updates...  per my other issues, I am a little weary.  Thoughts?

[ATTACH=CONFIG]267313[/ATTACH]

---

### Post by Bucky Ball on 2016-02-15
Helps if you link to the thread you got the info from.

I would be deleting both those syslog files, empty your trash, reboot.

---

### Post by FaultedGeologist on 2016-02-15
I may have found the answer in this thread (tons of other links to helpful threads) on askubuntu:
[http://askubuntu.com/questions/515146/very-large-log-files-what-should-i-do](http://askubuntu.com/questions/515146/very-large-log-files-what-should-i-do)

From that, I ran this in terminal:

```
tail -n 100 /var/log/syslog
```

A bunch of WPA supplicant errors!
My 2005ish WiFi card D-Link DWL-520 is causing problems.  I understand this particular version of the card is not supported and is likely never going to work well.  Heere are terminal codes to find wi-fi models and firmware:

```
lspci -v
```

Subsystem: D-Link System Inc DWL-520 Wireless PCI Adapter (rev E1) [ISL3872]
This rev E1 is 

```
sudo lshw -C network
```

description: Wireless interface
       product: ISL3874 [Prism 2.5]/ISL3872 [Prism 3]
       vendor: Intersil Corporation

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
Shows no working action.

**Now can I delete the log file and remove the card? ** I wanna mark SOLVED!!!

---

### Post by FaultedGeologist on 2016-02-15
> **Bucky Ball said:**
> Helps if you link to the thread you got the info from.

I would be deleting both those syslog files, empty your trash, reboot.

Sorry, I cannot find that link now for some reason.  The code was about all there was to mention in the thread.  Will link all in future.  

As for deleting the syslog file, it says access denied.  I am a little uncomfortable with sudo commands, and I am not sure the terminal codes I am finding are what I want to do.  This thread has some interesting suggestions, but they go back and forth on what to do:

[http://askubuntu.com/questions/414632/log-files-are-taking-too-much-space-and-i-cant-delete-clear-them](http://askubuntu.com/questions/414632/log-files-are-taking-too-much-space-and-i-cant-delete-clear-them)

This is the only other good thread I could find, and it has more back and forth, with just wanting to access the file:

[http://ubuntuforums.org/showthread.php?t=1697993](http://ubuntuforums.org/showthread.php?t=1697993)

Can you provide a safe terminal code to delete that file?  Other suggestions are to zip it, change the rotation of the logs, length of keeping the logs, etc.  I could put the keep range low, wait for it to terminate itself, then restore the keep length if deleting is not best.

---

### Post by FaultedGeologist on 2016-02-15
I think I found the answer in this thread after combing about 5 others:

[http://askubuntu.com/questions/436051/i-cannot-clear-syslog-but-i-can-remove-it](http://askubuntu.com/questions/436051/i-cannot-clear-syslog-but-i-can-remove-it)

```
> /var/log/syslog
```

My system is actively doing a Gzip of the syslog right now as I type.  I think it is done... posting a new pic of the file tree.  I would like to delete the Gzip files since the OS is only a few days old and this wifi card issue seems to be the only error.

I took the wifi card out and rebooted.  The new syslog file is small, 275 bytes.  syslog.1 is 36.2GB then I have syslog.2.gz and syslog.3.gz that need to go.  

I tried this in terminal:

```
> /var/log/syslog.1
```

```
sudo > /var/log/syslog.1
```
Both the above codes returned this:  bash: /var/log/syslog.1: Permission denied


[ATTACH=CONFIG]267317[/ATTACH]

Edit:
Reading this thread, it says not to use sudo on GUI apps.  Help a confused N00buntu user out!  It's all so confusing!
[http://ubuntuforums.org/showthread.php?t=1697993](http://ubuntuforums.org/showthread.php?t=1697993)


In this thread, the code below looks like it removes any file (*) with the .1 appendage in the whole log folder,
[http://askubuntu.com/questions/414632/log-files-are-taking-too-much-space-and-i-cant-delete-clear-them](http://askubuntu.com/questions/414632/log-files-are-taking-too-much-space-and-i-cant-delete-clear-them)
```
sudo rm /var/log/*.1
```
but there are lots of other files, such as kern.log.1 and auth.log.1 so I would need to change the code to
```
sudo rm /var/log/syslog.1
```

**Can I get advice on the included link stating not to use sudo commands in gui and what that means?  Should I use the last piece of code I created above?  **I am starting to see through the matrix... blonde, brunette...  I took the blue pill!
[URL="http://ubuntuforums.org/showthread.php?t=1697993"]
[/URL]

---

### Post by sudodus on 2016-02-15
Try ```
sudo rm /var/log/syslog.1
``` to remove the file

---

### Post by FaultedGeologist on 2016-02-15
SuhhhweEEt!  I removed syslog.1 and the syslog.2.gz and syslog.3.gz using above code.  Now to clean up, run the update that was prompted, and wish upon a star.

---

### Post by sudodus on 2016-02-15
Congratulations,

Thanks for sharing your result and for marking the thread as SOLVED :KS

---

