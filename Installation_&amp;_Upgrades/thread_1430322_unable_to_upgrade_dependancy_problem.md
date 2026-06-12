---
title: "unable to upgrade dependancy problem"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by loosescrew on 2010-03-15
I'm unable to upgrade. Any help would be appreciated.
joe@joe-laptop:~$ sudo apt-get dist-upgrade
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.31-20-generic:
 linux-backports-modules-2.6.31-20-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.31-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-karmic-generic:
 linux-backports-modules-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-karmic-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-wireless-karmic-generic:
 linux-backports-modules-wireless-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2No apport report written because the error message indicates its a followup error from a previous failure.
                                                             No apport report written because the error message indicates its a followup error from a previous failure.
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 .6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-wireless-karmic-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-backports-modules-2.6.31-20-generic
 linux-backports-modules-karmic-generic
 linux-backports-modules-wireless-karmic-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-laptop:~$

---

### Post by zvacet on 2010-03-15
```
sudo dpkg --configure -a
```

---

### Post by loosescrew on 2010-03-15
Thanks zvacet,but i get this message
joe@joe-laptop:~$ sudo dpkg --configure -a
[sudo] password for joe: 
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.31-20-generic:
 linux-backports-modules-2.6.31-20-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.31-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-karmic-generic:
 linux-backports-modules-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-karmic-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-wireless-karmic-generic:
 linux-backports-modules-wireless-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-wireless-karmic-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
 linux-backports-modules-2.6.31-20-generic
 linux-backports-modules-karmic-generic
 linux-backports-modules-wireless-karmic-generic
joe@joe-laptop:~$

---

### Post by leorolla on 2010-03-15
Try
```
sudo dpkg-reconfigure linux-image-2.6.31-20-generic

```,then```
sudo aptitude install \
linux-image-2.6.31-20-generic \
 linux-image-generic \
 linux-generic \
 linux-backports-modules-2.6.31-20-generic- \
 linux-backports-modules-karmic-generic- \
 linux-backports-modules-wireless-karmic-generic-

```Then
```
sudo aptitude install \
  linux-backports-modules-karmic-generic \
  linux-backports-modules-wireless-karmic-generic

```

---

### Post by loosescrew on 2010-03-16
Thanks,leorolla. This is what i get. I appreciate the help.joe
joe@joe-laptop:~$ sudo dpkg-reconfigure linux-image-2.6.31-20-generic
[sudo] password for joe: 
/usr/sbin/dpkg-reconfigure: linux-image-2.6.31-20-generic is broken or not fully installed
joe@joe-laptop:~$ sudo aptitude install \
> linux-image-2.6.31-20-generic \
>  linux-image-generic \
>  linux-generic \
>  linux-backports-modules-2.6.31-20-generic- \
>  linux-backports-modules-karmic-generic- \
>  linux-backports-modules-wireless-karmic-generic-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.31-20-generic 
  linux-backports-modules-karmic-generic 
  linux-backports-modules-wireless-karmic-generic 
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.31-20-generic linux-image-generic 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4,841kB will be freed.
Writing extended state information... Done
(Reading database ... 163257 files and directories currently installed.)
Removing linux-backports-modules-wireless-karmic-generic ...
Removing linux-backports-modules-karmic-generic ...
Removing linux-backports-modules-2.6.31-20-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

joe@joe-laptop:~$ sudo aptitude install \
>   linux-backports-modules-karmic-generic \
>   linux-backports-modules-wireless-karmic-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.31-20-generic{a} 
  linux-backports-modules-karmic-generic 
  linux-backports-modules-wireless-karmic-generic 
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.31-20-generic linux-image-generic 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,565kB of archives. After unpacking 4,841kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package linux-backports-modules-2.6.31-20-generic.
(Reading database ... 163187 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.31-20-generic (from .../linux-backports-modules-2.6.31-20-generic_2.6.31-20.22_i386.deb) ...
Selecting previously deselected package linux-backports-modules-karmic-generic.
Unpacking linux-backports-modules-karmic-generic (from .../linux-backports-modules-karmic-generic_2.6.31.20.33_i386.deb) ...
Selecting previously deselected package linux-backports-modules-wireless-karmic-generic.
Unpacking linux-backports-modules-wireless-karmic-generic (from .../linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb) ...
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.31-20-generic:
 linux-backports-modules-2.6.31-20-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.31-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent conNo apport report written because the error message indicates its a followup error from a previous failure.
                                                               No apport report written because the error message indicates its a followup error from a previous failure.
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   figuration of linux-backports-modules-karmic-generic:
 linux-backports-modules-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-karmic-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-wireless-karmic-generic:
 linux-backports-modules-wireless-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-wireless-karmic-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
 linux-backports-modules-2.6.31-20-generic
 linux-backports-modules-karmic-generic
 linux-backports-modules-wireless-karmic-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash”: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.31-20-generic:
 linux-backports-modules-2.6.31-20-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.31-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-karmic-generic:
 linux-backports-modules-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-karmic-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-wireless-karmic-generic:
 linux-backports-modules-wireless-karmic-generic depends on linux-backports-modules-2.6.31-20-generic; however:
  Package linux-backports-modules-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-backports-modules-wireless-karmic-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
 linux-backports-modules-2.6.31-20-generic
 linux-backports-modules-karmic-generic
 linux-backports-modules-wireless-karmic-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

joe@joe-laptop:~$

---

### Post by leorolla on 2010-03-16
There is a problem with your Grub installation.

Unless you downgraded to Grub legacy, you should do:

```
sudo aptitude reinstall grub2
```You won't solve that problem until you can run
```
sudo update-grub
```with success.

Show us this:```

grep GRUB_CMDLINE_LINUX_DEFAULT /etc/default/grub
```

---

### Post by loosescrew on 2010-03-17
leorolla thanks. sorry for the delay. This is my daughters laptop,and i only have limited access to it. 


joe@joe-laptop:~$ grep GRUB_CMDLINE_LINUX_DEFAULT /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

---

### Post by leorolla on 2010-03-17
> **loosescrew said:**
> leorolla thanks. sorry for the delay. This is my daughters laptop,and i only have limited access to it. 


joe@joe-laptop:~$ grep GRUB_CMDLINE_LINUX_DEFAULT /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

Someone used a bad editor that saved ” instead of " for this file.

If you fix this line and repeat the steps above, it should work.

---

### Post by loosescrew on 2010-03-17
leorolla,sorry. I'm not following you. what line should i fix ? Also gedit shows two grubs files. grub and grub~.Thanks,joe

---

### Post by leorolla on 2010-03-17
> **loosescrew said:**
> leorolla,sorry. I'm not following you. what line should i fix ? Also gedit shows two grubs files. grub and grub~.Thanks,joe

```
sudo gedit /etc/default/grub

```
Replace ” by "
Save
Exit

```
sudo dpkg-reconfigure linux-image-2.6.31-20-generic

```
If no errors:

```
sudo dpkg --configure -a

```

Somebody previously edited this file and the editor was so bad that ir replaced " by ”

PS: When you copy-paste outputs of a terminal, please select these parts and click on the "#" icon, or else use [ CODE ] before and [ /CODE ] after (I am writing extra spaces otherwise you can't see it), so it looks neat as my commands above.

---

### Post by loosescrew on 2010-03-17
leorolla,Thank you.Everything is good now. I appreciate the help.```
I will work on cleaning up my posts
``` Joe

---

### Post by Arand on 2010-03-23
I'm posting here since it's the same issue:

> **loosescrew said:**
> I started a thread here .[http://ubuntuforums.org/showthread.php?t=1430322](http://ubuntuforums.org/showthread.php?t=1430322) That got me up and running but according to what i have read my grub setup is still not correct. My boot-up takes quiet awhile.
 Here is the content of /etc/default/grub       When GRUB_CMDLINE_LINUX DEFAULT="QUIET SPLASH" i'M NOT ABLE TO UPDATE GRUB. Or anything else for that matter.  
  ```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”by” 
GRUB_CMDLINE_LINUX=""


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Thanks,Joe

You need to replace the character```
”
```with the character```
"
```
i.e. replace the line```
GRUB_CMDLINE_LINUX_DEFAULT=”by”
```with the line```
GRUB_CMDLINE_LINUX_DEFAULT=""
```or if you want the default splash screen add "quiet" and "splash" like so:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and then run ```
sudo update-grub
```

- Arand

---

