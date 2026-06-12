---
title: "Installing ubuntu ultimate edition from iso file"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by enthusiastic.sady on 2008-09-21
Dear guys,

I have an iso file (DVD image) of ubuntu ultimate edition. I am currently using windows. I have a CD-ROM drive (reader only). When I mounted a virtual drive using Alcohol 120%, the autorun of wubi comes with 2 options, one is - install inside windows (when I click this, it states "You need atleast 256mb memory to run the installer" (I just have 128 mb).
The other option is "Demo and full installation" which requires restart and since my virtual drive loads only after windows so it cannot boot through the mounted virtual drive. Thus the 1.3 gb iso has made me sad. Is there any way to install using the iso file without using CD-ROM drive ? Please help I am dying for using ubuntu. Actually I just need to install "base system" coz I know the KDE or GNOME is "NO" with low RAM. After installing base system once, I will choose, download and install things manually and customize my system for me.

Please help,
Pranav Nandan

---

### Post by Vadi on 2008-09-21
I would not recommend "Ubuntu Ultimate" at all to anyone. I do recommend against it, as the people who put it together have (apparently) little knowledge. They're also making another program ("Ultramatix" or something like that), that is known to break Ubuntu's because of the unsafe things it does.

Also, 128mb ram is very, very small these days. Even the normal Ubuntu won't run on that, nevermind the bloated (because it pre-installs a *ton* of programs and services) 'Ultimate' ubuntu will not.

You're better off trying **Fluxbuntu** or **Xubuntu**. Those are designed for machines such as yours.

---

### Post by enthusiastic.sady on 2008-09-21
OK I want Xubuntu, Is there a place anywhere where I can download the minimal system (text based) sth called base-installation only. I am asking this bcoz' the speed I have is just around (4-8)kbps. So downloading an iso of 500mb is a very tough job.

---

### Post by Vadi on 2008-09-21
[http://www.xubuntu.org/news/hardy.1/release](http://www.xubuntu.org/news/hardy.1/release)

You want the 'alternate' CD, it's text-based and only needs 64mb ram.

Or here's a Fluxbuntu link ([click]("http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso")), only 300mb...

---

### Post by enthusiastic.sady on 2008-09-21
Thanks too much for the link. (:-> I am downloading it. Now the last one - Can I install fluxubuntu without CD-ROM drive ? Perhaps by using iso. I have partitions and free spaces. Is it possible (by using some kinda emulators or virtualization that could mount the image and boot from it so that I install ?

---

### Post by Vadi on 2008-09-21
You 'burn' the iso onto the CD, put it in, and then it will boot from the CD.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by enthusiastic.sady on 2008-09-21
Thanks for the Wonderful Distro ! It's already 33% amazingly. I will definately try it, it seems too cool for my PC (I just read abt it and saw screen shots). Being based on ubuntu and ubuntu itself based on debian, does that mean I can install and run all software that are made for these two ?. Can a software made for Gnome, Kde or Xfce always work on each other or sometimes only ? What are repositories. Will you please clear these terms ?

---

### Post by Vadi on 2008-09-21
All Ubuntu/Debian/Gnome/Xfce software will work fine. KDE software will require an installation of KDE, which might slow your computer down.

'repositories' are servers that have software in them, and you can install it from them easily. You can find software available in repositories by doing to applications - add/remove after you install it.

---

### Post by enthusiastic.sady on 2008-09-21
I use a NIC RTL8139D, which I need to run in fluxubuntu. I have'nt tried it in any Linux Distros till now. It works in windows though being a duplicate real-tek driver from Shingai-China bcoz' it came with a CD that has drivers tampered for it.

In the same CD there's a Linux driver : sl_linux.tgz
there are instructions for it which are as follows:-

> *************************************************
**   Silan SC92031 PCI  Fast Ethernet Adapter  **
**                                             **
**   LINUX driver                              **
*************************************************

Introduction:
=============

    The instructions are for linux driver installation. You must
    compile the source code to generate sc92031.o and use insmod command to
    insert sc92031.o as module.

Contents of the Subdirectory:
=============================

    readme.txt                This file.
    sc92031.c                 The linux core driver source code file
    Makefile                  Makefile for generating driver object file
    
Kernel Supported
================
    This driver support linux kernel version 2.4.x/2.5.x now.

Installation
============
    1) Create a temporary directory:
        # mkdir /temp

    2) Change to the temporary directory:
        #cd /temp

    3) Copy driver (sl_linux.tgz) from CD-ROM to the temporary directory, and follow the commands: 
       # mount -t iso9660 /dev/cdrom /mnt
       # cp /mnt/sl_linux.tgz /temp

    4) untar the archive file:
       # tar xzvf sl_linux.tgz
       # cd sc92031
    
    5) Compile the driver source files and it will generate sc92031.o, and
       copy it to correct driver installation path (The installation directory
       is different in different kernel versions. In 2.4.x kernel, the path is 
       /lib/modules/KERNEL_VERSION/kernel/drivers/net/, and in 2.2.x kernel,
       the path is /lib/modules/KERNEL_VERSION/net/)
       # make install

    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it 
       depend on your Linux distribution) for loading kernel modules. Make sure
       there is the following content in the configuration file, where # is 
       interface number :
        alias eth# sc92031 
  
    7) Reboot now:
        shutdown -r now 

    8) Install your driver module (If the driver module is in the wrong place,
       an error message will appear, and say that can't find the driver 
       module):
        insmod sc92031.o

    8) Use ifconfig command to assign the IP address, where # is network 
       interface number:
        ifconfig eth# <IP>

    9) Check the interface works:
        ping <remote_host_IP>



My question is that what is the kernel version for the 1 I am downloading, will it work. And how to compile a .c file in step 5. Do you have some sujjestions ?


Pranav,

---

### Post by Hello71 on 2008-09-21
First of all, KDE software will not need an installation of KDE. It *can* run in GNOME. However, it needs to initialize a bunch of KDE variables and such. (Which, considering your 128MB memory, seems to stretch your computer)

About your driver installation, you have a long file, so I'll comment as I go.
For steps 1-4, simply use the commands given.
For step 5, I think you type in make install.
For step 6, you need to look for the line alias [NETINTERFACE] sc92031 assuming [NETINTERFACE] = your network interface. Normally it is eth0 (ethernet #1) or wlan0 (wireless #1).
For step 7, use the command there.
Step 8, use the command there with the network interface you found in step 6.
9, use the command there.

As for your concerns about it working, it should work.

---

### Post by Blackwolf_Oz on 2008-10-31
> **Vadi said:**
> I would not recommend "Ubuntu Ultimate" at all to anyone. I do recommend against it, as the people who put it together have (apparently) little knowledge. They're also making another program ("Ultramatix" or something like that), that is known to break Ubuntu's because of the unsafe things it does.

Also, 128mb ram is very, very small these days. Even the normal Ubuntu won't run on that, nevermind the bloated (because it pre-installs a *ton* of programs and services) 'Ultimate' ubuntu will not.

You're better off trying **Fluxbuntu** or **Xubuntu**. Those are designed for machines such as yours.

Rather offended by your post.
 Have you tried this 1.9x64 bit edition?
I have been using Ultimate for the last 2 years & have nothing but praise for the creator, TheeMahn.
Yes, it is Ubuntu, but with everything except kitchensink.deb thrown in - free, non-free, alpha, beta, theta or just plain fun.  One of the more "unofficial" offerings around, Ubuntu Ultimate grew out of a couple of specialist gamer rebuilds (via Reconstructor) by programmer and Ubuntu Forums member TheeMahn2003. It takes a very direct approach to the whole free/non-free issue by including scripts that pop up offering to install binaries with "End User Licence Agreements", like Adobe, Flash and Java, before the installation is even finished. Naturally, Compiz/Beryl and every plug-in imaginable has been included too - as has Recontructor in case you feel like going one better.


    * 100% Lintian / Debian base error free.
    * Added debug routine to help find any errors (--debug).
    * Exclusive lock class subroutine written (makes the possibility of package breakage nearly impossible) - not yet fully implemented.
    * Total restructor of file layout to comply with Debian standards.
    * Added option to add repos or not (can still be removed through menu if user changes their mind later) - not fully implemented.
    * Added key gathering routine if the user decides to use repositories.
    * Created custom icons for all categories.
    * Removed dependency of tango icons.
    * Removed all traces of zenity and removed zenity as a dependency.
    * Chown added to return ownership of downloaded files to the end user.
    * Removed dependency of bash & GZip was totally unnecessary.
    * Added Financial category
    * Added Desktop Publishing category
    * Added Jedit Editor
    * Added Gphpeditor
    * Added Abiword
    * Added Wifi-support & Wifi Tools
    * Added T.V. Capture card software & tools
    * Added Blender, Yafray and Inkscape vector based editors
    * Added Qemulator, Qemu Virtualization tools
    * Added Yakuake Terminal
    * Added DeVeDe Dvd movie creator
    * Added Lemonrip dvd ripper
    * Added Isomaster
    * Added Brasero
    * Added Kmymoney2
    * Added Gnucash
    * Added Ktorrent
We live in a McDonald's culture. We want everything instantly and without effort. And we bristle when others around us appear to be getting more, sooner. Waiting for rewards or results is out of favor. It is so uncool. :shock:

Many things are created suddenly: the two-day house makeovers on HOME & GARDEN TELEVISION, for example, but they aren't great. They are adequate, functional, or practical improvements. Greatness requires thought and time, effort and sacrifice. Especially sacrifice.

Stellar careers aren't built overnight. Take the orthopedic surgeon, whose education extends 15 years past high school. Take the country western star on Grand Ole' Opry. Take the NFL quarterback or wide receiver, the CEOs, CFOs, and Vice Presidents of brand-name companies. Think about Edison, Einstein, or Galileo, or anyone else you might admire. None of them got there overnight.
Here are some key features of "Ultimate Edition":

· New theme / splash screen / wallpaper
· VCD Gear debian style
· Subversion & build tools
· Wireless Internet integration
· Bluetooth integration
· PPP integration
· Networking tools
· 35 Additional fonts
· Tons more themes
· Repository driven Beryl
· New sounds theme
· Integrated Custom repository support
· All current Updates 158 at time of posting
· IPod support
· Beagle
· Gramps - Genealogy software (thanks poweruser2600)
· Legends - Video Game
· Kapote - Instant Messenger
· Integrated codecs (the good the bad & the ugly)
· Mplayer, VLC, Songbird & Amarok players with mp3 support
· Mencoder, K9Copy, DeVeDE, DVD Shrink - dvd copying software.
· Integrated Nvidia drivers (will work with other cards)
· Automatix 2 & Automatix Bleeder (in case you want additional software)
· Gaim beta 5 & plugins
· GFTP - FTP Client
· KVIrc - IRC Client
· Additional Themes, icons, cursors & logins
· XSnow
· Samba
· NFS
· EasyTag - MP3 Tag Editor
· GDesklets
· Inkscape - 2D vector drawing
· Screem - HTML Editor
· Gambas - Programing environment
· QEMU & Kqemu Accelerator - Emulation
· Screem - HTML Editor
· Avidemux - Avi (divx /xvid) editor
· GDesklets - Eyecandy & info
· NTFS read / write support
· Lamp - web server (Apache2, mysql, PHP5)
· phpmyadmin
· Azureus - P2P software
· MS core Font's and extra fonts
· Wine - Windows emulation (always newest version - through repo)
· Alien - Allows installation of foriegn packages (RPM, suse etc)
· Gobby Team programing software
· Ksnapshot - Screen capture software
· Google Picasa - Graphic editing software
· Frostwire Pro - P2P software
· Kolourpaint - Graphic editing software
· Qcad - Autocad wannabe
· Archive Suite - virtually any archive can be handled.
· Ajunta IDE - Programing environment
· Bluefish - HTML Editor
· Glade - Interface designer
· Gtranslator
· Bit Tornado - P2P Software
· Amule - P2P software
· Kino - Flick editor
· Audacity - Sound editor
· Debian Menu (pdmenu)
· Dvdrip - Dvd ripping software
· Democracy Player
· Listen Media Manager
· Steamripper
· Ilinux (banshee)
· Gnucash - Financial software
· Aria - Download manager
· Build Essentials and make utility's
· Quanta Plus and extras - HTML Editor
· Graveman - burning software
· New Grub splash screen and animated "very pretty" boot up screen
· Bum - Boot-up manager
· Sum - Startup manager (newer improved version gtk and terminal based)
· Istanbul - Live screen capture
· Ghex - Hex editor
· Gourmet - Recipe manager
· Isomaster - CD / DVD ISO editor
· GPHPEdit - PHP Editor
· Kino - Clip editor
· Aria - Download manager
· Democracy - Movie streamer
· ClamAV - Anti-virus software
· Listen - Media manager
· DVD|RIP - Dvd ripping software
· Lifrea - RSS feed reader
· Brasero - Disc burning tool
· X-Chat - IRC Client
· QDVDAuthor - DVD authoring software
·
· Furthermore additional software such as Flash, Java, Acrobat Reader and Google Earth among others can be added using our integrated custom repo.



Great Operating Systems are built upon hundreds of thousands of small efforts, undertaken daily, that eventually grow into a series of satisfying wins.

Before you grind someones hard work into the ground on on widely read forum, please consider that you use your operating system, we use ours. Simple.

[http://ultimateedition.info/ultimate-edition-19/](http://ultimateedition.info/ultimate-edition-19/)

---

### Post by Zero Prime on 2008-10-31
I wouldn't listen to a thing Vadi says anyway.  He has a history of knocking any thing based on Ubuntu that tries to make a better OS.  It's a shame anyone at all listens to his posts.  It is almost like he has a personal vendetta against TheeMahn and Ultimate edition.

Look at it this way folks, Ubuntu is a nice car, basic options from the factory.  It just works and is reliable.  Nothing wrong with that.  Ultimate Edition is that same car with all the luxury and even many performance upgrades.  Still reliable.  It even works with some hardware that Ubuntu won't work with.  

Of course it is amazing that you will see no one at the Ultimate forums knock Ubuntu, it's a great distro, but you can come here and see people knock a great OS such as Ultimate Edition.

Edit:  BTW, Vadi speaks of people with little knowledge when obviously he is the unknowledgeable one.  This is Linux, not Windows.  Tech lesson #1 folks.... It does not matter how many programs are installed in a Linux Distro because Linux doesn't have a registry.  Each program has it's own config file that does not have to load to run the OS.  Only installed services can make a Linux OS "Bloated".  In Windows all programs leave a registry key.  The more programs that are installed=the more registry keys.  This can lead to a very large registry that has to load when Windows boots.  That's why Windows gets slower over time.  Now who has little or no knowledge Vida.  Ubuntu and Ultimate use the same exact resources so to say one is bloated means the other has to be bloated.  :)

Edit #2  Oh yeah I almost forgot.  It's ULTIMATE EDITION, not Ubuntu Ultimate.  There is NO distro called Ubuntu Ultimate.

---

### Post by Bakon Jarser on 2008-11-01
I love ultimate edition.  Can't wait for UE 2.0 to come out.  I can hardly wait for tabbed nautilus but I suppose I can hold off for a few more days.:)

---

### Post by Ptero-4 on 2008-11-09
> **Vadi said:**
> You 'burn' the iso onto the CD, put it in, and then it will boot from the CD.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I think the OP said that his PC have a CD-ROM (the one that reads but can't write to CD's) drive, hence the option of burning the iso in that PC isn't possible. But he can take the iso to other computer via a usb key or request a free ubuntu CD from shipit.

---

