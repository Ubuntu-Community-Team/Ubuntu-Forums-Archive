---
title: "Installation on blank Hard drive"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by VSparks on 2011-03-01
Hello,
I have received an Asus Infiniti Plus with Pentium 4 but the previous owner removed the hard drive "for security reasons." I am trying to put a salvaged (it operates correctly as an external HD in a sleave) Dell laptop hard drive in it to use Ubuntu as the operating system. It will not boot with the original Dell version of Windows XP. Some one said to expect that problem. I have erased all from the hard drive except for 1 or 2 files for which there was "access denied." 
 
I down loaded Ubuntu 10.10 iso file (for windows) and placed it on the hard drive but it also does not boot, only momentarily saying Dell and that windows could not start because of missing or corrupt file &#8212; system 32\hal.dll.
 
Now that my amateur status is probably obvious, is there a way to install ubuntu in bootable form on a hard drive/computer without another operating system present? (Also, how do I totally erase the Dell version of Windows XP?)
 
I appreciate your help,
VSparks

---

### Post by tommcd on 2011-03-01
> **VSparks said:**
> 
I down loaded Ubuntu 10.10 iso file (for windows) and placed it on the hard drive but it also does not boot, only momentarily saying Dell and that windows could not start because of missing or corrupt file &#8212; system 32\hal.dll.

The Ubuntu for Windows is called Wubi. This is intended to install Ubuntu inside a functioning Windows OS. This way it can be deleted from Windows just like any other Windows application.This is meant to only try Ubuntu. If you do not have a functioning Windows OS, this will not work.

Just install the regular Ubuntu 10.10 linux iso:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Then burn it to a CD. If you are burning the CD from Windows, use Iso Recorder or Infra Recorder, and be sure to burn the disc at the slowest possible speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot the Ubutnu CD, be sure to run the option to *Check CD for Defects*: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
Note: You may need to hit the space bar when you boot the Ubuntu CD to see the option to check the CD for defects. This will insure that you have a valid CD to use to install Ubuntu:
See this for getting started with Ubutnu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And here is a simple beginners guide to install Ubuntu 10.10:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
write back if you need more help.
And welcome to the Ubuntu forums!

---

### Post by sahilsameerac on 2011-03-01
Yes, undoubtedly you can install
ubuntu will not create any problems
then insert the cd and chose manually specify partitons
select the partition you want to install and double click on it
in the first drop down box select ext 4
and the second drop down box select /
then install and enjoy

if disc is not booting go to bios setings-boot and select cd rom as first boot device

---

### Post by Hedgehog1 on 2011-03-02
> **VSparks said:**
> 
... 
**[SIZE="2"]I down loaded Ubuntu 10.10 iso file (for windows) and placed it on the hard drive but it also does not boot[/SIZE]**, only momentarily saying Dell and that windows could not start because of missing or corrupt file &#8212; system 32\hal.dll.
...


Hello VSparks!

I think I see the issue.

You cannot copy the ISO file onto the hard drive (That would be TOO easy).

Instead, please use CD burning software and burn a CD 'From an ISO'.

An ISO file is an entire CD compressed into the smallest data file we can squeeze it into to. 

Most burning software has a 'Burn ISO' option, that converts the compressed ISO file into a fully populated CD.

If you end up with a CD that has only the ISO file only on it, you did it wrong (and most of us did it wrong the first time, too)

Once you have that CD, put in in the CD drive of the PC, and boot it.  The PC Should boot off the CD - but you may have to change the boot order in the BIOS if it doesn't.

Once it boots, you can TRY Ubuntu or INSTALL Ubuntu. You want to install.

***The Hedge***

:KS

---

### Post by swift100 on 2011-03-02
Hi, use the links given by tommcd, download from here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I would personally go for ver. 10.4 as I've read that it's more stable and 10.10 doesn't work with Wubi which a lot of people benefit from when there's software only for Windows.

Burn a bootable disk from the downloaded image, change the boot order in BIOS or keep pressing F12 right after turning the pc on and select CD/DVD drive from the boot menu. When the pc loads the disc play around with it to test if you like it and install. Follow this page for instructions:

[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

To wipe the drive clean you need to use an app called ActiveKillDisk. Download the free version from here:

[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

Again you will have to create a bootable disc. There are usage instructions there as well.

---

### Post by VSparks on 2011-03-02
Great! :)
Thanks to all for the counsel and guidance. It will take me a few days to work through it in my spare time but it looks like light at the end of the tunnel. 
Many thanks, VSparks

---

### Post by VSparks on 2011-03-06
I did Killdisk on the HD as an external HD from WindowsXP on my personal computer. It was no longer visible to desktop explorer.
 
I put it in the new computer without present HD or OS and installed Obuntu but it stalled at 24% twice and 38% the third try. The HD shows as a single space without partitions - can this be the problem? lacking formatting.
 
Appreciate your help.
VSparks

---

### Post by Hedgehog1 on 2011-03-06
VSparks,

When installing, are you choosing the 'erase and use entire disk' option? You should be.

You should see at least 2 partitions on the disk, unless you do a manual partition layout and make more.

***The Hedge***

:KS

---

### Post by VSparks on 2011-03-07
> **Hedgehog1 said:**
> VSparks,
 
When installing, are you choosing the 'erase and use entire disk' option? You should be.
 
You should see at least 2 partitions on the disk, unless you do a manual partition layout and make more.
 
***The Hedge***
 
:KS
 I did with one of the tries. I believe that I am only seeing one partion, but after it says Ubuntu is on the HD it shows a second smaller "swap" partion.
VSparks

---

### Post by Hedgehog1 on 2011-03-07
Vsparks,

The two partitions you saw were a little one for swap space, and a big one for Ubuntu.

The fact that you seem unable to format the whole drive can be caused by a number of things; the one that comes to mind is the 120 gig limit on the boot partition on older hardware.

Please try this:

Reinstall, and choose the 'specifiy paritions manually (advanced)' option.

Create 4 partitions:

10 gig ext4 that mounts as '/boot'
20 gig ext4 that mounts as '/'
5 gig as swap
all the rest of the drive as ext4 that mounts as '/home'

I think this will get you past the issue - but if it doesn't, then change the size of the '/home/ to just 20 gigs and see if you can install.

***The Hedge***

:KS

---

