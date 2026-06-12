---
title: "Using Unetbootin (error mnt directory out of space)"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by Joe_Linux on 2020-04-25
Using Unetbootin to make a live usb (20.04) with persistence. It asks me to mount the usb so I did 
```

joe@joe-GA-78LMT-USB3:~$ sudo mount /dev/sdb2 /mnt
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ 

```

Then I am told my mnt directory is out of space. Any help would be appreciated. I am not very proficient with the CLI if possible step by step. Thank you

---

### Post by sudodus on 2020-04-25
1. What is the size of your USB pendrive?

2. What operating system are you running, when you use Unetbootin?

- If Ubuntu (or Debian) I would recommend [mkusb](https://help.ubuntu.com/community/mkusb).

- If Windows I would recommend [Rufus](http://rufus.ie).

- If MacOS, I think we should continue trying with [Unetbootin](https://unetbootin.github.io/) until it works.

[hr][/hr]
**mkusb** and **Rufus** can manage partitions for persistence, where only the drive size is limiting the size. But you are restricted to 4 GB, the maximum file size in a FAT32 file system, when you use **Unetbootin**.

---

### Post by Joe_Linux on 2020-04-25
1) 32 GB 
2) Ubuntu 20.04.4 
    5.3.0-46-generic kernel

---

### Post by sudodus on 2020-04-25
With a 32 GB pendrive and Ubuntu (all current versions), I suggest that you install and use mkusb.

If you run standard Ubuntu live, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```

sudo add-apt-repository universe  # only for standard Ubuntu live

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi

```

There are more details at this link: [help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Joe_Linux on 2020-04-25
```

joe@joe-GA-78LMT-USB3:~$ sudo mount /dev/sdb2 /mnt
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ sudo add-apt-repository universe  # only for standard Ubuntu live
[sudo] password for joe: 
'universe' distribution component is already enabled for all sources.
joe@joe-GA-78LMT-USB3:~$ sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
 
 More info: https://launchpad.net/~mkusb/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://linux.teamviewer.com/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:3 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu bionic InRelease          
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:6 http://ppa.launchpad.net/mkusb/ppa/ubuntu bionic InRelease               
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:8 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.7 kB]
Ign:9 http://linux.dropbox.com/ubuntu bionic InRelease                         
Get:10 http://linux.dropbox.com/ubuntu bionic Release [6,600 B]                
Get:11 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [669 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [915 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [301 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,968 B]
Fetched 2,511 kB in 3s (930 kB/s)                                            
Reading package lists... Done
joe@joe-GA-78LMT-USB3:~$ sudo apt-get update
Hit:1 http://linux.teamviewer.com/deb stable InRelease
Ign:2 http://linux.dropbox.com/ubuntu bionic InRelease                         
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Get:6 http://linux.dropbox.com/ubuntu bionic Release [6,600 B]                 
Hit:7 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu bionic InRelease          
Hit:8 http://ppa.launchpad.net/mkusb/ppa/ubuntu bionic InRelease               
Hit:10 http://security.ubuntu.com/ubuntu bionic-security InRelease             
Fetched 6,600 B in 2s (4,259 B/s)
Reading package lists... Done
joe@joe-GA-78LMT-USB3:~$ sudo apt-get install mkusb mkusb-nox usb-pack-efi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mkusb is already the newest version (12.4.5-1ubuntu5).
mkusb-nox is already the newest version (12.4.5-1ubuntu5).
usb-pack-efi is already the newest version (12.4.5-1ubuntu5).
The following packages were automatically installed and are no longer required:
  libllvm7 libllvm8
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by sudodus on 2020-04-25
Good, you have installed mkusb. Now you can use it, either via the graphical user interface, or from the command line.

If you like the command line, it is convenient to change directory to where you have your iso file(s), for example

```

cd ~/Downloads
dus ubuntu-20.04-desktop-amd64.iso

```

and then continue with the graphical interface of dus (mkusb-dus) ...

---

