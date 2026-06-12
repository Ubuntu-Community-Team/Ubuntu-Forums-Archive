---
title: "Xubuntu install woes"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by sambler on 2006-06-16
Hello. I am planning to try to post this to an appropriate site as a mini-review of the Xubuntu installation process. I would like to get some comments and feedback first.

I am generally extremely pleased with Ubuntu Dapper. I have installed it on three desktops and one laptop. Dapper has perfectly detected my hardware, including a wireless card on one of the desktops and a different wireless card on the laptop.

One of the desktops is an older machine with a Celeron processor and 128 megabytes of RAM. It is too old and slow to run Ubuntu or Kubuntu, so I decided to do an install of Xubuntu. I find the XFCE interface to be extremely fast and flexible even on faster machines. I have installed the xubuntu-desktop package on all of my machines, and alternate between using it and using Gnome. I finally have xubuntu-desktop running on my Celeron machine, and I am extremely happy with it. It's quite snappy and will allow me to get a few more years of productive use from an old machine. However, getting it installed on the machine was a nightmare.

This is the tale of my installation woes. I'm writing it in an attempt to provide some constructive criticism, in the hope that the next versions of the Xubuntu  live cd and alternate install cd will allow for trouble-free installation even on low-memory machines.

I'm writing this partly from my own perspective and partly from the hypothetical perspective of a neophyte who wants to install some kind of Linux distribution onto an older machine. I am not a neophyte: I first became a  Linux user when I installed a version of Slackware on a machine in 1998 from diskettes. So, I'm reasonably knowledgeable (or very stubborn), but I would consider myself a knowledgeable desktop user rather than an expert sysadmin.

In the past, I have used the text-based installation routines to install Ubuntu on various computers and have limited experience with running the live cd versions. I installed Dapper on my other machines by upgrading from Breezy (without a hitch).

I downloaded the release candidate version of Xubuntu 6.06 live cd and used it to fire up my computer, only to be confronted with trying to guess the default user name and password. I finally discovered what they were by posting on the Ubuntu user forums (the user name is ubuntu and the password      field is left blank).

Note that in general one goes through the entire process of downloading the Xubuntu live cd without running across this information. It's not on the home page:
[www.xubuntu.org](www.xubuntu.org)

It's not on the main download page that one accesses by clicking on the "download" link on the home page:
[https://wiki.ubuntu.com/Xubuntu/Releases?action=show&redirect=XubuntuReleases](https://wiki.ubuntu.com/Xubuntu/Releases?action=show&redirect=XubuntuReleases)

It's not on the release announcement page:
[https://wiki.ubuntu.com/Xubuntu/News/2006-06-01](https://wiki.ubuntu.com/Xubuntu/News/2006-06-01).

It's not on the release notes page:
[https://wiki.ubuntu.com/XubuntuDapperReleaseNotes](https://wiki.ubuntu.com/XubuntuDapperReleaseNotes)

It's not on the main page of the download site:
[http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)

There is no readme.txt file accessible from the latter page. I filed a bug report  (as did several other users). Perhaps as a result of this, the information was put up for a time on the main Wiki page ([https://wiki.ubuntu.com/Xubuntu)](https://wiki.ubuntu.com/Xubuntu)). Since the final release of the Dapper version, the page has been reorganized and the information is no longer there.

I gather the problem is not limited to Xubuntu. The bug is listed as #40689 and is a "confirmed" bug on launchpad.net for Ubuntu as well as Xubuntu. (I presume Kubuntu suffers the same fate.)

This is completely inexcusable. The information should be provided in big, bold letters **on the main login screen** that comes up when one boots the live   cd. As a fairly sophisticated user, I knew where to go to find the information, but it did take some time to get an answer. Think of a poor sod who is still using Windows 98 on an old machine and who stumbles across the Xubuntu distribution by visiting DistroWatch. They might burn the live cd and then give up in frustration when they find they can't log onto their machine. This has the potential of turning off a large number of potential converts to Linux.

I felt a bit like I was living in a version of Kafka's The Castle. To use a slightly more up-to-date pop cultural reference, it's like the Vogon order to demolish the planet Earth that was kept on file in a locked filing cabinet in a basement of a building on the Vogon homeworld.

Back to my saga.

Once I found out how to log on, I had a perfectly functional desktop running from the cd. I then chose to install to disk. Getting through the first few stages was a bit slow but straightforward, but then my machine choked (froze up completely) when I chose to do a custom partitioning of the hard drive. I don't think I'm alone here. A Google search of "ubuntu ubiquity partitioner" returns a whole series of results claiming that the installer will freeze at the partitioning stage with anything less than 256MB of RAM.

I then decided to use the alternate install cd instead to be able to use a  text-based installation routine that wouldn't use as much memory. All went well, and quickly, and I thought my troubles were over. I failed to notice that the installation process finished without asking me to set up a default user account. Trouble. I realized this when I tried to log on and failed. I also tried unsuccessfully to log on as root and was told that I did not have the correct password.

I am not the first person to experience this problem either. It's listed as bug #45206 on launchpad.net (as yet unconfirmed), and I've added my own comment to this bug report.

I rebooted the machine and went into recovery mode. I used adduser to add a user to the system and rebooted. I then dicovered that I could not invoke sudo to do any administrative tasks. Another reboot into recovery mode ... A glance at the /etc/group file told me that not only was the user not a member of the admin group, there was no line for the admin group and the user was not a member of any other group (such as floppy, cd, audio, etc.).

Rather than try to patch up the situation by struggling with various commands to add groups and add users to groups, I threw up my hands in frustration. (I haven't had much call to do this in the past since I am often the only user of my machines. When I have added other users, the distribution's default setup of groups has always worked.)

So how did I get an working desktop? I did a text-based install using an Ubuntu server cd (which did ask me to set up a user account), added the xubuntu-desktop and gdm packages from the command line with aptitude, and then booted up to a nice graphical login screen and a nicely configured XFCE desktop. (I personally don't mind that the developers have tried to modify the look of the XFCE desktop so that it looks as much like Ubuntu's Gnome desktop as possible.) With perfect hindsight I could have had a working system installed in less than half an hour.

I'm happy with the end result, but there is absolutely no excuse for putting users through all these hoops. I am astonished that, when I last checked (on June 16), Xubuntu was ranked 24 in the seven-day hit rankings on Distrowatch. I've actually seen it in the top ten at one point. I wonder how many people downloaded it, tried it out, and either went back to another Linux distribution or gave up on Linux altogether.

When people say that Linux is not ready for the desktop, it's frustrating experiences like these that many are referring to.

Here are some concrete suggestions:

1) For God's sake make sure that the alternate install cd sets up a default user during the installation process, and make sure that the default user is included in all the appropriate groups, especially (but not only) admin.

2) Include a friendly screen on the live cd that informs users of the existence of the alternate install cd and that they might like to try that cd if they are installing on a machine where the graphical install process is too slow or stops altogether due to insufficient memory. That way, someone who is given a Xubuntu live cd by a friend or an acquaintance will have a fighting chance to get Xubuntu up and running on an older machine. A reference to [www.xubuntu.org](www.xubuntu.org) on the bootup screen would help as well.

3) Include, in bright, friendly, red letters on the bootup screen the words "Don't Panic!" ;) As well, put the default user name and the default password on this screen in a noticeable location. This suggestion goes for the Ubuntu and Kubuntu live cds as well as for the Xubuntu version.

4) It would be possible to get installation to work (from the live cd) on low memory machines by including an option to set up a swap partition on the hard drive before booting up the GUI, or in the very early stages of the graphical installation routine. With very clear explanations this might work even for newbies, and it would certainly help more sophisticated users who are trying to rescue older machines with limited memory.

5) It appears that invoking custom partitioning during the installation process eats up a lot of additional memory. In my case, it appears to be the straw that broke the camel's back. It should be possible to add an option on the initial boot screen to allow the user to access fdisk or cfdisk in text mode. This would not be a big help for newbies, but it would be a godsend for more sophisticated users. Also, the graphical install routine could give the user the option to use either ubiquity's graphical partitioning tool or to drop temporarily into text mode to use cfdisk.

Thanks for reading.

---

### Post by bigfinch4991 on 2006-06-18
THANK you! Someone else with the exact same problem as me and a solution to boot! I'm going to try out the way you fixed yours up tonight. Just a question, do you have to be on the internet to get the xubuntu-desktop and gdm packages? What do you type in the command line? Thanks!

---

### Post by confused57 on 2006-06-18
[QUOTE=bigfinch4991]THANK you! Someone else with the exact same problem as me and a solution to boot! I'm going to try out the way you fixed yours up tonight. Just a question, do you have to be on the internet to get the xubuntu-desktop and gdm packages? What do you type in the command line? Thanks![/QUOTE]

What are your computer specs, i.e. CPU, ram, etc & do you have the means to acquire or have the Xubuntu-alternate CD?  This will help immensely for finding a possible solution for you.

---

### Post by bigfinch4991 on 2006-06-18
what I'm saying is XFCE already on the ubuntu server install cd?

---

### Post by confused57 on 2006-06-18
[QUOTE=bigfinch4991]what I'm saying is XFCE already on the ubuntu server install cd?[/QUOTE]

No, it's not on the Dapper server CD...it would be on the Xubuntu alternate CD, if you did a server install from that.

If you have less than 128 mb of ram, it'll be difficult to run Xubuntu...you probably can, but it would be slow.

---

### Post by sambler on 2006-06-18
Hi Bigfinch,

I'm glad to know that I'm not the only one to encounter the problem.

In my case I installed xubuntu-desktop and gdm over the Internet. The procedure is as follows. I hope I haven't left out any steps. I am assuming that you have already managed to do a server install using a Ubuntu server cd.

1) I first enabled access to the "universe" repositories by uncommenting the lines in the /etc/apt/sources.list file. Edit the file using nano (a very basic text-mode editor that is also self-explanatory). Make a backup copy first. Use the following commands:

cd /etc/apt
sudo cp sources.list sources.list.bak
sudo nano sources

You can name the backup file whatever you want. In the above, "sources.list.bak" is the backup file. Uncomment the relevant lines, save and exit.

I'm not sure this step is strictly necessary. The xubuntu-desktop and gdm packages may be in the "main" repositories.

2) Update the package index files using:

sudo apt-get update

3) Install xubuntu-desktop and gdm using:

sudo apt-get install xubuntu-desktop
sudo apt-get install gdm

The xubuntu-desktop package is a "metapackage" that basically contains a list of all the packages necessary for a complete Xubuntu desktop system.

If you don't have access to the Internet while installing, you can install from cd-rom, but you need to tell the apt-get program where to look for the packages. I installed the basic system from a Ubuntu server install cd. If you do the same, you will **also** need a copy of the Xubuntu alternative install cd (the Xubuntu desktop cd should also work). Insert the Xubuntu cd into your cd drive and issue the following command:

sudo apt-cdrom

This will add the new cd-rom to the list of available sources. Then just install xubuntu-desktop and gdm as in step 3) above.

Hope this helps.

---

### Post by sambler on 2006-06-18
Oops,

That should be:

sudo nano sources.list

in the above message, not:

sudo nano sources

---

### Post by ddryden on 2006-08-08
I've also just had the same expireience with the xubuntu live CD. My Dell Latitude CPi 266MHz with 128Meg's of ram has been quite happy with debian untill i recently needed a driver that wasnt in debian stables package list so i decided to give ubuntu a go. i must say im not very happy with the install from live CD idea on the low end hardware. Very slow and likes to crash abit.

I might give the alt install cd a go if there is a text based installer or the option to boot one.

---

### Post by ingeh on 2006-09-23
thank you very much for this explanation :D 
my laptop is freezing at excatly the same point with the live cd
i'll use your guide to install instead
thank you again

---

