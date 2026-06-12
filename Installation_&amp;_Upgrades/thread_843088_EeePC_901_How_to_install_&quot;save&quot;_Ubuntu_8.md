---
title: "EeePC 901: How to install &quot;save&quot; Ubuntu 8.04?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-06-27
I am going to buy an Asus EeePC 901, which is loaded with Xandros Linux.

I want to swap it to Ubuntu.

My first questions before I start are:

How can I get first all settings .... backup from it before I install Ubuntu? E.g., how to use the sound, the camera, ...

How can I get back to Xandros if it doesn't work?


I am planning to add a Microdrive 2 GB (real hard disk) for swap.

Any hints to get this move quickly would be highly appreciated.

bye

R.

---

### Post by ELMIT on 2008-07-01
No hints????

... and in about 14 hours I will have one.

HINTS PLEASE!!!  ;-)


bye

R.

---

### Post by Herman on 2008-07-01
:) Hello ELMIT,
I don't have an eee pc yet myself, but I certainly like the idea of buying one, I'm strongly considering it.
The model of EeePC I'm looking at is the smallest and most basic one, (I like the idea of a laptop that will fit in my lunchbox). It doesn't have any CD/DVD drive, but it does have three USB ports. I'd probably use one of my USB flash memory stick Ubuntu installations to boot with initially. 			 			[How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528").
I would use Ubuntu in my USB stick to make a Partimage backup of Xandros because then I'd always be able to restore the laptop to 'as new' or original conditition from the Partimage backup. Maybe I'd make two Partimage backups to be sure.
The best how-to on Partimage I've ever seen is at aysiu's site, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").

I would download Ubuntu Eee and install that, [Ubuntu Eee]("http://www.ubuntu-eee.com/index.php5?title=Main_Page"). I think it would  save a lot of work to just install Ubuntu eee which is Ubuntu that's already optimized for the Eee PC rather than installing the standard Ubuntu and doing all the work of getting the wireless networking and so on all set up myself.

I hope I'm being helpful, I can't speak from experience yet, but that's what I would do if I had an Eee PC, (or should I say 'when I get one'.
Regards, Herman :)

---

### Post by ELMIT on 2008-08-03
I finally got my EeePC 901 Linux, and yes it needs to install Ubuntu instead of Xandros.

I like the idea to use partimage, but I cannot install partimage, because I have no Ethernet in the initial phase. 

To install Ethernet, I need to build-essential, which requires Ehternet, ...

I am in a dead loop. Can anybody help please?

bye

R.

---

### Post by Herman on 2008-08-03
:) Hello ELMIT,
One of the best ways to get Partimage is to download [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and burn to disc, (make it into a CD), it has Partimage in it. You just boot GParted LiveCD and open a terminal and type 'partimage', to start partimage. (There are no icons for it, you just have to know it's there).
GParted LiveCD is free and it's only a small download and it's very useful.

[System Rescue CD]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.sysresccd.org%2F&ei=vHeVSLjHKoq2sQPW1uCiCg&usg=AFQjCNHLezgCI1IM3RH_amPHKhYtEeiaEQ&sig2=76MH4yUMN-axzdHucqpKmQ") is another very good CD with contains Partimage, also free but a bit larger download, it has lots of useful programs in it.

Regards, Herman :)

---

### Post by ELMIT on 2008-08-03
Your hint comes to late!

I needed to convert this pc to Ubuntu mainly because I need to install some more programs.
To be able to go back I wanted to make the backup.

On my search on the Internet I found that Xandros has also this program I need, ... I followed the instructions, ... and the last line during the installation started with "rm ... " --- Not a good feeling.

For a short moment I thought some programmer copied the MRTG installation, where at the end he said thanks for ordering the CD, ...

... but it was not so. My desktop is now empty!

So I go ahead to install Ubuntu without a way back!


And I get the next problem:
To get Ethernet and wireless to work I need to install build-essential, 
... All afternoon I tried to go to the web site:
[http://packages.ubuntu.com/hardy/i386/build-essential/download](http://packages.ubuntu.com/hardy/i386/build-essential/download)
(this page I found in three docs mentioned how to get Ethernet working), but this page is unavailable!!!! or is wrong, ... 

Any hints?

---

### Post by ELMIT on 2008-08-04
I used the recovery CD ... and I am back on Xandros.

I have made a 8.04.1 USB Flash-drive as Live-CD with unetbootin-linux-248.

It boots! But as expected, it does not have build-essential, so I cannot continue yet till the [http://package.ubuntu.com](http://package.ubuntu.com) web site is up again.

However, I need some thinking help ;-)

The USB Flash-drive is a Live-CD, so I have to install it somewhere. Can I use a 8 GB SD card (just saw a price of less than 30 US$) as my installation target? With Grub, which could find now Xandros????

One step more. Would it be possible to install on the same SD Windows XP as well? and bind it into Grub?

bye

Ronald

---

### Post by Tha-Fox on 2008-08-13
Did you install the standard Ubuntu or EEE Ubuntu? Did you get everything working, including microphone, webcam and so on? If you got, are the settings there after kernel update too?

I livein a hope that I get my 901 in two weeks. I'm unsure whether it's a good thing to install Ubuntu or not. I'd like to install it, but I also want everything work.

---

### Post by mac-duff on 2008-08-13
Hey dudes,

maybe this can help:
[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

I also will get my 901 hopefully in two weeks but also not sure if I should install ubuntu....

---

### Post by Tha-Fox on 2008-08-14
There is now array.org`s [kernel]("http://www.array.org/ubuntu/index.html") out that supports 901 100%. So everything should work. Haven't tried it myself though.

---

### Post by ELMIT on 2008-08-14
Thanks I will try it tomorrow.

I have some concerns though:

1. I have installed 8.04.1, does it make a difference?
2. "Hotkey Support (Fn-F2, Fn-F7 to Fn-F9)"
I have not tried it yet, but I would need Fn-F5 - second monitor, does it work out of the box or why is nowhere mentioned?

I found already one problem with the EeePC (not related to Ubuntu).

I have 2 GB RAM, 1 SD card 8GB and if I use wireless Internet connection AND Bluetooth mouse, the power supply cannot anymore charge the EeePC. E.g., if I used the EeePC first without power supply and it dropped to 54% battery, then even I connect the power it does not anymore charge. It remains on 54% !!! (Maybe it will go up, but not within the first 6 hours !!!) I have to turn it off and charge it in turned off status.

bye

R.

---

### Post by ELMIT on 2008-08-14
Could not wait till tomorrow, .... worked great!
(Not tested all)


Wireless came up immediately and suggested me to download 105 packages.

There is also included linux-images/headers for 2.6.24-19   

What should I do ? untick this or download? The eeepc kernel is on 2.6.24-21 !!!!

bye

Ronald

---

### Post by ELMIT on 2008-08-14
Some problems I found:

1. USB mouse:
"Couldn't display "obex://[00:07:61:D1:C1:40]/"

Error: Host down
Please select another viewer and try again.

---> Which host? Which viewer? What does the error mean?


2. USB flashdrive will not be mounted, shows an error:

Cannot mount volume.
Invalid mount option when attempting to mount the volume "USB-disk".


I could install the files, because I have on that harddisk also a ext3 partition, where I deposit the files.


3. Camera is not found in Skype

4. Audacity cannot record from my microphone - Skype also fails with the test call

Will test later more, maybe somebody knows already some hints for above.

bye

Ronald

---

### Post by Infra on 2008-08-19
> **ELMIT said:**
> Some problems I found:

2. USB flashdrive will not be mounted, shows an error:

Cannot mount volume.
Invalid mount option when attempting to mount the volume "USB-disk".


I could install the files, because I have on that harddisk also a ext3 partition, where I deposit the files.




2) Remove the cdrom or /dev/sdX (your usb stick) reference from /etc/fstab so it won't try to mount it wrong. I had the same problem after install, and it's because the installer puts the usb-stick also in the fstab file.

And then...if you don't already know...DO NOT USE JOURNALING FILESYSTEM for SSD. Journaling (like ext3) wears/kills your SSD much faster than non-journaling, because journal is being written like every couple of seconds. Also mount your SSD drives with the noatime option (put it in /etc/fstab)

Also do the tips for EEE 901 from [http://wiki.ubuntu-eee.com](http://wiki.ubuntu-eee.com)

---

### Post by Tha-Fox on 2008-08-20
> **Infra said:**
> 

And then...if you don't already know...DO NOT USE JOURNALING FILESYSTEM for SSD. Journaling (like ext3) wears/kills your SSD much faster than non-journaling, because journal is being written like every couple of seconds. Also mount your SSD drives with the noatime option (put it in /etc/fstab)



How fast is this wearing? I read "some articles" whics said that those would last about 17 years. If I use ext3 for example, will it last only 1 or 10 years?

---

### Post by Herman on 2008-08-21
Roughly 51 years, if you agree with the following linked article,[SSD Myths and Legends - "write endurance" article in STORAGE ...]("http://www.google.com.au/url?sa=t&ct=res&cd=9&url=http%3A%2F%2Fwww.storagesearch.com%2Fssdmyths-endurance.html&ei=CButSMy0Mpm0sAP_vvDeDQ&usg=AFQjCNEAP2fy0azBU7Aw-Qp00MmZnJ5MTA&sig2=uskLsEiNEWIrA6eJKGXqpA")

That calculation is for a 64 GB flash memory device, thee eeepc only has a 4 GB flash memory I think. 
Can a mathematician with a little computer knowledge shed any more light on this subject for us? 

The [Ubuntu eeepc wiki]("http://www.ubuntu-eee.com/index.php5?title=Main_Page") has a page about how to reduce write cycles to the flash memory, [How to: Reduce Disk Writes to Prolong the Life of your Flash Drive]("http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive"). That page looks like it contains some very useful information.

Pendrive Linux has users download their own special initrd.img which they say reduces writes to flash memory sticks.

It's hard to find any decent tests or figures on this subject.

---

### Post by dimov000 on 2008-08-21
As a matter of fact I am already for three months into EEE. Started with a 4Gb 700 and changed to a 20Gb 900.
As they come standard with xandros you could change it into advanced mode and have a full desktop in front of you as easy mode gives you a kind of tabs with programs and no more.
The Xandros comes with a Fn F9 to  bbring back the EEE in factory defaults.
Go to [www.eeeuser.com](www.eeeuser.com) or [www.eeeusers.nl](www.eeeusers.nl) to find out in wiki how to change to advanced mode.

On my 900 I changed to EEEBuntu version from eeebuntu.org This is a specially made ubuntu version for EEE. 
This one is coming in desktop version or in netbook remix...which I have.
There is also a Ubuntu EEE, which I tried but gave to many difficulties.

My EEEBuntu version took 45 minutes to install from a DVD. I had to do a few scripts and tricks and now all works properly.

I made a manual which explains all incl tips and tricks and a how to...
Unfortunally its in Dutch.

If there are any questions...do not hestitate to mail me or shout...or visit [www.eeeuser.com](www.eeeuser.com)

Dimov000

---

### Post by ELMIT on 2008-08-25
I am not anymore sure if I installed ext2 or ext3. How can I find that out now?

---

### Post by Tha-Fox on 2008-08-25
I think you can find that out with: ```
sudo gedit /etc/fstab
```

---

### Post by Alcareru on 2008-08-25
> **Tha-Fox said:**
> I think you can find that out with: ```
sudo gedit /etc/fstab
```

Technically speaking there you can only read what is written in the fstab. If I remember correct Ext3 partitions can be mounted as ext2 (though I doubt that ext2 partitions could be mounted as ext3). There for at least in principle it is possible that information in fstab is not accurate even if the partition mounts correctly. To print the partition table you could do:
fdisk -l /dev/somedevice but it wont tell you the filesystems (says only Linux). So an alternative to that is to type the command:
parted /dev/somedvice print
These of course require root privileges so sudo or something..

---

### Post by mac-duff on 2008-08-25
Hi there,
it seems there are a kind of different Ubuntu Version for the EEE PC out. I really like for my normal laptop the standard Ubuntu Version, but which shall i take for my 901? I would also prefer to do it with a step by step guide there my linux skills are not the best

Thx

---

### Post by Paul_K on 2008-08-25
I installed the eee version of 8.04 on my eee 901.  I got everything to work except for wired ethernet (might work, haven't tried)

Here is a good doc to make a bootable USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Getting everything to work:

[http://www.ubuntu-eee.com/index.php5?title=EeePC_901](http://www.ubuntu-eee.com/index.php5?title=EeePC_901)

I booted from USB and installed to an 8Gig SD card in the SD slot, leaving Xandros for dual boot.  Am thinking I will install the next version over Xandros.

One advantage of my setup was if I needed anything I could boot into Xandros, download what I needed and save it to the SD card, reboot into Ubuntu and have the files.

It is sooo worth it.  I was surfing all weekend on my EEE.  Nice and quiet, light and cool.  Battery life is great, 4+ hours.

I tried the Netbook Remix and disabled it.  Too quirky and plain vanilla Ubuntu looks great on my EEE.  I actually preferred the Xandros interface to Netbook Remix.  Maybe when it gets a little more polished...

Enjoy!  I sure am :-)

-PaulK

---

