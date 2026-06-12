---
title: "HELP PLEASE!!! dpkg was interrupted,"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by jorje_villafan on 2008-02-29
**I tried to run add/update and synaptic package manager and I get this:**

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

[B]So I tried the  'dpkg --configure -a' and I get this:
[/B]
root@jonathan:/home/jonathan# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.22-14-rt (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: subprocess post-installation script returned error exit status 1

I can't even use 'apt-get'

I checked some other threads but couldn't find the solution. Does anyone have any ideas on how to fix this?

Thanks in advance.

---

### Post by Pumalite on 2008-02-29
sudo apt-get install -f
Post the output

---

### Post by forestpixie on 2008-02-29
you need to use sudo with apt-get, aptitude 

do ```
sudo dpkg --configure -a
```

didn't see you logged in as root though

---

### Post by jorje_villafan on 2008-02-29
**Pumalite. I tried your code and I get this:**

root@jonathan:/home/jonathan# sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

[B]
Forestpixie, I tried yours and I get:[/B]

root@jonathan:/home/jonathan# sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.22-14-rt (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by Pumalite on 2008-02-29
Post the output of (if you are root):
apt-get update

---

### Post by jorje_villafan on 2008-02-29
**Pumalite are the results:**

root@jonathan:/home/jonathan# apt-get update
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/multiverse Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/universe Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 44.2kB in 3s (13.4kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Pumalite on 2008-02-29
What were you doing before this happened?

---

### Post by jorje_villafan on 2008-02-29
Well, yesterday I got a notification for updates so I installed them. Before that I was having problems with my computer not dealing with files right. So I enabled the extra stuff in synaptic, Hoping that would fix it. It did fix it and everything was fine 'til I tried to open synaptic.

---

### Post by Pumalite on 2008-02-29
What do you mean by 'it did fix it'?

---

### Post by jorje_villafan on 2008-02-29
Here are some examples of my computer not dealing with file s properly:

-Right clicking on a .tar.gz  there was no option to extract here.

-Double clicking on any type of file type I would return an error or I would have to go find a suitable app. to open the file with. 

-Icons for all the files were all changed to blank white rectangles or little pages with  "writing".

All of that happen when I accidentally stopped the nautilus process. I reinstalled nautilus but it didn't fix it. I even reinstalled ubuntu. and it didn't work.

So I tried the updates it fixed those issues perfectly.

---

### Post by Pumalite on 2008-02-29
I'm trying to figure out what file we need to force remove before you can get your apt-get back

---

### Post by jorje_villafan on 2008-02-29
Thanks a bunch for helping me out. I am fairly new to ubuntu. I'll check back in a bit.

---

### Post by ellalan on 2008-02-29
Hi
I did have the same error few days ago and I did what forestpixie had told,
but from your post I noticed that you ignored the spaces in between the words.
In terminal enter "sudo  dpkg  --configure  -a",
                            sudo spacedpkgspace--configurespace-a.

I hope this helps you.

---

### Post by jorje_villafan on 2008-02-29
**ellalan, I tried with the spaces and got:**

jonathan@jonathan:~$ sudo dpkg --configure -a
[sudo] password for jonathan:
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.22-14-rt (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-rt
dpkg: subprocess post-installation script returned error exit status 1
jonathan@jonathan:~$ 

I am actually thinking about just backing everything up and reinstalling.

---

