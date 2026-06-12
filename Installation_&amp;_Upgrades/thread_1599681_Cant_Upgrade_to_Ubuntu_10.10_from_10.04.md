---
title: "Cant Upgrade to Ubuntu 10.10 from 10.04"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by tendaic on 2010-10-18
I am running Ubuntu 10.04LTS but when I attempted to upgrade to 10.10 I got an error message with text like "Failed to fetch cdrom://ubuntu 10.04LTS......please use apt-cdrom to make this CD-ROM recognised by APT.apt-get update cannot be used to add new CD-ROMS. Problem number one is that I am a complete noob and dont know how to use the command line.Secondly I am using a Samsung N130 netbook with no CD ROM so this leaves me confused. Please help on how I can upgrade, I have the .iso file for ubuntu 10.10 so advice if it is possible to upgrade using this image file

---

### Post by garvinrick4 on 2010-10-18
> **tendaic said:**
> I am running Ubuntu 10.04LTS but when I attempted to upgrade to 10.10 I got an error message with text like "Failed to fetch cdrom://ubuntu 10.04LTS......please use apt-cdrom to make this CD-ROM recognised by APT.apt-get update cannot be used to add new CD-ROMS. Problem number one is that I am a complete noob and dont know how to use the command line.Secondly I am using a Samsung N130 netbook with no CD ROM so this leaves me confused. Please help on how I can upgrade, I have the .iso file for ubuntu 10.10 so advice if it is possible to upgrade using this image file
You have an internet connection I do imagine. Copy and paste this in a terminal and it will change your sources.list and upgrade to maverick. 
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```
You can do a fresh install by taking a usb flash drive and using startup disk creator and making a Live USB out of the .iso you have and booting it and installing.
 Other than that I have no more salutions to upgrading, different styles of dist-upgrades but all to same ends. But that is all I have seen.
Startup disk creator:
```
sudo apt-get install usb-creator-gtk
```

---

### Post by h.vinay on 2010-10-18
Hi garvinrick4,
  
I have created live USB from ubuntu-10.10-desktop-i386.iso. After  booting with Live USB i didn't find the option for 'upgrading', there is  only 'install' option. I guess this will wipe out my old version(Ubuntu 10.04). I don't want to do a fresh install as i have lot of softwares installed and settings changed. I don't want to upgrade through network as it takes lot of time and as iso file is also present in my local disk.

Please let me know how to go ahead?

Thanks,
Vinay

---

### Post by garvinrick4 on 2010-10-18
I know no way of upgrading with a .iso file or burned cd or USB without it being a fresh install. After a while you get so you can do a clean install pretty darn quick. I always keep a seperate /home so do not have to worry about personals and keep back-ups anyway. Keep my Firefox browser bookmarks backed up in organize bookmarks in Firefox. Install in same partition and then do a:
```
sudo apt-get install ubuntu-restricted-extras gparted libdvdcss2
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Then do my panels and edit menus and go thru preferences while all that is going on. Go's pretty darn quick and fresh is so much nicer than upgraded. Just a personal opinion.

---

### Post by h.vinay on 2010-10-25
I don't have /home as seperate partition currently, can you please let me know if i can do the following and do fresh install with out losing any settings
1) Backup current /home directory
2) Create partition with mount point /home
3) After restarting, copy contents of backed up /home to newly created /home

I have 3 users now, would i have to create the users again? will there be issues with this?

---

