---
title: "unable to remove old kernels"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2012-08-21
I used janitor, synaptic and terminal using [this method]("http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/"):

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

It is not for the pangolin, but it should work. Right? And, no, I did not remove the current 24 kernel. ;)

Here is what happened when I tried to remove those using 3 different ways.

I think there is something wrong with my system (I ran into some fan issue and upgraded thinking that it would solve that), but who know what I did wrong! HELP!

pierre2@Pierre-Vancouver:~$ dpkg --list | grep linux-image
rc  linux-image-2.6.35-28-generic                                    2.6.35-28.50                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.38-10-generic                                    2.6.38-10.46                               Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-11-generic                                    2.6.38-11.50                               Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-12-generic                                    2.6.38-12.51                               Linux kernel image for version 2.6.38 on x86/x86_64
rH  linux-image-2.6.38-13-generic                                    2.6.38-13.52                               Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-8-generic                                     2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86/x86_64
rH  linux-image-3.0.0-14-generic                                     3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-15-generic                                     3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-16-generic                                     3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-17-generic                                     3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-19-generic                                     3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-20-generic                                     3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-21-generic                                     3.0.0-21.35                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-22-generic                                     3.0.0-22.36                                Linux kernel image for version 3.0.0 on x86/x86_64
rH  linux-image-3.0.0-23-generic                                     3.0.0-23.39                                Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-24-generic                                     3.0.0-24.40                                Linux kernel image for version 3.0.0 on x86/x86_64
iF  linux-image-3.2.0-29-generic                                     3.2.0-29.46                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic                                              3.2.0.29.31                                Generic Linux kernel image
pierre2@Pierre-Vancouver:~$ sudo apt-get purge linux-image-2.6.35-28-generic
[sudo] password for pierre2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.35-28-generic* linux-image-2.6.38-13-generic linux-image-3.0.0-14-generic
  linux-image-3.0.0-15-generic linux-image-3.0.0-16-generic linux-image-3.0.0-17-generic
  linux-image-3.0.0-19-generic linux-image-3.0.0-20-generic linux-image-3.0.0-21-generic
  linux-image-3.0.0-22-generic linux-image-3.0.0-23-generic
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
17 not fully installed or removed.
After this operation, 1,167 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 280841 files and directories currently installed.)
Removing linux-image-2.6.38-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-13-generic /boot/vmlinuz-2.6.38-13-generic
update-initramfs: Deleting /boot/initrd.img-2.6.38-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-13-generic /boot/vmlinuz-2.6.38-13-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.38-13-generic.postrm line 328.
dpkg: error processing linux-image-2.6.38-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-14-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-14-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-15-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-15-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-16-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-16-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-17-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-17-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-19-generic /boot/vmlinuz-3.0.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-19-generic /boot/vmlinuz-3.0.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-19-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-20-generic /boot/vmlinuz-3.0.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-20-generic /boot/vmlinuz-3.0.0-20-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-20-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-21-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-22-generic /boot/vmlinuz-3.0.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-22-generic /boot/vmlinuz-3.0.0-22-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-22-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-23-generic /boot/vmlinuz-3.0.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-23-generic /boot/vmlinuz-3.0.0-23-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-23-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-13-generic
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-3.0.0-17-generic
 linux-image-3.0.0-19-generic
 linux-image-3.0.0-20-generic
 linux-image-3.0.0-21-generic
 linux-image-3.0.0-22-generic
 linux-image-3.0.0-23-generic
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)
pierre2@Pierre-Vancouver:~$

---

### Post by lindsay7 on 2012-08-21
Install Ubuntu Tweak and use it to get rid of the old kernels.

---

### Post by Bucky Ball on 2012-08-21
I generally just use Synaptics to locate and delete but Ubuntu Tweak would work. Might give that a try myself. ;)

---

### Post by pierreu1 on 2012-08-22
Thank you, Lindsay and Bucky!

I forgot about Tweaks. I tried and this is what I got (see attachment)! When I tried to install it anyway, it froze partly through the install! 

Any other ideas?

I think I copied a root command (i) and must have messed up enough things to make my system not work well, when I realized I had my fan was not working.

I am just thinking to reinstall everything, but I would like to keep my skype audio and video settings/drivers (because I had some initial problems with those last time). I took screen shots of the chosen settings.

Any advice?

---

### Post by hank22077 on 2012-08-22
I was given this answer for this same issue in 10.04, but it works the same with 12.04:

¨Check this [article ]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/")(video included) for the details on how to do it.¨

---

### Post by pierreu1 on 2012-08-22
> **hank22077 said:**
> I was given this answer for this same issue in 10.04, but it works the same with 12.04:

¨Check this [article ]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/")(video included) for the details on how to do it.¨

Oh! Thanks a lot! Well! I like the idea that I did not have ton do a compete removal, but as I went into synaptic it told me that I needed to do sudo dpkg-configure-a, but terminal did not know what that was! :) I am enable to do anything, install new programs,...

I think my systems is so messed up that a clean install of a new system, with a window partition to boot might resolve my fan issue and make my system run smoother! :)

Thanks!

I will p;ost in a few days with a post or not! :)

---

### Post by Bucky Ball on 2012-08-22
Give that a go. 

Notes: Delete partitions; install Windows first on its own partition using the tools in the Windows install; once Win is installed rest of disk should be free space; install Ubuntu using the free space either automatically or manually partition by choosing 'Something Else'.

If you want to share data between Win and Ubuntu you are going to need a share partition, either NTFS or FAT. This might be helpful:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

---

### Post by pierreu1 on 2012-08-22
> **Bucky Ball said:**
> Give that a go. 

Notes: Delete partitions; install Windows first on its own partition using the tools in the Windows install; once Win is installed rest of disk should be free space; install Ubuntu using the free space either automatically or manually partition by choosing 'Something Else'.

If you want to share data between Win and Ubuntu you are going to need a share partition, either NTFS or FAT. This might be helpful:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Oh! Thanks! That should prove invaluable! Thanks!

---

### Post by mcduck on 2012-08-22
> **pierreu1 said:**
> 
I think I copied a root command (i) and must have messed up enough things to make my system not work well, when I realized I had my fan was not working.

```
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```
Remove that file or rename it properly (the right extension is .list) and then run apt-get update.

> **pierreu1 said:**
> as I went into synaptic it told me that I needed to do sudo dpkg-configure-a, but terminal did not know what that was!
that would be becasue there's supposed to be a space in the command:
```
sudo dpkg-configure -a
```

---

### Post by pierreu1 on 2012-08-22
> **mcduck said:**
> ```
N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```
Remove that file or rename it properly (the right extension is .list) and then run apt-get update.


that would be becasue there's supposed to be a space in the command:
```
sudo dpkg-configure -a
```

Oh! Thanks! I tried both codes and they did not work!

N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

sudo dpkg-configure -a

Strange!

My system is really screwed! :)

---

### Post by mcduck on 2012-08-22
> **pierreu1 said:**
> Oh! Thanks! I tried both codes and they did not work!

N: Ignoring file 'google.listgksu' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

sudo dpkg-configure -a

Strange!

My system is really screwed! :)

The first one is not a command to run, it's a quote from the error messages you posted in the first post, indicating that you have somehow ended with a configuration file that has a wrong filename, messing up your package management.

If you want an actual command to fix that, try this:
```

sudo mv /etc/apt/sources.list.d/google.listgksu /etc/apt/sources.list.d/google.list && sudo apt-get update
```

---

### Post by dino99 on 2012-08-22
you can find the installed kernel(s) into: /lib/modules

so you can remove the unwanted by using:

sudo rm /lib/modules/thekernelname2remove

---

### Post by pierreu1 on 2012-08-22
> **mcduck said:**
> The first one is not a command to run, it's a quote from the error messages you posted in the first post, indicating that you have somehow ended with a configuration file that has a wrong filename, messing up your package management.

If you want an actual command to fix that, try this:
```

sudo mv /etc/apt/sources.list.d/google.listgksu /etc/apt/sources.list.d/google.list && sudo apt-get update
```

Oops! Another window guys who is learning Ubuntu! :) I am getting there, but one must be VERY patient! :) Sorry!

I uses the command to move the Google file. 

Ran sudo apt-get update and got this:

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pierre2@Pierre-Vancouver:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) testing InRelease                                     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://dl.google.com](http://dl.google.com) testing Release.gpg                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Ign [http://dl.google.com](http://dl.google.com) testing Release                                       
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [770 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) testing/non-free TranslationIndex                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise InRelease                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates InRelease                     
Err [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages                        
  404  Not Found [IP: 173.194.33.5 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_CA                    
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [161 kB]  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [377 kB] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [41.0 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [124 kB]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en       
Fetched 828 kB in 8s (99.4 kB/s)                                               
W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 173.194.33.5 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
pierre2@Pierre-Vancouver:~$ sudo dpkg --configure -a
Setting up memtest86+ (4.20-1.1ubuntu1) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Error! Bad return status for module build on kernel: 3.2.0-29-generic (i686)
Consult /var/lib/dkms/vboxhost/4.0.2/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99-21ubuntu3.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up friendly-recovery (0.2.25) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
 linux-image-3.2.0-29-generic
 linux-image-generic
 grub-pc
 friendly-recovery
 linux-generic


Boy! There seems a lot of issues! No?

Should I reboot?

---

### Post by pierreu1 on 2012-08-22
> **dino99 said:**
> you can find the installed kernel(s) into: /lib/modules

so you can remove the unwanted by using:

sudo rm /lib/modules/thekernelname2remove

I might be able to do this in synaptic now. I will try! It is easier to do as it is getting late here in Vancouver! :)

Thanks again you guys!

---

### Post by scruffyeagle on 2012-08-27
> **hank22077 said:**
> I was given this answer for this same issue in 10.04, but it works the same with 12.04:

¨Check this [article ]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/")(video included) for the details on how to do it.¨

That was a great, simple explanation. I'm going to try it. Thanks!

---

### Post by hank22077 on 2012-08-27
_**pierreu1**_: sry I wasn't  of much help; sounds like more than a kernel issue. But, some of these other posts by more experienced users will, hopefully, get u straight.

 
_**scruffyeagle:**_ you're welcome. The tutorial is for 10.04, but still works (for me) in 12LTS

---

### Post by pierreu1 on 2012-08-27
> **scruffyeagle said:**
> That was a great, simple explanation. I'm going to try it. Thanks!

Okay! Now I get an error as I open synaptic! 

dpkg-configure -a (that did not work)
dpkg--configure -a (that did not work)
dpkg --configure -a (that did work :) )

HELP!

sudo dpkg --configure -a 
[sudo] password for pierre2: 
Setting up memtest86+ (4.20-1.1ubuntu1) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Error! Bad return status for module build on kernel: 3.2.0-29-generic (i686)
Consult /var/lib/dkms/vboxhost/4.0.2/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99-21ubuntu3.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up friendly-recovery (0.2.25) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
 linux-image-3.2.0-29-generic
 linux-image-generic
 grub-pc
 friendly-recovery
 linux-generic

---

### Post by scruffyeagle on 2012-09-09
> **hank22077 said:**
> _**pierreu1**_: sry I wasn't  of much help; sounds like more than a kernel issue. But, some of these other posts by more experienced users will, hopefully, get u straight.

 
_**scruffyeagle:**_ you're welcome. The tutorial is for 10.04, but still works (for me) in 12LTS

Update: I tried it, and it worked like a charm. Thanks again!

---

### Post by hank22077 on 2012-09-10
> **scruffyeagle said:**
> Update: I tried it, and it worked like a charm. Thanks again!

scruffyeagle: You're very welcome. Figured it'd work same as in 10.04.

> **pierreu1 said:**
> Okay! Now I get an error as I open synaptic! 

dpkg-configure -a (that did not work)
dpkg--configure -a (that did not work)
dpkg --configure -a (that did work :smile: )

HELP!

sudo dpkg --configure -a 
[sudo] password for pierre2: 
Setting up memtest86+ (4.20-1.1ubuntu1) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
Error! Bad return status for module build on kernel: 3.2.0-29-generic (i686)
Consult /var/lib/dkms/vboxhost/4.0.2/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99-21ubuntu3.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up friendly-recovery (0.2.25) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
 linux-image-3.2.0-29-generic
 linux-image-generic
 grub-pc
 friendly-recovery
 linux-generic

pierreu1: Sorry, again, I couldn't help you. I'm just responding to give you a little 'bump' to keep this up top where maybe a more experienced person can see it and help you out.

I was told that if you post updates it's not actually 'bumping' your thread; and it gives a more recent spot in the forum, so hopefully you get the advise you need.

---

### Post by hank22077 on 2012-09-10
Oops! 2 posts anyway:

You posted:
> **pierreu1 said:**
> dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 memtest86+
 ubuntu-standard
 linux-image-3.2.0-29-generic
 linux-image-generic
 grub-pc
 friendly-recovery
 linux-generic
towards the end of your last post...

Are you SURE your updates are occurring correctly?
I've had issues where I've ran updates and it would tell me that my last update had failed or I needed to run a partial update.
Or, perhaps you accidentally erased a newer kernel and kept an older one. 

What results in your Update Manager?

---

### Post by Bucky Ball on 2012-09-11
> **hank22077 said:**
> 
pierreu1: Sorry, again, I couldn't help you. I'm just responding to give you a little 'bump' to keep this up top where maybe a more experienced person can see it and help you out.

I was told that if you post updates it's not actually 'bumping' your thread; and it gives a more recent spot in the forum, so hopefully you get the advise you need.

Posting updates is encouraged and necessary to keep helpers up to date; the fact that it bumps the thread to the top of the list should be seen as an added benefit. Posting for the sake of bumping a thread whilst adding no new information is not encouraged.

To make it clear; the original OP bumping every five minutes is definitely NOT encouraged, but a bump once every twenty four hours or more is fine and acceptable. 

In other words, the original poster is quite free to bump this whenever they want to get things going again at this point, if they so choose. Often a thread dwindles for the simple reason that no-one has any new information, breakthroughs, solutions, or ideas to add. That looks to be the case here. ;)

---

### Post by hank22077 on 2012-09-11
> **Bucky Ball said:**
> Posting updates is encouraged and necessary to keep helpers up to date; the fact that it bumps the thread to the top of the list should be seen as an added benefit. Posting for the sake of bumping a thread whilst adding no new information is not encouraged.

To make it clear; the original OP bumping every five minutes is definitely NOT encouraged, but a bump once every twenty four hours or more is fine and acceptable. 

In other words, the original poster is quite free to bump this whenever they want to get things going again at this point, if they so choose. Often a thread dwindles for the simple reason that no-one has any new information, breakthroughs, solutions, or ideas to add. That looks to be the case here. ;)

Understood,

wasn't tryin to cause trouble; just was notified scruffyeagle had thanked me, and was tryin to explain your point to **pierreu1, **to the best of my ability.

Apologies.

Btw, does my second post, seem in anyway informative?; cuz although I haven't had as much trouble as **pierreu1,** the issue in my post has left me perplexed a time or two.

Again, apologies, if my 'bump' was inappropriate; just wanted to respond to scruffyeagle, and encourage **pierreu1. **I've learned that ofttimes folks don't close, or 'solve' thier threads, or let those of us tryin to give advice know if or what they did to get a fix.

---

### Post by Bucky Ball on 2012-09-11
All good. ;)

---

