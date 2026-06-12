---
title: "Is it possible to install Lubuntu on a USB hard disk without data loss?"
date: 2018-03-13
forum: Installation &amp; Upgrades
---

### Post by matthew-wai on 2018-03-13
[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) I have created a bootable SD card with Lubuntu 17.10.1 Desktop 64-bit.
I have an HP Pavilion v7078hk motherboard with an Intel Core2 CPU 4300 and 3GB of RAM.
I have a USB hard disk with two partitions. The first one contains backups.
Is it possible to install Lubuntu on the second partition without data loss on the first one?
I just tried but failed to install it. See the screenshots below.
dev/sda1 was the partition containing backups, and I wanted to install Lubuntu on dev/sda2.
An error arose and the installation could not be finished. It stuck at "Detecting file systems".
At the moment, dev/sda2 is still in NTFS. Does it mean Lubuntu failed to format it?

---

### Post by T.J. on 2018-03-13
Yes, it is possible, but you should be warned in advance that regardless of what OS you try to install - Windows, Linux, and so on (doesn't matter) that installing it on a drive used for backups is a very bad idea.  You run the risk of corrupting your entire backup, either due to human error or a software flaw.

That said, if you chose to press on, it can be done, but it would have to be done manually to make certain you do not damage your backup partition.  Booting it will depend on your specific hardware.

---

### Post by yancek on 2018-03-13
If you made the selections showing in the first image, selecting sda2 and clicking the check box to format, it should format and install.  If it fails, you might try formatting using GParted before trying the install.  Not sure if GParted is on the Lubuntu install disk although it is on most other UBuntus.  Is the machine you are going to be using the install on a Legacy/mbr machine?  Make sure you install grub to the mbr, which is what is showing in the image.  Make sure you check the device name (/dev/sda, /dev/sdb, etc.) as that can change.

I would agree that it is not a good idea to be modifying partitions and installing an OS on a drive used for backups, too much can go wrong.  No reason what you want cannot be done if everything works right.

---

### Post by mastablasta on 2018-03-14
you need enough disk space at the start of the drive to acomodate the GRUB.

You can do what you want to do. I suggest manual formatting. and you need to be sure the disk doesn't have osme strange formatting type done (e.g. some weird preformated thing).

---

### Post by sudodus on 2018-03-14
@matthew-wai,

***The answer is yes*** to your question in the title: 'Is it possible to install Lubuntu on a USB hard disk without data loss?'

But I agree with the other people who warn about installing an operating system on a drive, where you have your backup, because things can go wrong.

Instead I suggest that you get another external drive and install Lubuntu into that drive. A fast SSD in an external box (USB3) is a good alternative. I am running a few such systems. You can install them according to the following link and links from it,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

[hr][/hr]
@yancek,

GParted *is* on the Lubuntu *desktop* install disk, and you can use it, if you 'Try Lubuntu'. But you cannot use it with the Lubuntu *alternate* installer.

---

### Post by matthew-wai on 2018-03-14
[COLOR=#333333][FONT=&amp]I unmounted all partitions, and then I could install Lubuntu successfully. However, I could not set up a PPPoE connection. See below:

[/FONT][/COLOR]**[COLOR=#ff0000]matthew@matthew-pc:~$ pppoeconf[/COLOR]**
**[COLOR=#ff0000]The program 'pppoeconf' is currently not installed. You can install it by typing:[/COLOR]**
**[COLOR=#ff0000]sudo apt install pppoeconf[/COLOR]**
**[COLOR=#ff0000]matthew@matthew-pc:~$ sudo apt install pppoeconf[/COLOR]**
**[COLOR=#ff0000][sudo] password for matthew: [/COLOR]**
**[COLOR=#ff0000]Reading package lists... Done[/COLOR]**
**[COLOR=#ff0000]Building dependency tree       [/COLOR]**
**[COLOR=#ff0000]Reading state information... Done[/COLOR]**
**[COLOR=#ff0000]E: Unable to locate package pppoeconf[/COLOR]**

So I gave up and went to install Mint instead. I am now running Mint on the USB hard disk. 
I have successfully set up a PPPoE connection via [COLOR=#ff0000]**pppoeconf**[/COLOR] on Mint.

---

### Post by ubfan1 on 2018-03-14
@sudodus,
Last time I tried an SSD in a USB3 box, I couldn't TRIM the drive.  I can TRIM an SSD in a box which connects via eSATA.  Are your SSD self-TRIMing or do you periodically remove the drive, put it into a SATA slot and TRIM it?

---

### Post by sudodus on 2018-03-14
@ubfan1,

I have both self-trimming external drives, and SSD drives in USB3 boxes, that cannot be trimmed via USB. I do have an USB & eSATA box (and such a plug-in adapter), so I can trim it that way, when connected to a computer with an eSATA connector.

@everybody,

There is also a problem with new SSDs with 4096 bytes physical sector size and some adapters/boxes. See the following link,

[USB boxes/adapters for SATA drives with 4096 B physical sectors](https://ubuntuforums.org/showthread.php?t=2386278)

---

### Post by matthew-wai on 2018-03-15
Why is "pppoeconf" absent from Lubuntu as it is essential for a PPPoE connection?
Does that mean a user has to download "pppoeconf" via a different operating system that has an Internet connection?

---

### Post by sudodus on 2018-03-15
I have checked and **pppoeconf** is in the repository **main** in 16.04 LTS as well as in 17.10.1, so it should be available in both versions of Lubuntu.

You can check with

```

apt-cache policy pppoeconf

```
and install with
```

sudo apt update
sudo apt install pppoeconf

```

if you system is installed and set up correctly.

---

### Post by matthew-wai on 2018-03-15
> **T.J. said:**
>  make certain you do not damage your backup partition. Booting it will depend on your specific hardware.
Fortunately, the backup partition remains safe and sound, and the USB hard disk is bootable.

---

### Post by matthew-wai on 2018-03-15
> **sudodus said:**
> I have checked and **pppoeconf** is in the repository **main** in 16.04 LTS as well as in 17.10.1
My version was Lubuntu 17.10.1 Desktop 64-bit. 
Was it normal to get the messages (in red) in my post #6 above? 
Was my system installed and set up correctly?

---

### Post by sudodus on 2018-03-15
I tested in an installed Ubuntu 17.10.1 Desktop 64-bit and an installed Lubuntu 16.04 LTS and

```
apt-cache policy pppoeconf
```

showed the same result, that pppoeconf is available via the repository main, which is there in standard Ubuntu and all Ubuntu community flavours (including Lubuntu).

I would say that your message is not normal (I do not get it). I don't know how you installed your system, so I don't know if it was installed and set up correctly, but I suspect that some setting is wrong. Maybe it helps to run

```
sudo apt update
sudo apt full-upgrade
```

Check that these commands finish without errors, and then try again to install pppoeconf

```
sudo apt install pppoeconf
```

**Edit:**

What is the output, when you run

```
apt-cache policy pppoeconf
```

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by matthew-wai on 2018-03-16
I have already subscribed to this thread, but I have still received no notification of your reply. I wonder why.

---

### Post by sudodus on 2018-03-16
You can specify email notification separately. Did you do that?

---

### Post by matthew-wai on 2018-03-16
I just found that I have to select "Instantly, using email".

---

### Post by matthew-wai on 2018-03-16
> **sudodus said:**
> I would say that your message is not normal (I do not get it). I don't know how you installed your system, so I don't know if it was installed and set up correctly, but I suspect that some setting is wrong. 
I did not check the box marked "Install third-party software for graphics and Wifi-hardware, Flash, MP3 and other media". Was I wrong?

---

### Post by sudodus on 2018-03-16
Can the computer connect to the internet?

- If yes, I don't think it should make a difference concerning pppoeconf.

- If no, I suggest that you try to connect via wire (ethernet) or install a proprietary driver for WiFi.

If you need WiFi but cannot make it work, and if your system is new, then you re-install with the option "Install third-party software for graphics and Wifi-hardware, Flash, MP3 and other media".

-o-

I am no expert on WiFi. If still no luck, I suggest that you start a **new thread** with a title about your WiFi problem.

---

### Post by matthew-wai on 2018-04-21
I booted it from the Lubuntu 17.10.1 Live SD card and ran the following:
```

lubuntu@lubuntu:~$ pppoeconf
The program 'pppoeconf' is currently not installed. You can install it by typing:
sudo apt install pppoeconf
lubuntu@lubuntu:~$ sudo apt install pppoeconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ifupdown
Suggested packages:
  rdnssd xdialog
The following NEW packages will be installed:
  ifupdown pppoeconf
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 70.0 kB of archives.
After this operation, 356 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 <http://archive.ubuntu.com/ubuntu artful/main> amd64 ifupdown amd64 0.8.16ubuntu2
  Temporary failure resolving 'archive.ubuntu.com'
Err:2 <http://archive.ubuntu.com/ubuntu artful/main> amd64 pppoeconf all 1.21ubuntu1
  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.8.16ubuntu2_amd64.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pppoeconf/pppoeconf_1.21ubuntu1_all.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
lubuntu@lubuntu:~$ apt-cache policy pppoeconf
pppoeconf:
  Installed: (none)
  Candidate: 1.21ubuntu1
  Version table:
     1.21ubuntu1 500
        500 <http://archive.ubuntu.com/ubuntu artful/main> amd64 Packages
lubuntu@lubuntu:~$ sudo apt update
Ign:1 cdrom://Lubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105) artful InRelease
Hit:2 cdrom://Lubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105) artful Release
Err:3 http://archive.ubuntu.com/ubuntu artful InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:4 http://archive.ubuntu.com/ubuntu artful-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:5 http://security.ubuntu.com/ubuntu artful-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful-updates/InRelease  Temporary failure resolving 'archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by sudodus on 2018-04-21
```
Temporary failure resolving 'archive.ubuntu.com'
```

indicates a temporary failure. In other words, it might work better if you wait a while and try again.

But you need a working connection to the internet. Please check, that you can reach to some web site, that we know well, for example

```

$ ping ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=49 time=47.9 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=49 time=48.9 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=49 time=48.7 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=4 ttl=49 time=48.6 ms
^C
--- ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 47.970/48.574/48.904/0.390 ms

```
and after that try
```

$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.152) 56(84) bytes of data.
64 bytes from steelix.canonical.com (91.189.88.152): icmp_seq=1 ttl=50 time=48.5 ms
64 bytes from steelix.canonical.com (91.189.88.152): icmp_seq=2 ttl=50 time=47.5 ms
64 bytes from steelix.canonical.com (91.189.88.152): icmp_seq=3 ttl=50 time=48.4 ms
64 bytes from steelix.canonical.com (91.189.88.152): icmp_seq=4 ttl=50 time=48.4 ms
^C
--- archive.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 47.501/48.238/48.552/0.481 ms

```

Response from ping is still no guarantee that 'everything works' at archive.ubuntu.com, but it is a good start.

---

### Post by matthew-wai on 2018-04-22
> **sudodus said:**
> But you need a working connection to the internet. 
The program "pppoeconf" is absent from Lubuntu.
Internet connection is necessary for downloading "pppoeconf".
"pppoeconf" is necessary for setting up a PPPoE connection.
So, Internet connection is necessary for setting up a PPPoE connection on Lubuntu.
Thus it is impossible to set up a PPPoE connection without Internet connection.

Is it correct to say the above?

---

### Post by sudodus on 2018-04-22
> **matthew-wai said:**
> The program "pppoeconf" is absent from Lubuntu.
Internet connection is necessary for downloading "pppoeconf".
"pppoeconf" is necessary for setting up a PPPoE connection.
So, Internet connection is necessary for setting up a PPPoE connection on Lubuntu.
Thus it is impossible to set up a PPPoE connection without Internet connection.

Is it correct to say the above?

*Maybe* in your case, it is correct to say the above.

But in my case, it is possible to connect via wired internet (ethernet), and install pppoeconf (also in a fresh install of Lubuntu Bionic).

```
sudo apt install pppoeconf
```

---

### Post by matthew-wai on 2018-04-22
[https://debian.pkgs.org/9/debian-main-amd64/pppoeconf_1.21_all.deb.html](https://debian.pkgs.org/9/debian-main-amd64/pppoeconf_1.21_all.deb.html) 
Does the above pppoeconf_1.21_all.deb apply to Lubuntu 17.10.1 Desktop 64-bit? 
If yes, where should it be put on Lubuntu? Or should I simply double-click to install it?

---

### Post by sudodus on 2018-04-22
That version, 1.21 is what you can install via Ubuntu's main repository both in 16.04 LTS and Bionic. So it should be the correct version. In the file browser it should be possible to 'click on the deb file'.

But that way you will not get automatic updates (which is different from when installed via Ubuntu's repositories).

---

### Post by matthew-wai on 2018-04-22
Do you mean 1.21 is not the latest version? Where can the latest one be downloaded via Windows, which I am now running?

---

### Post by sudodus on 2018-04-22
I mean that it is probably compatible with 16.04 LTS and Bionic (18.04 LTS). 'Probably' because the Ubuntu developer might have modified it slightly before adding it to the Ubuntu repository.

(I have not checked for the latest version, and if there is one, it might cause problems, so 1.21 is probably a good choice.)

---

### Post by matthew-wai on 2018-04-22
What do you think about the ones below?
[https://www.ubuntuupdates.org/package/core/artful/main/base/pppoeconf](https://www.ubuntuupdates.org/package/core/artful/main/base/pppoeconf) 
[https://packages.ubuntu.com/en/trusty/all/pppoeconf/download](https://packages.ubuntu.com/en/trusty/all/pppoeconf/download)

---

### Post by sudodus on 2018-04-22
I cannot say that one of them should be better, except that the developers had a reason to improve something from the previous version to the next version. And that the same version as in the Ubuntu repository is tested with Ubuntu.

You can try both if you wish, I would still suggest version 1.21 first if you are running Ubuntu 16.04 LTS or newer , and if it works, fine (and you need not try the older one).

---

### Post by matthew-wai on 2018-04-22
What is the difference between the following?
pppoeconf_1.21ubuntu1_all.deb (15 KB)
pppoeconf_1.21_all.deb (40 KB)

---

### Post by sudodus on 2018-04-22
I don't know the details. The one with Ubuntu in the file name should be tested with Ubuntu.

---

### Post by matthew-wai on 2018-10-08
> **sudodus said:**
> I have checked and **pppoeconf** is in the repository **main** in 16.04 LTS as well as in 17.10.1, so it should be available in both versions of Lubuntu.

You can check with
```
apt-cache policy pppoeconf
```
Today I installed Lubuntu 16.04.5 LTS downloaded from _**[COLOR=#0000cd][this link]("http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04.5-desktop-amd64.iso")[/COLOR]**_ and then ran "apt-cache policy pppoeconf".
```
matthew_wai@matthew-pc:~$ apt-cache policy pppoeconf
N: Unable to locate package pppoeconf
```
> **sudodus said:**
>  Maybe it helps to run
```
sudo apt update
sudo apt full-upgrade
```See the results below:
```
matthew_wai@matthew-pc:~$ sudo apt update
[sudo] password for matthew_wai: 
Err:1 http://hk.archive.ubuntu.com/ubuntu xenial InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://hk.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Err:4 http://hk.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'hk.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'hk.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
matthew_wai@matthew-pc:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matthew_wai@matthew-pc:~$ sudo apt install pppoeconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pppoeconf
```
It was impossible to update/upgrade anything because Internet connection was unavailable due to the absence of "pppoeconf", which is present in Ubuntu but absent from Lubuntu.

---

### Post by sudodus on 2018-10-08
Try the 'first' point releases, [Lubuntu 16.04.1 LTS](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/) and [18.04.1 LTS](cdimage.ubuntu.com/lubuntu/releases/18.04.1/release) (instead of 16.04.5 LTS).

---

### Post by matthew-wai on 2018-10-09
> **matthew-wai said:**
> Today I installed Lubuntu 16.04.5 LTS downloaded from _**[COLOR=#0000cd][this link]("http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04.5-desktop-amd64.iso")[/COLOR]**_ 
> **sudodus said:**
> Try the 'first' point releases, [Lubuntu 16.04.1 LTS]("http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/") 
The two links actually provide the same version "lubuntu-16.04.5-desktop-amd64", which includes no "pppoeconf". Today I installed "pppoeconf_1.20ubuntu1_all.deb" downloaded from _**[[COLOR=#0000cd]this link[/COLOR]]("https://packages.ubuntu.com/en/trusty/all/pppoeconf/download")**_, and I have successfully set up a PPPoE connection. The said .deb file is only 17KB. I wonder why the .iso file does not include it.

---

### Post by sudodus on 2018-10-09
1. My link *does* provide Lubuntu 16.04.1 LTS (but also 16.04.5 LTS, if you scroll further down).

2. I'm glad that you found a working pppoeconf deb file, that solves your problem :-)

---

### Post by matthew-wai on 2018-10-11
Today I failed to access the Internet.
```
matthew@matthew-pc:~$ sudo pppoeconf
[sudo] password for matthew: 
Plugin rp-pppoe.so loaded.
matthew@matthew-pc:~$ plog
Oct 11 23:48:59 matthew-pc pppd[4471]: Plugin rp-pppoe.so loaded.
Oct 11 23:48:59 matthew-pc pppd[4472]: pppd 2.4.7 started by root, uid 0
Oct 11 23:49:05 matthew-pc pppd[3235]: No response to PAP authenticate-requests
Oct 11 23:49:05 matthew-pc pppd[3235]: Connection terminated.
matthew@matthew-pc:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Is "System Files" missing from "Home Folder" in the screenshot below?
I cannot find "/etc/ppp/peers/dsl-provider".

---

