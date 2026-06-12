---
title: "ubuntu 10.11 to ubuntu 12.04 issues"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by tsukune1791 on 2012-04-27
Hello people, im haveing some issues with my newly updated computer. i sat through the like 5 hr update progress and whatnot, but i got a couple of error and didnt really catch them. but~ after restarting and logging in to my ubuntu, i find that my desktop wouldnt load properly and i got a couple of... i cant remember the na,e of the program but it is for reporting bug. i tried that but it wont connect saying something about checking my internet connection, but its just fine. well anyway i tried "sudo apt-get update" and that didnt work reading a couple errors, that i will post in a sec, and decided to surf the interwebz to see if i could find anything that would help and read that i should try to force install "sudo apt-get -f install" and got the following, fairly similer to what i got previously > dustin@marceau-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-24-generic; however:
  Package linux-image-3.2.0-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however:
  Package linux-image-generic is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-generic
 linux-generic
 initramfs-tools
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
and im now at a loss, i can still log in my gnome and ubuntu 2d, only ubuntu doesnt load right. can some one please help me? i really appreiciat it.
-edit-
p.s.
i could think of another place to post this so, i appoligize if im in the wrong forum

---

### Post by jadtech on 2012-04-27
your upgrade is incomplete something went wrong  one file is all it takes maybe couldn't down load and started a chain reaction either I believe you need to continue the upgrade ..

---

### Post by cookiecruncher on 2012-04-27
I didn't want to create a new topic but I cannot find the file '/var/log/messages'. Can someone help me out with the 12.04 equivalent?

Thanks

EDIT.  Nevermind, Google did its bit for the day.

---

### Post by tsukune1791 on 2012-04-27
okay well, ive ran the following and got the same errors:
> 
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade

and this is the newst readout
> 
dustin@marceau-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk python-apport python-problem-report
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 238 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main python-problem-report all 2.0.1-0ubuntu7 [9,550 B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main python-apport all 2.0.1-0ubuntu7 [78.2 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main apport all 2.0.1-0ubuntu7 [141 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main apport-gtk all 2.0.1-0ubuntu7 [9,306 B]
Fetched 238 kB in 2s (80.8 kB/s)      
(Reading database ... 259018 files and directories currently installed.)
Preparing to replace python-problem-report 2.0.1-0ubuntu6 (using .../python-problem-report_2.0.1-0ubuntu7_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 2.0.1-0ubuntu6 (using .../python-apport_2.0.1-0ubuntu7_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 2.0.1-0ubuntu6 (using .../apport_2.0.1-0ubuntu7_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace apport-gtk 2.0.1-0ubuntu6 (using .../apport-gtk_2.0.1-0ubuntu7_all.deb) ...
Unpacking replacement apport-gtk ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-24-generic; however:
  Package linux-image-3.2.0-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up python-problem-report (2.0.1-0ubuntu7) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Setting up python-apport (2.0.1-0ubuntu7) ...
Setting up apport (2.0.1-0ubuntu7) ...
apport start/running
Setting up apport-gtk (2.0.1-0ubuntu7) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-generic
 linux-generic
 initramfs-tools
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by BicyclerBoy on 2012-04-27
Have just updated to 12.04 with similar & more problems..

Try in terminal
sudo update-initramfs -u

---

### Post by tsukune1791 on 2012-04-27
> **BicyclerBoy said:**
> Have just updated to 12.04 with similar & more problems..

Try in terminal
sudo update-initramfs -u
thanks for you input but i got this error
> 
dustin@marceau-laptop:~$ sudo update-initramfs -u
[sudo] password for dustin: 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dustin@marceau-laptop:~$ 


i think the "fatal: no images have been defined." is the catcher, but i have no idea how to fix this

---

### Post by BicyclerBoy on 2012-04-27
Yes there is no existing boot image (found) to update. But this is due to initramfs-tools package error.

sudo dpkg --configure -a

Are you still using lilo instead of grub ?

---

### Post by tsukune1791 on 2012-04-27
> **BicyclerBoy said:**
> Yes there is no existing boot image (found) to update. But this is due to initramfs-tools package error.

sudo dpkg --configure -a

Are you still using lilo instead of grub ?
idk what lilo is but yeah im not in grub im on my gnome thingy butill try running that real quick and post the readout if anything comes up
> 
dustin@marceau-laptop:~$ sudo dpkg --configure -a
[sudo] password for dustin: 
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-24-generic; however:
  Package linux-image-3.2.0-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
Fatal: No images have been defined.
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-generic
 linux-generic
 initramfs-tools
dustin@marceau-laptop:~$ 
same thing damn this id irritaing
i also tried running it in grub but grub wouldnt let me connect to the network it hung after running fsck. i tried a few times so idk

---

### Post by BicyclerBoy on 2012-04-27
There are some risky stuff that could work but I've no personal experience..so I don't want to suggest..


A save optiuon could be
run synaptic package manager (install it if necessary)
find the linux-image-generic & reinstall

or in terminal
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install linux-image-generic

---

### Post by tsukune1791 on 2012-04-27
> **BicyclerBoy said:**
> There are some risky stuff that could work but I've no personal experience..so I don't want to suggest..


A save optiuon could be
run synaptic package manager (install it if necessary)
find the linux-image-generic & reinstall

or in terminal
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install linux-image-generic
okay i got into synaptic and found the linux package mentioned and got this after it tried twice to reinstall it
> E: linux-image-3.2.0-24-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: initramfs-tools: subprocess installed post-installation script returned error exit status 1


---

### Post by BicyclerBoy on 2012-04-27
Another save option would be:
reboot & (in grub) select the previous kernel image.
remove the package linux-image-3.2.0-24-generic

Note: 
you must be running the previous kernel (if you can)
you must remove the package by direct name & **NOT the meta package** linux-image-generic

reboot & then run updates...

---

### Post by tsukune1791 on 2012-04-27
> **BicyclerBoy said:**
> Another save option would be:
reboot & (in grub) select the previous kernel image.
remove the package linux-image-3.2.0-24-generic

Note: 
you must be running the previous kernel (if you can)
you must remove the package by direct name & **NOT the meta package** linux-image-generic

reboot & then run updates...

okay i remove the package name "linux-image-3.2.0-24-generic" in my pervious kernal (i think it 3.0.x or something like that) right?

---

### Post by BicyclerBoy on 2012-04-27
Yes, you reboot into a previous kernel & then remove the problem package.

The reboot & run updates ..
Hopefully it fixes itself..

---

### Post by tsukune1791 on 2012-04-27
> **BicyclerBoy said:**
> Yes, you reboot into a previous kernel & then remove the problem package.

The reboot & run updates ..
Hopefully it fixes itself..
i guess its not even there i got the error that theres no such file or drectory O.o now im super confused

---

### Post by BicyclerBoy on 2012-04-27
Is this in synaptic package manager or using apt-get ?

I did not mean delete the file by name in terminal...
I meant use the full package name in synaptic or apt-get (& not the meta package name).

(The meta package linux-image-generic points to the latest kernel package)

sudo apt-get purge linux-image-3.2.0-24-generic

**BUT you must be** in the previous kernel
You can check the current kernel with
uname -r

---

### Post by tsukune1791 on 2012-04-27
okay well i did it, the purge, and tried to reboot and what not and *faceplams* find out the i cant log into the thing i just deleted so, i ran sudo apt-get install linux-image-3.2.0-24-generic and it looks like its hung idk ill post the readout
> dustin@marceau-laptop:~$ sudo apt-get install linux-image-3.2.0-24-generic
[sudo] password for dustin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-24-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/37.7 MB of archives.
After this operation, 112 MB of additional disk space will be used.
Selecting previously unselected package linux-image-3.2.0-24-generic.
(Reading database ... 254643 files and directories currently installed.)
Unpacking linux-image-3.2.0-24-generic (from .../linux-image-3.2.0-24-generic_3.2.0-24.37_i386.deb) ...
Done.
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic

and hasnt moved for about two minutes

---

### Post by BicyclerBoy on 2012-04-28
Whoops important step missing..
When you removed the latest kernel image package you have to:
- update-grub (so latest image is removed form boot options)
- reboot & pick the previous kernel image just as before..

If you reboot without doing either of above, grub picks the most recent image listed & then finds it is missing..

1. reboot into previous kernel image
2. purge the latest kernel image
3. sudo update-initramfs -u
4. sudo update-grub
5. reboot letting grub run the latest default..
6. run update manager/synaptic or apt-get etc..

---

### Post by naki78 on 2012-05-01
Hi all, to resolve the trouble on linux-image-3.2.0-24-generic please do sudo update-initramfs -c -k 3.2.0-24-generic

---

