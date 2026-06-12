---
title: "[GUIDE] Ubuntu 10.04 LTS on Pentium 200Mhz below 48MB RAM (32MB minimum) Server &amp; CLI"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by Panties on 2011-09-27
Editor note: *After weeks of trying to get this machine to work, I finally did it. I am an Ubuntu Noob, I hope this guide will be some of help, to those who wants their Super-Legacy machine to work with Ubuntu. (Somehow, arch linux or Gentoo, won't work under 32MB RAM)*


**_Compaq Presario 4506_**

Pentium 200 Mhz - MMX
3 ISA slots or 2 ISA slots with 1 PCI slots
16MB RAM Build-In + 32MB RAM 1 slot = 48MB
Primary IDE:
PM 3.2GB
PS CDROM


 [FONT=Constantia][SIZE=2]PCI SLOT: [/SIZE][/FONT]
  [FONT=Calibri][SIZE=3]**Wireless G(Belkin RTL8185L) - F507000**[/SIZE][/FONT]
  [FONT=Calibri][http://www.belkin.com/support/article/?lid=en&pid=f5d7000&aid=6001&scid=221](http://www.belkin.com/support/article/?lid=en&pid=f5d7000&aid=6001&scid=221)[/FONT]
[FONT=Calibri]
[/FONT]
[SIZE=2]ISA Slot[/SIZE]: 
[SIZE=3]**ISA - 3COM 3c509  10Mbps**[/SIZE]



**_Download & Burn the following  files links:  _**
  [FONT=Calibri]1.[/FONT]
  [FONT=Calibri](Recommended for system below 48MB Ram and Framebuffer issues![/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/breezy/ubuntu-5.10-install-i386.iso](http://old-releases.ubuntu.com/releases/breezy/ubuntu-5.10-install-i386.iso)[/FONT]
  
  [FONT=Calibri]2.[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-alternate-i386.iso](http://old-releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-alternate-i386.iso)[/FONT]
  [FONT=Calibri]Alternative[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/dapper/ubuntu-6.06-alternate-i386.iso](http://old-releases.ubuntu.com/releases/dapper/ubuntu-6.06-alternate-i386.iso)[/FONT]
  
  [FONT=Calibri]3.[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/hardy/ubuntu-8.04-desktop-i386.iso](http://old-releases.ubuntu.com/releases/hardy/ubuntu-8.04-desktop-i386.iso)[/FONT]
  [FONT=Calibri]Alternative[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/hardy/ubuntu-8.04.3-alternate-i386.iso](http://old-releases.ubuntu.com/releases/hardy/ubuntu-8.04.3-alternate-i386.iso)[/FONT]
  
  [FONT=Calibri]4.[/FONT]
  [FONT=Calibri](This part, is optional, but recommend using apt-get instead)[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/lucid/ubuntu-10.04-alternate-i386.iso](http://old-releases.ubuntu.com/releases/lucid/ubuntu-10.04-alternate-i386.iso)[/FONT]
  [FONT=Calibri]Alternative[/FONT]
  [FONT=Calibri][http://old-releases.ubuntu.com/releases/lucid/ubuntu-10.04.1-alternate-i386.iso](http://old-releases.ubuntu.com/releases/lucid/ubuntu-10.04.1-alternate-i386.iso)[/FONT]
  

[SIZE=4][U][B]BIOS
[/B][/U][SIZE=2]
Large Disk Access : Other / DOS (DOS recommended)
Floppy Disk: Disable(Unless you are still using Floppy Disk!)
Serial Ports/Parallel Port/SoundCard/GamingPort: Disable (Unless you need them)
PNP OS: NO
PCI bus master: Enable
32-Bit Access: Enable for CDROM and Harddisk.
BIOS Order: CDROM 1st. (able to boot up CDROM.)

The rest, is up to you.
[/SIZE][U][B]
Ubuntu 5.10[/B][/U][/SIZE]

  [SIZE=2]Upon CD boot-up, type 'server' without '' and press enter. The installer will load "Low Memory" mode. Follow the step-by-step on screen.
Partition wise, this is my personal recommendation:-
SWAP = 768MB
/ = The remaining harddisk.

Of course, if your Harddisk is bigger than mine (3.2 GB), by all means, increase the SWAP, as this system is only 48MB RAM or 32MBRAM.

During the Installation, it will Eject the CD and hit enter to reboot. [U]
Insert the CD back after the reboot! (Required to complete the installation)[/U]

Once you see the Login & Password, proceed with login.
Do this
sudo passwd
Enter password: ****
Enter root password : 123456 (we are setting your root password, using 123456 as example)

than type 'Logout'.

Now, do the following
Login: root
Password 123456

You'll be login in root enviroment. From here on, everything is done in root, to ease the installation.

_**[SIZE=4]Ubuntu 5.10 to 6.06LTS[/SIZE]**_
More info: [/SIZE]  [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
  [SIZE=2]
Since this is a delicate process as this is really an antique machine, insert the burned ISO for 6.06 Alternative version, and than type:-

apt-cdrom add
apt-get update && apt-get dist-upgrade

All is automated. At any prompt, select 'Y'.

To ensure all is proper, type:
lsb_release -a
uname -a

It should show the correct 6.06 dapper drake release. You can type these commands at any time after each distro upgrade.

**_[SIZE=4]Ubuntu 6.06LTS to 8.04LTS[/SIZE]_**
[/SIZE][SIZE=2] More Info: [/SIZE]  [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

[FONT=Calibri][http://www.youtube.com/watch?v=0O4zeuRDdHU](http://www.youtube.com/watch?v=0O4zeuRDdHU)[/FONT]
    [SIZE=2]
Thanks to the youtube uploader, I manage to install without any problem. Just like the step above, insert the 8.04LTS CD and proceed.
Here's the steps:-

apt-get remove dmsetup
apt-get cd-rom add
apt-get update
apt-get dist-upgrade && apt-get -f install && apt-get -configure -a

(Play xbox or something, hit 'Y' in most cases)

dpkg-reconfigure locales
pico /etc/kernel.img.conf

(add /usr example:-)
postinst hook /usr/bin/updategrub
postrm hook /usr/bin/updategrub

save and quit the editor by pressing "ctrl-x" and hit Y to save.

(again)
lsb_release -a
uname -a

reboot the machine.

[SIZE=4][U][B]Ubuntu 8.04 to 8.04.3 (or 8.04.4) <IMPORTANT>
[/B][/U]
[/SIZE]More info: [/SIZE]  [http://articles.slicehost.com/ubuntu-hardy](http://articles.slicehost.com/ubuntu-hardy)
  
For those who are using 3c509 network card, you are require to do this before proceeding below, as most 3c509 3com network card, are not detected yet.:-
modprobe 3c509
dhclient

You may need to do this everytime you reboot. You can load this on startup, google it up. As for now, I'm only emphazing on how to upgrade Ubuntu.

[SIZE=2]This is, by far, the most important step. In any attempt to try to upgrade directly, from 8.04 to 10.04 directly, you will face problems. What works for me, is by doing this:-

sudo pico  /etc/apt/sources.list

comment everything there, including the CD, by adding just # at the beginning for each line!

Now, for new line, just put this in:-
[/SIZE]  [FONT=Calibri]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
[/FONT]
  [FONT=Calibri]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
[/FONT]
  [FONT=Calibri]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe[/FONT]
  

[SIZE=2]Alternatively, You can delete everything there, and just add the above. Is entirely up to you. Hit Ctrl-X and 'Y' to save. Than type:-

aptitude update
aptitude safe-upgrade

Note: You can use aptitude full-upgrade, but it is risky, as you are downloading and replacing everything. Due to 3.2GB Harddrive limited space, safe-upgrade updates only upgrades what is necessary. Works well with me.

Everything should go well up to this point, reboot the machine. final steps:-
apt-get update
apt-get -f install
apt-get upgrade

If all goes well:
apt-get full-upgrade


[SIZE=4]_**8.04.04LTS to 10.04LTS <CRITICAL>**_[/SIZE]
More info: [/SIZE]  [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)
  

[SIZE=2]Up to this point, this is the hardest upgrade for me. Unfortunately, I couldn't even upgrade using alternative Cd/DVD method, as listed in [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades).

The best way that works for me, is below:-

pico /etc/apt/sources.list

Just like above, change everything to Lucid. Alternatively, I put here for you:-

[/SIZE]  [FONT=Calibri]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe
[/FONT]
  [FONT=Calibri]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe
[/FONT]
  [FONT=Calibri]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe[/FONT]
  

[SIZE=2][FONT=Verdana]Hit Ctrl-X & 'y' to save. Than type:-
aptitude update
aptitude safe-upgrade
(If you want, you can reboot here if you want to. type in release -a to be sure, than follow by below)
apt-get update
apt-get -f install
apt-get upgrade

again, if all goes well, than:-
apt-get full-upgrade


This is all the guides. You also upgrade to Ubuntu 10.10 by repeating the step above. Just make appropriate changes to sources.list and you are good to go.  This method works, as of today. I hope Ubuntu don't make changes to their site, otherwise, it is hard to determine where is their update located (URL http:// ..etc), and you'll have to update sources.list again, to get the correct [http://!]("http://%21")


That's all ubuntu noobs!

P/S: I am a noob, teaching another noob! :)


[/FONT] 
[/SIZE]

---

