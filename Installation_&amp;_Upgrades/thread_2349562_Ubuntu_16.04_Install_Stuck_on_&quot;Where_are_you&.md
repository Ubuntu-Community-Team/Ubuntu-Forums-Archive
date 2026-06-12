---
title: "Ubuntu 16.04 Install Stuck on &quot;Where are you&quot; on new Dell XPS 13 (9360)"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by jakecoll on 2017-01-16
I've been trying for several hours to install Ubuntu 16.04 on my new Dell XPS, but the install keeps getting stuck and hanging on "Where are you". I've tried the install both from "Install Ubuntu" and as a program in "Try Ubuntu without Installing" and it hasn't made a difference. I've also tried disconnecting from my WIFI networking since I came across an article in another forum where that worked for someone. Any help would be greatly appreciated. Thanks!

---

### Post by yancek on 2017-01-16
Since this is a new computer I expect it is UEFI compatible.  Are you booting Ubuntu in UEFI mode?  See the Ubuntu documentation at the link below which explains how to determine this.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Which Installation Type option are you using.  You don't mention having any other OS so you are you using the Erase Disk option to overwrite the entire drive.  If you do have another OS, that would be important information to post as would more details on the system or at least a link to the Dell site with details.  It's not realistic to expect others to look this up for you.

---

### Post by RobGoss on 2017-01-16
>   I've also tried disconnecting from my WIFI networking since I came across an article in another forum where that worked for someone  

I'm  assuming your wired up to install any third party software and update, this is an option but not necessary because you can still do this after your installation is completed

As mentioned the née UEFI bios is a bit more complex but doable it requires more reading and making a fee changes in your bios settings

You haven't given up enough information about your installation process it would be most helpful 

How did you try to install Ubuntu USB or DVD?

What software did you use to create your installation media?

The new UEFI bios required us to make a few changes in the bios depending on what machine is used some are harder to get Linux installed on them

---

### Post by oldfred on 2017-01-16
Please review this link, and link in my signature below for general UEFI install info.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

similar Dell models & the specific issues they had.
 Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[URL="https://ubuntuforums.org/showthread.php?t=2345444"]https://ubuntuforums.org/showthread.php?t=2345444
[/URL]
 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 

Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by howefield on 2017-01-16
Could be this bug : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1584417](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1584417) ?

---

### Post by jakecoll on 2017-01-16
The computer came with Windows 10 and I want to setup a dual boot. It has has 256 gb ssd storage and 7th gen i5 processor. I managed to get Ubuntu to install in legacy mode, but then of course it won't actually boot. I attempted using boot-repair but it still won't boot.

I made a bootable usb using rufus. I'm trying to do a dual boot since laptop came pre-installed with Windows 10.

---

### Post by iraiscoming223 on 2017-02-03
I am stuck on the same issue.
I am dual booting with preinstalled Win 10, and installing in EUFI mode. USB is recognised, SSD is also recognised, and everything looks happy and jolly. I even have Windows asking me which operating system I want to boot (with the Win bootloader). Just the installation get stuck.
I read A LOT on the internet, and then realised the following:
[LIST]
[*]The issue some users are having is with the internet time server (disconnecting from the internet solved this for some users, like someone before me already said)
[*]Looking at kernel messages, it appears the issue is with gparted, when resizing/formatting volumes (I loaded another distro, did the formatting and resizing, and then installed ubuntu, still stuck at the same point)
[*]I also tried downloading 16.04, 16.10, GNOME edition, same outcome
[*]Some users also reported that installing ubuntu with the aid of an exorcist has helped in some cases, but I'm stuck on the Himalaya and don't have access to an exorcist
[/LIST]

Given the reasons above - any more Ubuntu-savvy user willing to help / have suggestions? Happy to try new approached, just don't have access to the aforementioned exorcist... ](*,)

---

### Post by oldfred on 2017-02-03
@iraiscoming223
Often better to have your own thread, but since some system we will leave it for now.

Have you checked AHCI vs. RAID settings in UEFI?
Is Windows fast start up (hibernation) off?
Dell sells Ubuntu systems. But offers Sputnik as drivers for those systems. Often then those newer drives get incorporated into newer Linux distributions.

When I built my new Skylake system about a year ago I knew it needed the newest Ubuntu/kernel, drivers and other support software. So even though 16.04 was not yet released, I installed 16.04 and it just worked. I prefer to use LTS versions, but often install newer ones just to see what has changed. But if LTS version supports one's hardware they should keep that as main working system.

That said, try 17.04. It may still have breakage as not yet released. Your then are a tester.
You will need to reinstall with 17.10 and then 18.04LTS. 
I also prefer clean installs, but have large enough drives to have several / (root) partitions and larger separate data partition(s).

 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by iraiscoming223 on 2017-02-03
Hi oldfred,
thanks for your quick reply.
Fast Start Up is off, and I tried to use both AHCI and UEFI, no changes.
What bothers me the most is that the distro boots properly in live mode and is completely usable! It's just the installation that fails!

I will give it one more chance, but if that fails... any suggestion on how to incorporate / load new drivers prior installation? This is a production machine and I'd rather not use an unstable distro.
If i keep failing I may even just go Ubuntu server and then install everything separately!!
Thanks in advance

---

### Post by oldfred on 2017-02-03
That live installer works and installer fails is not normal.
But often Windows related if it is the partitioning stage as it cannot see the NTFS correctly if hibernated or needs chkdsk.

Where exactly does it fail?
Are you using one of the auto install options, or Something Else? If past partitioning, you can see what it is doing at bottom of screen.

---

### Post by RobGoss on 2017-02-03
> **jakecoll said:**
> I made a bootable usb using rufus. I'm trying to do a dual boot since laptop came pre-installed with Windows 10.

Did you create a unallocated partition for Ubuntu to be installed on? you can do this with Windows Disk management tool, after that boot the live desktop from your USB for Ubuntu and choose that unallocated partition and go from there

Also If your machine is a newer one it's probably **UEFI** and that means if Windows is installed in **UEFI **then you have to install Ubuntu the same way

---

