---
title: "Purge Errors for Updating 14.04"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by bonzo2 on 2016-03-16
Greetings,:D

 

 When updating my 14.04 LTS system files, I get a message to clean unused files boot files. My boot folder is 231.1 MB and is 100% full.  

 I tried *apt-get purge *and ended up with a host of errors, shown below. Could someone explain what this means and how to resolve it?  Increasing the size of my boot folder seems warranted, but I'd like to resolve this issue first. I've been using Ubuntu for over a year but still consider myself a Linux novice.

```
**sudo apt-get purge **
    
  Reading package lists... Done 
  Building dependency tree        
  Reading state information... Done 
  0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
  6 not fully installed or removed. 
  After this operation, 0 B of additional disk space will be used. 
  Setting up linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ... 
  run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
  run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
  update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic 
   
  gzip: stdout: No space left on device 
  E: mkinitramfs failure cpio 141 gzip 1 
  update-initramfs: failed for /boot/initrd.img-3.13.0-83-generic with 1. 
  run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
  dpkg: error processing package linux-image-extra-3.13.0-83-generic (--configure): 
   subprocess installed post-installation script returned error exit status 1 
  dpkg: dependency problems prevent configuration of linux-image-generic: 
   linux-image-generic depends on linux-image-extra-3.13.0-83-generic; however: 
    Package linux-image-extra-3.13.0-83-generic is not configured yet. 
   
  dpkg: error processing package linux-image-generic (--configure): 
   dependency problems - leaving unconfigured 
  dpkg: dependency problems prevent configuration of linux-generic: 
   linux-generic depends on linux-image-generic (= 3.13.0.83.89); however: 
    Package linux-image-generic is not configured yet. 
   
  dpkg: error processing package linux-generic (--configure): 
   dependency problems - leaving unconfigured 
  dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-83-generic: 
   linux-signed-image-3.13.0-83-generic depends on linux-image-extra-3.13.0-83-generic (= 3.13.0-83.127); however: 
    Package linux-image-extra-3.13.0-83-generic is not configured yet. 
   
  dpkg: error processing package linux-signed-image-3.13.0-83-generic (--configure): 
   dependency problems - leNo apport report written because the error message indicates its a followup error from a previous failure. 
                                                     No apport report written because the error message indicates its a followup error from a previous failure. 
                                                                               No apport report written because MaxReports is reached already 
                                                             No apport report written because MaxReports is reached already 
                                           No apport report written because MaxReports is reached already 
                         aving unconfigured 
  dpkg: dependency problems prevent configuration of linux-signed-image-generic: 
   linux-signed-image-generic depends on linux-signed-image-3.13.0-83-generic; however: 
    Package linux-signed-image-3.13.0-83-generic is not configured yet. 
   
  dpkg: error processing package linux-signed-image-generic (--configure): 
   dependency problems - leaving unconfigured 
  dpkg: dependency problems prevent configuration of linux-signed-generic: 
   linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.83.89); however: 
    Package linux-signed-image-generic is not configured yet. 
   
  dpkg: error processing package linux-signed-generic (--configure): 
   dependency problems - leaving unconfigured 
  Errors were encountered while processing: 
   linux-image-extra-3.13.0-83-generic 
   linux-image-generic 
   linux-generic 
   linux-signed-image-3.13.0-83-generic 
   linux-signed-image-generic 
   linux-signed-generic 
  E: Sub-process /usr/bin/dpkg returned an error code (1) 
  

```
   

 [LEFT] 
[/LEFT]
 [LEFT] Thanks! :-)[/LEFT]
 [LEFT]Bonzo
[/LEFT]

---

### Post by ian-weisser on 2016-03-16
A partition seems to be full.

When apt starts, it checks that the current package state matches your desired package state.
If any package actions have not been done, apt tries to do them.
New actions are queued until the older actions complete.

In this case 'apt tries to do them' fails (out of space), so the entire queue aborts.

Next time you start apt, the package actions *still* aren't complete, so the failure occurs again.

It might be very easy to fix.

Please show us the complete output of the command:
```
df
```

---

### Post by grahammechanical on 2016-03-17
Is it correct to run apt-get purge without a packaged being named to be purged?

See heading - Removal commands - section 1; 2; 3

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards

---

### Post by ajgreeny on 2016-03-17
> **grahammechanical said:**
> Is it correct to run apt-get purge without a packaged being named to be purged?

See heading - Removal commands - section 1; 2; 3

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards
Exactly the point I was about to make when I read the first post.

I don't believe that command will do anything without a target package, but that has nothing to do with the possibility of the /boot partition being full so it would be very helpful to see the output of that command, though add the -h option to make it more understandable in human terms, showing space as M or G rather than kilobytes.
```
df -h
```
Also show us the output of ```
ls /boot | grep vmlinuz
```to see how many kernels are installed at the moment; we can then help you remove the unneeded ones.  You could start by running command ```
sudo apt-get autoremove

```which can remove all but the two most recent versions if there is space; if you are already getting those errors the command will probably not work and we shall have to start by manually removing one or two kernels, then using autoremove.

---

### Post by bonzo2 on 2016-03-28
Hey Ian-Weisser, Grahammechanical, and Ajgreeny:
 

 Thank you for jumping in on this thread. Apologies for the belated reply. I couldn't access my Ubuntu account to reply. I've provided below what I believe to be the requested output. I'm continuing to get alerts that my partition is full but don't know how to resolve it. Suggestions?
 
Thanks again!
 Bonzo

                   
 ```
df -h 

 Filesystem                   Size  Used Avail Use% Mounted on 
 udev                         7.8G  4.0K  7.8G   1% /dev 
 tmpfs                        1.6G  1.1M  1.6G   1% /run 
 /dev/mapper/ubuntu--vg-root  901G  581G  275G  68% / 
 none                         4.0K     0  4.0K   0% /sys/fs/cgroup 
 none                         5.0M     0  5.0M   0% /run/lock 
 none                         7.8G  288K  7.8G   1% /run/shm 
 none                         100M   48K  100M   1% /run/user 
 /dev/sda1                    236M  217M  6.4M  98% /boot 
 /home/abc/.Private           901G  581G  275G  68% /home/abc 
 


 ls /boot | grep vmlinuz

 abc@123:~$ ls /boot | grep vmlinuz 
 vmlinuz-3.13.0-74-generic 
 vmlinuz-3.13.0-74-generic.efi.signed 
 vmlinuz-3.13.0-76-generic 
 vmlinuz-3.13.0-76-generic.efi.signed 
 vmlinuz-3.13.0-77-generic 
 vmlinuz-3.13.0-79-generic 
 vmlinuz-3.13.0-79-generic.efi.signed 
 vmlinuz-3.13.0-83-generic
 

 

sudo apt-get autoremove
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 6 not fully installed or removed. 
 After this operation, 0 B of additional disk space will be used. 
 Setting up linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ... 
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic 
  
 gzip: stdout: No space left on device 
 E: mkinitramfs failure cpio 141 gzip 1 
 update-initramfs: failed for /boot/initrd.img-3.13.0-83-generic with 1. 
 run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
 dpkg: error processing package linux-image-extra-3.13.0-83-generic (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of linux-image-generic: 
  linux-image-generic depends on linux-image-extra-3.13.0-83-generic; however: 
   Package linux-image-extra-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-generic: 
  linux-generic depends on linux-image-generic (= 3.13.0.83.89); however: 
   Package linux-image-generic is not configured yet. 
  
 dpkg: error processing package linux-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-83-generic: 
  linux-signed-image-3.13.0-83-generic depends on linux-image-extra-3.13.0-83-generic (= 3.13.0-83.127); however: 
   Package linux-imageNo apport report written because the error message indicates its a followup error from a previous failure. 
                                                No apport report written because the error message indicates its a followup error from a previous failure. 
                                                                          No apport report written because MaxReports is reached already 
                                                        No apport report written because MaxReports is reached already 
                                      No apport report written because MaxReports is reached already 
                    -extra-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-image-3.13.0-83-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-image-generic: 
  linux-signed-image-generic depends on linux-signed-image-3.13.0-83-generic; however: 
   Package linux-signed-image-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-generic: 
  linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.83.89); however: 
   Package linux-signed-image-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-generic (--configure): 
  dependency problems - leaving unconfigured 
 E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Ouch !

You do not have the head room for the package manager to operate :
> 
gzip: stdout: No space left on device 
E: mkinitramfs failure cpio 141 gzip 1 

Let's prepare to drop down to a lower level to remove the extraneous kernels; 
Post back - Between code tags - the output of terminal commands:
```

uname -r
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
so we know what kernels are installed and which is the booting kernel.

[INDENT][INDENT]give the package manager a helping hand
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Hi Bashing-OM
  

  "Ouch!" is how I feel! :confused:

Thanks for your reply.  I'm really lost but believe I've provided the outputs you requested. The &#8220;problem&#8221; I have with Ubuntu is that it's been so reliable that I haven't become the expert I was with Windows, which presented MORE than ample opportunities to trouble shoot.

  

  PS: How do I properly format outputs so they stand out from the narrative in my posts?
  

  Thanks,
  Bonzo
 

  **uname -r**

3.13.0-83-generic


**dpkg -l | grep linux- **
 
```

ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 iU  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-76                               3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-76-generic                       3.13.0-76.120                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-76-generic                         3.13.0-76.120                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-76-generic                   3.13.0-76.120                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iF  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iU  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 iU  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 rc  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-66-generic                  3.13.0-66.108                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-73-generic                  3.13.0-73.116                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-74-generic                  3.13.0-74.118                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-76-generic                  3.13.0-76.120                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-77-generic                  3.13.0-77.121                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by ajgreeny on 2016-03-28
It look as as if you installed using either encryption or LVM partitioning, neither of which I have any experience of, so am unable to specifically comment about.

However, as I suspected, the /boot partition of your installation is full, at 98% so there is no room for any further kernels to be installed.  Unfortunately when using encryption or LVM the system automatically makes a separate /boot partition, but of only 236MB, which is too small in reality.

The solution for you is to remove some of the older kernels.
This is normally carried out by running command ```
sudo apt-get autoremove
``` which removes all except the two most recent kernels.
That command will probably not be successful as there is insufficient headroom in the system so we may have to get down and dirty and use ```
sudo dpkg -P linux-image-3.13.0-{74,76,77}-generic
```.
That should remove three of your old kernels, and if no errors are shown from this you can confirm that it has been successful with the df -h command.  Look for the line ending with /boot which will hopefully now show something like 25 - 30%, not 98%.
You should then make sure that you either run the autoremove command I show above regularly, and always after seeing a new kernel in updates, or manually remove the old kernels if you prefer; most users simply autoremove them.

Good luck.

---

### Post by bonzo2 on 2016-03-28
Hi AJgreeny:

Thanks for jumping back in here. Yes, during the 14.04 installation I chose to encrypt the drive. I don't think either of the commands suggested in your reply were successful. Have I any other options? [B]:D
[/B]
Here are the outputs:

Thanks,
Bonzo

[B]sudo apt-get autoremove
[/B]
                        Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded. 
 6 not fully installed or removed. 
 After this operation, 0 B of additional disk space will be used. 
 Setting up linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ... 
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic 
  
 gzip: stdout: No space left on device 
 E: mkinitramfs failure cpio 141 gzip 1 
 update-initramfs: failed for /boot/initrd.img-3.13.0-83-generic with 1. 
 run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
 dpkg: error processing package linux-image-extra-3.13.0-83-generic (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of linux-image-generic: 
  linux-image-generic depends on linux-image-extra-3.13.0-83-generic; however: 
   Package linux-image-extra-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-generic: 
  linux-generic depends on linux-image-generic (= 3.13.0.83.89); however: 
   Package linux-image-generic is not configured yet. 
  
 dpkg: error processing package linux-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-83-generic: 
  linux-signed-image-3.13.0-83-generic depends on linux-image-extra-3.13.0-83-generic (= 3.13.0-83.127); however: 
   Package linux-image-extra-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-image-3.13.0-83-generic (--configure): 
  dependency problems - leNo apport report written because the error message indicates its a followup error from a previous failure. 
                                                    No apport report written because the error message indicates its a followup error from a previous failure. 
                                                                              No apport report written because MaxReports is reached already 
                                                            No apport report written because MaxReports is reached already 
                                          No apport report written because MaxReports is reached already 
                        aving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-image-generic: 
  linux-signed-image-generic depends on linux-signed-image-3.13.0-83-generic; however: 
   Package linux-signed-image-3.13.0-83-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-signed-generic: 
  linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.83.89); however: 
   Package linux-signed-image-generic is not configured yet. 
  
 dpkg: error processing package linux-signed-generic (--configure): 
  dependency problems - leaving unconfigured 
 Errors were encountered while processing: 
  linux-image-extra-3.13.0-83-generic 
  linux-image-generic 
  linux-generic 
  linux-signed-image-3.13.0-83-generic 
  linux-signed-image-generic 
  linux-signed-generic 
 E: Sub-process /usr/bin/dpkg returned an error code (1)
 
_____________________________________________________________________________________________________________________________________________

                        
**sudo dpkg -P linux-image-3.13.0-{74,76,77}-generic **
  
 dpkg: dependency problems prevent removal of linux-image-3.13.0-74-generic: 
  linux-signed-image-3.13.0-74-generic depends on linux-image-3.13.0-74-generic (= 3.13.0-74.118). 
  linux-image-extra-3.13.0-74-generic depends on linux-image-3.13.0-74-generic. 
  
 dpkg: error processing package linux-image-3.13.0-74-generic (--purge): 
  dependency problems - not removing 
 dpkg: dependency problems prevent removal of linux-image-3.13.0-76-generic: 
  linux-signed-image-3.13.0-76-generic depends on linux-image-3.13.0-76-generic (= 3.13.0-76.120). 
  linux-image-extra-3.13.0-76-generic depends on linux-image-3.13.0-76-generic. 
  
 dpkg: error processing package linux-image-3.13.0-76-generic (--purge): 
  dependency problems - not removing 
 dpkg: dependency problems prevent removal of linux-image-3.13.0-77-generic: 
  linux-image-extra-3.13.0-77-generic depends on linux-image-3.13.0-77-generic. 
  
 dpkg: error processing package linux-image-3.13.0-77-generic (--purge): 
  dependency problems - not removing 
 Errors were encountered while processing: 
  linux-image-3.13.0-74-generic 
  linux-image-3.13.0-76-generic 
  linux-image-3.13.0-77-generic 

___________________________________________________________________________________________________________________________________________________

---

### Post by Bashing-om on 2016-03-28
bonzo2; Hummm ...

AJ :)


How about we try a different order of operations ??
```

sudo dpkg -P linux-signed-image-3.13.0-{74,76,77}-generic

```

If that flies, we will want to manually remove the other 2 images and the 2 header files from each respective version.

bonzo2; The use of Code tags really helps :
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Our poor tired eyes.

[INDENT][INDENT]'times I do wonder
[INDENT][INDENT][INDENT]others I have to guess
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM:

I think we have success on the first command, yes? :D  Below is the output, which I hope is now formatted correctly. Thanks for the tips.
Are we able to progress to the manual removal step?

Thanks,
Bonzo


```

[COLOR=#000080]                         **sudo dpkg -P linux-signed-image-3.13.0-{74,76,77}-generic **
 

  (Reading database ... 353309 files and directories currently installed.) 
  Removing linux-signed-image-3.13.0-74-generic (3.13.0-74.118) ... 
  Generating grub configuration file ... 
  Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
  Found linux image: /boot/vmlinuz-3.13.0-83-generic 
  Found initrd image: /boot/initrd.img-3.13.0-83-generic 
  Found linux image: /boot/vmlinuz-3.13.0-79-generic 
  Found initrd image: /boot/initrd.img-3.13.0-79-generic 
  Found linux image: /boot/vmlinuz-3.13.0-77-generic 
  Found initrd image: /boot/initrd.img-3.13.0-77-generic 
  Found linux image: /boot/vmlinuz-3.13.0-76-generic 
  Found initrd image: /boot/initrd.img-3.13.0-76-generic 
  Found linux image: /boot/vmlinuz-3.13.0-74-generic 
  Found initrd image: /boot/initrd.img-3.13.0-74-generic 
  Found memtest86+ image: /memtest86+.elf 
  Found memtest86+ image: /memtest86+.bin 
  done 
  Purging configuration files for linux-signed-image-3.13.0-74-generic (3.13.0-74.118) ... 
  Removing linux-signed-image-3.13.0-76-generic (3.13.0-76.120) ... 
  Generating grub configuration file ... 
  Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
  Found linux image: /boot/vmlinuz-3.13.0-83-generic 
  Found initrd image: /boot/initrd.img-3.13.0-83-generic 
  Found linux image: /boot/vmlinuz-3.13.0-79-generic 
  Found initrd image: /boot/initrd.img-3.13.0-79-generic 
  Found linux image: /boot/vmlinuz-3.13.0-77-generic 
  Found initrd image: /boot/initrd.img-3.13.0-77-generic 
  Found linux image: /boot/vmlinuz-3.13.0-76-generic 
  Found initrd image: /boot/initrd.img-3.13.0-76-generic 
  Found linux image: /boot/vmlinuz-3.13.0-74-generic 
  Found initrd image: /boot/initrd.img-3.13.0-74-generic 
  Found memtest86+ image: /memtest86+.elf 
  Found memtest86+ image: /memtest86+.bin 
  done 
  Purging configuration files for linux-signed-image-3.13.0-76-generic (3.13.0-76.120) ... 
  Removing linux-signed-image-3.13.0-77-generic (3.13.0-77.121) ... 
  Purging configuration files for linux-signed-image-3.13.0-77-generic (3.13.0-77.121) ... 
[/COLOR]

```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Yeah !

Success ! That ran .

OK, now I do suggest:
```

sudo dpkg -P linux-image-extra-3.13.0-{74,76,77}-generic
sudo dpkg -P linux-image-3.13.0-{74,76,77}-generic
sudo dpkg -P linux-headers-3.13.0-{74,76,77}-generic
sudo dpkg -P linux-headers-3.13.0-{74,76,77}

```

Once these run clean, let's get the system stable on the latest kernel:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

And insure the package management system is now consistent.

[INDENT][INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Hi again, Bashing-om, :o

  

  I entered the full four lines of each of the two commands you suggested. (Was I to enter them separately, as eight commands?)  
  

  When I entered it the first command, I got a longer output than what is included below, but I somehow lost it. Duh!!! I retried the command (all four lines) and got the following output. The full output for the second command is also below.

  

  Did it work?  
  

  Thanks,
  Bonzo
 

 ```
 **sudo dpkg -P linux-image-extra-3.13.0-{74,76,77}-generic
```**```


 

 dpkg: warning: ignoring request to remove linux-image-extra-3.13.0-74-generic which isn't installed
 dpkg: warning: ignoring request to remove linux-image-extra-3.13.0-76-generic which isn't installed
 dpkg: warning: ignoring request to remove linux-image-extra-3.13.0-77-generic which isn't installed 
```
 

 

 **```
 sudo apt update 
```**```


 

 Hit http://security.ubuntu.com trusty-security InRelease                        
 Ign http://us.archive.ubuntu.com trusty InRelease                               
 Ign http://archive.canonical.com trusty InRelease                               
 Hit http://ppa.launchpad.net trusty InRelease                                   
 Ign http://extras.ubuntu.com trusty InRelease                                   
 Hit http://us.archive.ubuntu.com trusty-updates InRelease                       
 Hit http://security.ubuntu.com trusty-security/main Sources                     
 Hit http://archive.canonical.com trusty Release.gpg                             
 Hit http://us.archive.ubuntu.com trusty-backports InRelease                     
 Hit http://ppa.launchpad.net trusty InRelease                                   
 Hit http://extras.ubuntu.com trusty Release.gpg                                 
 Hit http://security.ubuntu.com trusty-security/restricted Sources               
 Hit http://us.archive.ubuntu.com trusty Release.gpg                             
 Hit http://archive.canonical.com trusty Release                                 
 Hit http://security.ubuntu.com trusty-security/universe Sources                 
 Hit http://us.archive.ubuntu.com trusty-updates/main Sources                    
 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         
 Hit http://extras.ubuntu.com trusty Release                                     
 Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources              
 Hit http://security.ubuntu.com trusty-security/multiverse Sources               
 Hit http://archive.canonical.com trusty/partner Sources                         
 Hit http://us.archive.ubuntu.com trusty-updates/universe Sources                
 Hit http://ppa.launchpad.net trusty/main i386 Packages                          
 Hit http://extras.ubuntu.com trusty/main Sources                                
 Hit http://security.ubuntu.com trusty-security/main amd64 Packages              
 Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources              
 Hit http://archive.canonical.com trusty/partner amd64 Packages                  
 Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages        
 Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages             
 Hit http://ppa.launchpad.net trusty/main Translation-en                         
 Hit http://extras.ubuntu.com trusty/main amd64 Packages                         
 Hit http://security.ubuntu.com trusty-security/universe amd64 Packages          
 Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages       
 Hit http://archive.canonical.com trusty/partner i386 Packages                   
 Hit http://ppa.launchpad.net trusty/main Sources                                
 Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages         
 Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages        
 Hit http://extras.ubuntu.com trusty/main i386 Packages                          
 Hit http://archive.canonical.com trusty/partner Translation-en                  
 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         
 Hit http://security.ubuntu.com trusty-security/main i386 Packages               
 Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages       
 Hit http://security.ubuntu.com trusty-security/restricted i386 Packages         
 Hit http://ppa.launchpad.net trusty/main i386 Packages                          
 Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages              
 Hit http://security.ubuntu.com trusty-security/universe i386 Packages           
 Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages        
 Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages         
 Hit http://ppa.launchpad.net trusty/main Translation-en                         
 Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages          
 Hit http://security.ubuntu.com trusty-security/main Translation-en              
 Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages        
 Hit http://security.ubuntu.com trusty-security/multiverse Translation-en        
 Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en             
 Hit http://security.ubuntu.com trusty-security/restricted Translation-en        
 Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en       
 Hit http://security.ubuntu.com trusty-security/universe Translation-en          
 Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en 
 Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en 
 Hit http://us.archive.ubuntu.com trusty-backports/main Sources           
 Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources 
 Ign http://extras.ubuntu.com trusty/main Translation-en_US     
 Hit http://us.archive.ubuntu.com trusty-backports/universe Sources 
 Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources 
 Ign http://extras.ubuntu.com trusty/main Translation-en            
 Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages 
 Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en 
 Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en 
 Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en 
 Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en 
 Hit http://us.archive.ubuntu.com trusty Release                                 
 Hit http://us.archive.ubuntu.com trusty/main Sources                            
 Hit http://us.archive.ubuntu.com trusty/restricted Sources                      
 Hit http://us.archive.ubuntu.com trusty/universe Sources                        
 Hit http://us.archive.ubuntu.com trusty/multiverse Sources                      
 Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                     
 Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages               
 Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                 
 Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages               
 Hit http://us.archive.ubuntu.com trusty/main i386 Packages                      
 Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages                
 Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                  
 Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                
 Hit http://us.archive.ubuntu.com trusty/main Translation-en                     
 Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en               
 Hit http://us.archive.ubuntu.com trusty/restricted Translation-en               
 Hit http://us.archive.ubuntu.com trusty/universe Translation-en                 
 Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                  
 Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US            
 Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US            
 Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US              
 Reading package lists... Done   
```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Welp,

Chances are it all took;
" get -f install" resulted in all zeros ?
" dpkg -C" just a direct return to prompt with no output ?

Let's look:
```

dpkg -l | grep linux

```
at what is now, and we next do a bit of clean up .

[INDENT][INDENT]nothing like a clean house
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Hi Again, Bashing-OM,

I hope I did what you've asked. I ran    	 	 	 	"dpkg -l l grep linux" and included the output below. I wasn't clear on whether I was supposed to do something with the commands in quotes. Let me know if I've given you the proper information, please. 


Thanks,
Bonzo 




```
dpkg -l | grep linux 

 ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries 
 ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries 
 ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries 
 ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library 
 ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 iU  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-76                               3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-76-generic                       3.13.0-76.120                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 pi  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 pi  linux-image-3.13.0-76-generic                         3.13.0-76.120                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 pi  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iF  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iU  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 iU  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 rc  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-66-generic                  3.13.0-66.108                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-73-generic                  3.13.0-73.116                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client 
 ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders 
 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies 
 ii  util-linux                                            2.20.1-5.1ubuntu20.7                                amd64        Miscellaneous system utilities 
  

```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Nope ......

Not clean yet .
Let's backup a bit and redo, terminal command:
```

sudo dpkg -P linux-image-3.13.0-{74,76,77}-generic

```

If and when that runs clean we remove the related headers files.

Show a new :
```

dpkg -l |grep linux-

```
When the above is completed. We make sure of that next step.


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
[FONT=arial black]Bashing-OM,

Here are the results of the first command.  Is it OK to go forward with the second command above 
[/FONT][FONT=arial black](dpkg -l |grep linux-)?

Thanks,
Bonzo

[/FONT]
```

sudo dpkg -P linux-image-3.13.0-{74,76,77}-generic
(Reading database ... 341556 files and directories currently installed.)
Removing linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Removing linux-image-3.13.0-76-generic (3.13.0-76.120) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-76-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-76-generic (3.13.0-76.120) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
Removing linux-image-3.13.0-77-generic (3.13.0-77.121) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-77-generic (3.13.0-77.121) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-77-generic /boot/vmlinuz-3.13.0-77-generic

```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Yepper,

That looks good.

So yes now we want an updated status of installed kernels.
Post back:
```

dpkg -l | grep linux-

```
And we hope to see that next is to remove the headers .

[INDENT]longest journey ends
[INDENT][INDENT][INDENT]even with small steps
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM,

Here we go again ... What does it tell us? :wink:

Bonzo

  	 	 	 	   ```
dpkg -l | grep linux- 

 ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 iU  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-76                               3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-76-generic                       3.13.0-76.120                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iF  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iU  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 iU  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 rc  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-66-generic                  3.13.0-66.108                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-73-generic                  3.13.0-73.116                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies 

```

---

### Post by Bashing-om on 2016-03-28
bonzo2; K,

Next small step:
Do terminal command:
```

sudo dpkg -P linux-headers-3.13.0-{74,76,77}-generic

```

Now that runs clean. next step:
Do terminal command:
```

sudo dpkg -P linux-headers-3.13.0-{74,76,77}

```

Show again a new:
```

dpkg -l | grep linux-

```

Let's see now what remains for cleanup.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-om,
Once again … output. I can't decipher the output, but it wouldn't be premature of me to celebrate, would it? :lolflag:

 

  
Thanks,
Bonzo

  

 

 

 ```
**sudo dpkg -P linux-headers-3.13.0-{74,76,77}-generic **

 (Reading database ... 338844 files and directories currently installed.) 
 Removing linux-headers-3.13.0-74-generic (3.13.0-74.118) ... 
 Removing linux-headers-3.13.0-76-generic (3.13.0-76.120) ... 
 Removing linux-headers-3.13.0-77-generic (3.13.0-77.121) ... 

``` 

 

 ```
**sudo dpkg -P linux-headers-3.13.0-{74,76,77} **

 (Reading database ... 310148 files and directories currently installed.) 
 Removing linux-headers-3.13.0-74 (3.13.0-74.118) ... 
 Removing linux-headers-3.13.0-76 (3.13.0-76.120) ... 
 Removing linux-headers-3.13.0-77 (3.13.0-77.121) ... 

``` 

 ```
**dpkg -l | grep linux- **

 ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 iU  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iF  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 iU  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 iU  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 rc  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-66-generic                  3.13.0-66.108                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-73-generic                  3.13.0-73.116                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 iU  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 

 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies 

```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Uh HUh ..

Looking good, but not out of the woods yet .
Per:
> 
iU  linux-generic
iU  linux-image-generic 
iU  linux-signed-generic 
iF  linux-image-extra-3.13.0-83-generic 
iU  linux-signed-image-3.13.0-83-generic 

we have some re-building to do.
where in that 1st field 'iU' ; The desired state is (I)nstalled but the actual state is (U)ninstalled and the 'F' is hal(F)-configured !

Let's now run:
```

sudo apt install --reinstall linux-generic linux-image-generic linux-signed-generic
sudo apt-get -f install

```
For my piece of mind show us the results .

Next perhaps we are ready to do some final cleanup.

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM,

Here it is. What the what?!:confused:

Bonzo

```

[B]sudo apt install --reinstall linux-generic linux-image-generic linux-signed-generic
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 23 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-image-generic:amd64
```

---

### Post by Bashing-om on 2016-03-28
bonzo2; Yuk !

I thought we were past this !
> 
e and [color=red]23[/color] not upgraded.

This is totally unexpected, and I do not presently know what to make of:
> 
E: Internal Error, No file name for linux-image-generic:amd64


Let's try once more with feeling:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```
And show us the complete outputs of those commands.

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to make a package manager like you
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM,

Okay, that post made me laugh, although I'm getting nervous! OOZING WITH FEELING, I present:
:P

```

**sudo apt update **

 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                        
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]           
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                     
 Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                   
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                 
 Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                             
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages              
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [270 kB]         
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                         
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages          
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages        
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                         
 Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                                
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                   
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages         
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages           
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B]  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages         
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [742 kB]  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en        
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB] 
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [356 kB] 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en          
 Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB] 
 Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [710 kB]  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB] 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                  
 Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [357 kB] 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                         
 Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB] 
 Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [370 kB] 
 Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,227 B] 
 Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B] 
 Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [186 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                      
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US              
 Fetched 3,289 kB in 9s (341 kB/s)                                               
 Reading package lists... Done
```

---

### Post by Bashing-om on 2016-03-28
bonzo2; 

So far so good ..

And the next 2 commands ?

[INDENT][INDENT]not done 'til
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM,

FYI: I'm in a holding pattern. The upgrade is just plugging along quite slowly (now at 15%) but surely. 

Will post output when it's complete. Thank you so much for hanging in here with me. You have the patience of a saint!

Thx,
Bonzo

---

### Post by Bashing-om on 2016-03-28
bonzo2; 

So far so good ..

We await the outcome of 'upgrade' !

[INDENT][INDENT]not done 'til
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-28
Bashing-OM,

I'm barely at the half-way mark in the upgrade.  I have to catch my train, but will post my output tomorrow. I hope to see you then, and I cannot thank you enough for sharing your time with me. You've been so generous.

Have a good day!

Bonzo

---

### Post by Bashing-om on 2016-03-28
bonzo2; Yikes ...

Taking this long for an 'upgrade'; something stinks !

We pick this up tomorrow, after my chores are done .

[INDENT][INDENT][INDENT]oh boy !
[INDENT][INDENT][INDENT]here we go again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Hi Bashing-OM,

I couldn't bear to walk away from my computer as it was churning away on the update. I'm going offline now, but am hoping tomorrow to get your stamp of approval on the output. Seems good, yes? 
                     

 ```
**sudo apt upgrade **
 

 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 The following packages will be upgraded: 
   chromium-browser chromium-browser-dbg chromium-browser-l10n 
   chromium-codecs-ffmpeg-extra coreutils gir1.2-javascriptcoregtk-3.0 
   gir1.2-webkit-3.0 initramfs-tools initramfs-tools-bin 
   libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libtiff5 libtiff5:i386 
   libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0 
   libwebkitgtk-3.0-common openjdk-7-doc openjdk-7-jdk openjdk-7-jre 
   openjdk-7-jre-headless tzdata tzdata-java 
 23 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 6 not fully installed or removed. 
 Need to get 1,102 MB of archives. 
 After this operation, 244 MB of additional disk space will be used. 
 Do you want to continue? [Y/n] y 
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main coreutils amd64 8.21-1ubuntu5.4 [1,091 kB] 
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe chromium-browser-l10n all 49.0.2623.87-0ubuntu0.14.04.1.1112 [3,302 kB] 
 Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe chromium-browser-dbg amd64 49.0.2623.87-0ubuntu0.14.04.1.1112 [943 MB] 
 Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe chromium-browser amd64 49.0.2623.87-0ubuntu0.14.04.1.1112 [68.6 MB] 
 Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe chromium-codecs-ffmpeg-extra amd64 49.0.2623.87-0ubuntu0.14.04.1.1112 [890 kB] 
 Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libwebkitgtk-1.0-common all 2.4.10-0ubuntu0.14.04.1 [108 kB] 
 Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libwebkitgtk-1.0-0 amd64 2.4.10-0ubuntu0.14.04.1 [7,232 kB] 
 Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libjavascriptcoregtk-1.0-0 amd64 2.4.10-0ubuntu0.14.04.1 [1,823 kB] 
 Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libwebkitgtk-3.0-common all 2.4.10-0ubuntu0.14.04.1 [108 kB] 
 Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libwebkitgtk-3.0-0 amd64 2.4.10-0ubuntu0.14.04.1 [7,229 kB] 
 Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libjavascriptcoregtk-3.0-0 amd64 2.4.10-0ubuntu0.14.04.1 [1,824 kB] 
 Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libtiff5 i386 4.0.3-7ubuntu0.4 [142 kB] 
 Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libtiff5 amd64 4.0.3-7ubuntu0.4 [143 kB] 
 Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main openjdk-7-jdk amd64 7u95-2.6.4-0ubuntu0.14.04.2 [16.3 MB] 
 Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main openjdk-7-jre amd64 7u95-2.6.4-0ubuntu0.14.04.2 [172 kB] 
 Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main tzdata-java all 2016b-0ubuntu0.14.04 [69.4 kB] 
 Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main tzdata all 2016b-0ubuntu0.14.04 [166 kB] 
 Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main openjdk-7-jre-headless amd64 7u95-2.6.4-0ubuntu0.14.04.2 [39.1 MB] 
 Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main initramfs-tools all 0.103ubuntu4.3 [44.4 kB] 
 Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main initramfs-tools-bin amd64 0.103ubuntu4.3 [9,172 B] 
 Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main gir1.2-webkit-3.0 amd64 2.4.10-0ubuntu0.14.04.1 [60.6 kB] 
 Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main gir1.2-javascriptcoregtk-3.0 amd64 2.4.10-0ubuntu0.14.04.1 [12.6 kB] 
 Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main openjdk-7-doc all 7u95-2.6.4-0ubuntu0.14.04.2 [10.9 MB] 
 Fetched 1,102 MB in 1h 30min 52s (202 kB/s)                                     
 Preconfiguring packages ... 
 (Reading database ... 264379 files and directories currently installed.) 
 Preparing to unpack .../coreutils_8.21-1ubuntu5.4_amd64.deb ... 
 Unpacking coreutils (8.21-1ubuntu5.4) over (8.21-1ubuntu5.3) ... 
 Processing triggers for install-info (5.2.0.dfsg.1-2) ... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
 Setting up coreutils (8.21-1ubuntu5.4) ... 
 (Reading database ... 264379 files and directories currently installed.) 
 Preparing to unpack .../chromium-browser-l10n_49.0.2623.87-0ubuntu0.14.04.1.1112_all.deb ... 
 Unpacking chromium-browser-l10n (49.0.2623.87-0ubuntu0.14.04.1.1112) over (48.0.2564.116-0ubuntu0.14.04.1.1111) ... 
 Preparing to unpack .../chromium-browser-dbg_49.0.2623.87-0ubuntu0.14.04.1.1112_amd64.deb ... 
 Unpacking chromium-browser-dbg (49.0.2623.87-0ubuntu0.14.04.1.1112) over (48.0.2564.116-0ubuntu0.14.04.1.1111) ... 
 Preparing to unpack .../chromium-browser_49.0.2623.87-0ubuntu0.14.04.1.1112_amd64.deb ... 
 Unpacking chromium-browser (49.0.2623.87-0ubuntu0.14.04.1.1112) over (48.0.2564.116-0ubuntu0.14.04.1.1111) ... 
 Preparing to unpack .../chromium-codecs-ffmpeg-extra_49.0.2623.87-0ubuntu0.14.04.1.1112_amd64.deb ... 
 Unpacking chromium-codecs-ffmpeg-extra (49.0.2623.87-0ubuntu0.14.04.1.1112) over (48.0.2564.116-0ubuntu0.14.04.1.1111) ... 
 Preparing to unpack .../libwebkitgtk-1.0-common_2.4.10-0ubuntu0.14.04.1_all.deb ... 
 Unpacking libwebkitgtk-1.0-common (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libwebkitgtk-1.0-0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking libwebkitgtk-1.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libjavascriptcoregtk-1.0-0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking libjavascriptcoregtk-1.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libwebkitgtk-3.0-common_2.4.10-0ubuntu0.14.04.1_all.deb ... 
 Unpacking libwebkitgtk-3.0-common (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libwebkitgtk-3.0-0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking libwebkitgtk-3.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libjavascriptcoregtk-3.0-0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking libjavascriptcoregtk-3.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../libtiff5_4.0.3-7ubuntu0.4_i386.deb ... 
 De-configuring libtiff5:amd64 (4.0.3-7ubuntu0.3) ... 
 Unpacking libtiff5:i386 (4.0.3-7ubuntu0.4) over (4.0.3-7ubuntu0.3) ... 
 Preparing to unpack .../libtiff5_4.0.3-7ubuntu0.4_amd64.deb ... 
 Unpacking libtiff5:amd64 (4.0.3-7ubuntu0.4) over (4.0.3-7ubuntu0.3) ... 
 Preparing to unpack .../openjdk-7-jdk_7u95-2.6.4-0ubuntu0.14.04.2_amd64.deb ... 
 Unpacking openjdk-7-jdk:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) over (7u95-2.6.4-0ubuntu0.14.04.1) ... 
 Preparing to unpack .../openjdk-7-jre_7u95-2.6.4-0ubuntu0.14.04.2_amd64.deb ... 
 Unpacking openjdk-7-jre:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) over (7u95-2.6.4-0ubuntu0.14.04.1) ... 
 Preparing to unpack .../tzdata-java_2016b-0ubuntu0.14.04_all.deb ... 
 Unpacking tzdata-java (2016b-0ubuntu0.14.04) over (2015g-0ubuntu0.14.04) ... 
 Preparing to unpack .../tzdata_2016b-0ubuntu0.14.04_all.deb ... 
 Unpacking tzdata (2016b-0ubuntu0.14.04) over (2015g-0ubuntu0.14.04) ... 
 Processing triggers for mime-support (3.54ubuntu1.1) ... 
 Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
 Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
 Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
 Rebuilding /usr/share/applications/bamf-2.index... 
 Processing triggers for hicolor-icon-theme (0.13-1) ... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
 Setting up tzdata (2016b-0ubuntu0.14.04) ... 
  
 Current default time zone: 'America/New_York' 
 Local time is now:      Mon Mar 28 23:42:43 PDT 2016. 
 Universal Time is now:  Tue Mar 29 03:42:43 UTC 2016. 
 Run 'dpkg-reconfigure tzdata' if you wish to change it. 
  
 (Reading database ... 264084 files and directories currently installed.) 
 Preparing to unpack .../openjdk-7-jre-headless_7u95-2.6.4-0ubuntu0.14.04.2_amd64.deb ... 
 Unpacking openjdk-7-jre-headless:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) over (7u95-2.6.4-0ubuntu0.14.04.1) ... 
 Preparing to unpack .../initramfs-tools_0.103ubuntu4.3_all.deb ... 
 Unpacking initramfs-tools (0.103ubuntu4.3) over (0.103ubuntu4.2) ... 
 Preparing to unpack .../initramfs-tools-bin_0.103ubuntu4.3_amd64.deb ... 
 Unpacking initramfs-tools-bin (0.103ubuntu4.3) over (0.103ubuntu4.2) ... 
 Preparing to unpack .../gir1.2-webkit-3.0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking gir1.2-webkit-3.0 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../gir1.2-javascriptcoregtk-3.0_2.4.10-0ubuntu0.14.04.1_amd64.deb ... 
 Unpacking gir1.2-javascriptcoregtk-3.0 (2.4.10-0ubuntu0.14.04.1) over (2.4.8-1ubuntu1~ubuntu14.04.1) ... 
 Preparing to unpack .../openjdk-7-doc_7u95-2.6.4-0ubuntu0.14.04.2_all.deb ... 
 Unpacking openjdk-7-doc (7u95-2.6.4-0ubuntu0.14.04.2) over (7u95-2.6.4-0ubuntu0.14.04.1) ... 
 Processing triggers for doc-base (0.10.5) ... 
 Processing 2 changed doc-base files... 
 Registering documents with scrollkeeper... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
 Setting up linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ... 
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic 
 Generating grub configuration file ... 
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
 Found linux image: /boot/vmlinuz-3.13.0-83-generic 
 Found initrd image: /boot/initrd.img-3.13.0-83-generic 
 Found linux image: /boot/vmlinuz-3.13.0-79-generic 
 Found initrd image: /boot/initrd.img-3.13.0-79-generic 
 Found memtest86+ image: /memtest86+.elf 
 Found memtest86+ image: /memtest86+.bin 
 done 
 Setting up linux-image-generic (3.13.0.83.89) ... 
 Setting up linux-generic (3.13.0.83.89) ... 
 Setting up linux-signed-image-3.13.0-83-generic (3.13.0-83.127) ... 
 Generating grub configuration file ... 
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
 Found linux image: /boot/vmlinuz-3.13.0-83-generic 
 Found initrd image: /boot/initrd.img-3.13.0-83-generic 
 Found linux image: /boot/vmlinuz-3.13.0-79-generic 
 Found initrd image: /boot/initrd.img-3.13.0-79-generic 
 Found memtest86+ image: /memtest86+.elf 
 Found memtest86+ image: /memtest86+.bin 
 done 
 Setting up linux-signed-image-generic (3.13.0.83.89) ... 
 Setting up linux-signed-generic (3.13.0.83.89) ... 
 Setting up chromium-codecs-ffmpeg-extra (49.0.2623.87-0ubuntu0.14.04.1.1112) ... 
 Setting up chromium-browser (49.0.2623.87-0ubuntu0.14.04.1.1112) ... 
 Setting up chromium-browser-l10n (49.0.2623.87-0ubuntu0.14.04.1.1112) ... 
 Setting up chromium-browser-dbg (49.0.2623.87-0ubuntu0.14.04.1.1112) ... 
 Setting up libwebkitgtk-1.0-common (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libjavascriptcoregtk-1.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libwebkitgtk-1.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libwebkitgtk-3.0-common (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libjavascriptcoregtk-3.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libwebkitgtk-3.0-0:amd64 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up libtiff5:amd64 (4.0.3-7ubuntu0.4) ... 
 Setting up libtiff5:i386 (4.0.3-7ubuntu0.4) ... 
 Setting up tzdata-java (2016b-0ubuntu0.14.04) ... 
 Setting up openjdk-7-jre-headless:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) ... 
 Setting up openjdk-7-jre:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) ... 
 Setting up openjdk-7-jdk:amd64 (7u95-2.6.4-0ubuntu0.14.04.2) ... 
 Setting up initramfs-tools-bin (0.103ubuntu4.3) ... 
 Setting up initramfs-tools (0.103ubuntu4.3) ... 
 update-initramfs: deferring update (trigger activated) 
 Setting up gir1.2-javascriptcoregtk-3.0 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up gir1.2-webkit-3.0 (2.4.10-0ubuntu0.14.04.1) ... 
 Setting up openjdk-7-doc (7u95-2.6.4-0ubuntu0.14.04.2) ... 
 Processing triggers for libc-bin (2.19-0ubuntu6.7) ... 
 Processing triggers for initramfs-tools (0.103ubuntu4.3) ... 
 update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic
``` 
 

 ```
**sudo apt full-upgrade **
 
Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2016-03-29
bonzo2; Ho Kay ...

I do have a spot of reservation, but overall I think things look good.

Let's look at what is .. and what might have been done amiss at some point in the past.
Show us the outputs of :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd*

```
All directories MUST agree with the installed versions. Now if all agree and I am happy with what the system has set as the booting kernels, well ... no time like then to reboot and then check the effects.

If at that point all is still good .. we do some cleanup .

[INDENT][INDENT][INDENT]is that light peeking through
[INDENT][INDENT][INDENT]yonder window
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Good day, Bashing-OM,

Bonzo here with the output you requested. And, yes! That is light you see over yonder. :-)



```
**ls -al /usr/src/** 
 total 28 
 drwxr-xr-x  7 root root 4096 Mar 28 18:18 . 
 drwxr-xr-x 10 root root 4096 Jul 22  2014 .. 
 drwxr-xr-x 24 root root 4096 Dec 16 21:54 linux-headers-3.13.0-73 
 drwxr-xr-x 24 root root 4096 Feb 22 20:04 linux-headers-3.13.0-79 
 drwxr-xr-x  7 root root 4096 Feb 22 20:04 linux-headers-3.13.0-79-generic 
 drwxr-xr-x 24 root root 4096 Mar 16 19:09 linux-headers-3.13.0-83 
 drwxr-xr-x  7 root root 4096 Mar 16 19:09 linux-headers-3.13.0-83-generic 
```
 

 

 ```
**ls -al /lib/modules/ **
 total 16 
 drwxr-xr-x  4 root root 4096 Mar 28 18:17 . 
 drwxr-xr-x 26 root root 4096 Feb 19 01:31 .. 
 drwxr-xr-x  5 root root 4096 Feb 23 15:07 3.13.0-79-generic 
 drwxr-xr-x  5 root root 4096 Mar 28 20:43 3.13.0-83-generic
 
```

 

 ```
**ls -al /boot/ **
 total 90196 
 drwxr-xr-x  4 root root     3072 Mar 28 20:44 . 
 drwxr-xr-x 23 root root     4096 Mar 16 19:09 .. 
 -rw-r--r--  1 root root  1165513 Feb 19 07:47 abi-3.13.0-79-generic 
 -rw-r--r--  1 root root  1165578 Mar 10 17:35 abi-3.13.0-83-generic 
 -rw-r--r--  1 root root   165918 Feb 19 07:47 config-3.13.0-79-generic 
 -rw-r--r--  1 root root   165918 Mar 10 17:35 config-3.13.0-83-generic 
 drwxr-xr-x  5 root root     1024 Mar 28 20:43 grub 
 -rw-r--r--  1 root root 29318505 Feb 23 15:07 initrd.img-3.13.0-79-generic 
 -rw-r--r--  1 root root 29335659 Mar 28 20:44 initrd.img-3.13.0-83-generic 
 drwx------  2 root root    12288 Jan 13  2015 lost+found 
 -rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin 
 -rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf 
 -rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin 
 -rw-------  1 root root  3393574 Feb 19 07:47 System.map-3.13.0-79-generic 
 -rw-------  1 root root  3393725 Mar 10 17:35 System.map-3.13.0-83-generic 
 -rw-------  1 root root  5828256 Feb 19 07:47 vmlinuz-3.13.0-79-generic 
 -rw-------  1 root root  5830168 Feb 23 15:08 vmlinuz-3.13.0-79-generic.efi.signed 
 -rw-------  1 root root  5827776 Mar 10 17:35 vmlinuz-3.13.0-83-generic 
 -rw-------  1 root root  5829688 Mar 28 20:43 vmlinuz-3.13.0-83-generic.efi.signed
``` 
 

 ```
**dpkg -l | grep linux- **
 ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 ii  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 rc  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 rc  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 ii  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 rc  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-66-generic                  3.13.0-66.108                                       amd64        Signed kernel image generic 
 rc  linux-signed-image-3.13.0-73-generic                  3.13.0-73.116                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies 
```
  
 ```
**ls -al /vmlinuz*** 
 lrwxrwxrwx 1 root root 30 Mar 16 19:09 /vmlinuz -> boot/vmlinuz-3.13.0-83-generic 
 lrwxrwxrwx 1 root root 30 Feb 22 20:04 /vmlinuz.old -> boot/vmlinuz-3.13.0-79-generic 
 
```

 **ls```
 -al /initrd* 
```**```

 lrwxrwxrwx 1 root root 33 Mar 16 19:09 /initrd.img -> boot/initrd.img-3.13.0-83-generic 
 lrwxrwxrwx 1 root root 33 Feb 22 20:04 /initrd.img.old -> boot/initrd.img-3.13.0-79-generic
```

---

### Post by Bashing-om on 2016-03-29
bonzo2; Not looking too shabby 
At all.

BUT, we still have work to do .. as we must make all the directories agree with what is installed.

Still to clean up:
> 
rc  linux-image-extra-3.13.0-73-generic 

ii  linux-headers-3.13.0-73


Let's "assume" that the 'rc' is valid and remove the header file:
```

sudo apt remove linux-headers-3.13.0-73

```
and if that goes well we next need to reboot the system
and see what kernel is now booting:
```

uname -r

```

Where we hope and want it to boot the -83 kernel version .

If all is good at this point, we do the final cleanup .

[INDENT][INDENT]it is it is -> LIGHT
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Bashing-OM,

I don't quite understand everything you've explained, but by now I know to just listen, learn, and RUN THE CODE!:o

Bonzo

  ```
**sudo apt remove linux-headers-3.13.0-73 **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be REMOVED: 
   linux-headers-3.13.0-73 
 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
 After this operation, 63.4 MB disk space will be freed. 
 Do you want to continue? [Y/n] y 
 (Reading database ... 264082 files and directories currently installed.) 
 Removing linux-headers-3.13.0-73 (3.13.0-73.116) ... 
```
 

 ```
**uname -r **
 3.13.0-83-generic
```

---

### Post by Bashing-om on 2016-03-29
bonzo2l Hey ....Hey ..

Look'n good !
> 
I don't quite understand everything you've explained, but by now I know to just listen, learn, and RUN THE CODE!


This forum also serves as an institution of learning ..... ASK for clarification. I do try to explain but I often fall short of that goal.

Let's prepare to bite the bullet. I want a record of what will happen when we pull the trigger.
```

sudo apt-get -s autoremove

```
where the '-s' flag is "simulate" ; look but do not do.

[INDENT][INDENT]s l o w,
[INDENT][INDENT][INDENT]but gets the job done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Hey Bashing-OM,

That is cool to learn about the simulate flag. Had no idea. ;-)

As requested, the bullet has been bitten thusly:

```
**sudo apt-get -s autoremove**
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2016-03-29
bonzo2; Surprise, surprise

The package manager is fat dumb and happy; nothing left there to do.
Cleanup:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.

```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

[INDENT][INDENT]now tell me
[INDENT][INDENT][INDENT]is the fat lady sing'n ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Bashing-OM[B],


[/B]The fat lady is cautiously humming :-) ... will be singing after confirmation that this looks right[B]. 

[/B]```
[B]
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge [/B]

 (Reading database ... 248825 files and directories currently installed.) 
 Removing cndrvcups-common (2.50-1-2~raring1) ... 
 Purging configuration files for cndrvcups-common (2.50-1-2~raring1) ... 
 Removing flashplugin-installer (11.2.202.559ubuntu0.14.04.1) ... 
 Purging configuration files for flashplugin-installer (11.2.202.559ubuntu0.14.04.1) ... 
 Removing libavahi-client3:i386 (0.6.31-4ubuntu1) ... 
 Purging configuration files for libavahi-client3:i386 (0.6.31-4ubuntu1) ... 
 Removing libavahi-common3:i386 (0.6.31-4ubuntu1) ... 
 Purging configuration files for libavahi-common3:i386 (0.6.31-4ubuntu1) ... 
 Removing libboost-graph1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Purging configuration files for libboost-graph1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Removing libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Purging configuration files for libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Removing libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Purging configuration files for libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Removing libboost-test1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Purging configuration files for libboost-test1.54.0:amd64 (1.54.0-4ubuntu3.1) ... 
 Removing libcairo-script-interpreter2:amd64 (1.13.0~20140204-0ubuntu1.1) ... 
 Purging configuration files for libcairo-script-interpreter2:amd64 (1.13.0~20140204-0ubuntu1.1) ... 
 Removing libcups2:i386 (1.7.2-0ubuntu1.6) ... 
 Purging configuration files for libcups2:i386 (1.7.2-0ubuntu1.6) ... 
 Removing libglade2-0:i386 (1:2.6.4-2) ... 
 Purging configuration files for libglade2-0:i386 (1:2.6.4-2) ... 
 Removing libgnutls26:i386 (2.12.23-12ubuntu2.2) ... 
 Purging configuration files for libgnutls26:i386 (2.12.23-12ubuntu2.2) ... 
 Removing libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Purging configuration files for libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Removing libgtk2.0-0:i386 (2.24.23-0ubuntu1.2) ... 
 Purging configuration files for libgtk2.0-0:i386 (2.24.23-0ubuntu1.2) ... 
 Removing libgtkhtml-4.0-0 (4.6.6-2ubuntu1) ... 
 Purging configuration files for libgtkhtml-4.0-0 (4.6.6-2ubuntu1) ... 
 Removing libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1) ... 
 Purging configuration files for libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1) ... 
 Removing libharfbuzz-gobject0:amd64 (0.9.27-1ubuntu1) ... 
 Purging configuration files for libharfbuzz-gobject0:amd64 (0.9.27-1ubuntu1) ... 
 Removing libk5crypto3:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Purging configuration files for libk5crypto3:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Removing libkeyutils1:i386 (1.5.6-1) ... 
 Purging configuration files for libkeyutils1:i386 (1.5.6-1) ... 
 Removing libkrb5-3:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Purging configuration files for libkrb5-3:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Removing libkrb5support0:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Purging configuration files for libkrb5support0:i386 (1.12+dfsg-2ubuntu5.1) ... 
 Removing libp11-kit0:i386 (0.20.2-2ubuntu2) ... 
 Purging configuration files for libp11-kit0:i386 (0.20.2-2ubuntu2) ... 
 Removing libpcrecpp0:amd64 (1:8.31-2ubuntu2) ... 
 Purging configuration files for libpcrecpp0:amd64 (1:8.31-2ubuntu2) ... 
 Removing libpisock9 (0.12.5-6ubuntu2) ... 
 Purging configuration files for libpisock9 (0.12.5-6ubuntu2) ... 
 Removing libpisync1 (0.12.5-6ubuntu2) ... 
 Purging configuration files for libpisync1 (0.12.5-6ubuntu2) ... 
 Removing libpopt0:i386 (1.16-8ubuntu1) ... 
 Purging configuration files for libpopt0:i386 (1.16-8ubuntu1) ... 
 Removing libpst4:amd64 (0.6.59-1build1) ... 
 Purging configuration files for libpst4:amd64 (0.6.59-1build1) ... 
 Removing libsearchclient0 (0.7.8-1ubuntu2) ... 
 Purging configuration files for libsearchclient0 (0.7.8-1ubuntu2) ... 
 Removing libstrigihtmlgui0 (0.7.8-1ubuntu2) ... 
 Purging configuration files for libstrigihtmlgui0 (0.7.8-1ubuntu2) ... 
 Removing libstrigiqtdbusclient0 (0.7.8-1ubuntu2) ... 
 Purging configuration files for libstrigiqtdbusclient0 (0.7.8-1ubuntu2) ... 
 Removing libtasn1-6:i386 (3.4-3ubuntu0.3) ... 
 Purging configuration files for libtasn1-6:i386 (3.4-3ubuntu0.3) ... 
 Removing libunique-1.0-0 (1.1.6-4ubuntu2) ... 
 Purging configuration files for libunique-1.0-0 (1.1.6-4ubuntu2) ... 
 Removing libytnef0:amd64 (1.5-6) ... 
 Purging configuration files for libytnef0:amd64 (1.5-6) ... 
 Removing linux-image-3.13.0-44-generic (3.13.0-44.73) ... 
 Purging configuration files for linux-image-3.13.0-44-generic (3.13.0-44.73) ... 
 Examining /etc/kernel/postrm.d . 
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic 
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic 
 Removing linux-image-3.13.0-66-generic (3.13.0-66.108) ... 
 Purging configuration files for linux-image-3.13.0-66-generic (3.13.0-66.108) ... 
 Examining /etc/kernel/postrm.d . 
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic 
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic 
 Removing linux-image-3.13.0-73-generic (3.13.0-73.116) ... 
 Purging configuration files for linux-image-3.13.0-73-generic (3.13.0-73.116) ... 
 Examining /etc/kernel/postrm.d . 
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic 
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic 
 Removing linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ... 
 Purging configuration files for linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ... 
 Removing linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ... 
 Purging configuration files for linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ... 
 Removing linux-image-extra-3.13.0-73-generic (3.13.0-73.116) ... 
 Purging configuration files for linux-image-extra-3.13.0-73-generic (3.13.0-73.116) ... 
 Removing linux-signed-image-3.13.0-44-generic (3.13.0-44.73) ... 
 Purging configuration files for linux-signed-image-3.13.0-44-generic (3.13.0-44.73) ... 
 Removing linux-signed-image-3.13.0-66-generic (3.13.0-66.108) ... 
 Purging configuration files for linux-signed-image-3.13.0-66-generic (3.13.0-66.108) ... 
 Removing linux-signed-image-3.13.0-73-generic (3.13.0-73.116) ... 
 Purging configuration files for linux-signed-image-3.13.0-73-generic (3.13.0-73.116) ... 
 Removing mail-notification (5.4.dfsg.1-9) ... 
 Purging configuration files for mail-notification (5.4.dfsg.1-9) ... 
 Removing rhythmbox (3.0.2-0ubuntu2) ... 
 Purging configuration files for rhythmbox (3.0.2-0ubuntu2) ... 
 Removing tango-icon-theme (0.8.90-5ubuntu1) ... 
 Purging configuration files for tango-icon-theme (0.8.90-5ubuntu1) ... 
 Removing thunar (1.6.3-1ubuntu5) ... 
 Purging configuration files for thunar (1.6.3-1ubuntu5) ... 
 Removing thunar-volman (0.8.0-4ubuntu1) ... 
 Purging configuration files for thunar-volman (0.8.0-4ubuntu1) ... 
 Removing xfce4-appfinder (4.10.1-1) ... 
 Purging configuration files for xfce4-appfinder (4.10.1-1) ... 
 Removing xfce4-mixer (1:4.10.0-1ubuntu2) ... 
 Purging configuration files for xfce4-mixer (1:4.10.0-1ubuntu2) ... 
 Removing xfce4-panel (4.11.0-0ubuntu1) ... 
 Purging configuration files for xfce4-panel (4.11.0-0ubuntu1) ... 
 Processing triggers for menu (2.1.46ubuntu1) ...
```

---

### Post by ajgreeny on 2016-03-29
Brilliant work again Bashing-om!

You certainly know dpkg better than I and I think have sorted this out extremely patiently.

Well done.

---

### Post by bonzo2 on 2016-03-29
Hello ajgreeny,

Thanks for confirming my suspicion that Bashing-OM's work has in fact been **[COLOR=#ff0000]brilliant[/COLOR]**.  I'm not proficient enough to understand much of anything we've done here, but it's patently obvious that Bashing in talented and patient.  I feel so lucky to have his/her assistance!  

Lucky day ... lucky day ... lucky day! :-)

Cheers to Bashing-OM!

Bonzo

---

### Post by Bashing-om on 2016-03-29
@ AJ ... 

All I can say is that I had good teachers - you one of them ( I do remember all those whens ).

@ bonzo2 .. as we go humm'n merrily right on along ....

Reboot and let's verify/re-confirm :
```

df -h
df -i
dpkg -l | grep linux
sudo apt update
sudo apt upgrade
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get -f install

```
All that comes back clean and clear ... we in good shape ..

Now with the next kernel version release .. after it is installed and you have booted and verified all is good on this new kernel;
At that point run:
```

sudo apt-get autoremove

```
and if it does not also remove the old kernels we need to look and find out why.
Then one does not get into the condition we have just climbed out of. You have a very small /boot partition ( there is a bug report in this respect) and you must keep on top of it.


[INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Hi Bash,

Do I understand correctly that small buggy partition is best addressed by using the "sudo apt-get autoremove" command after every update?  Would it be better or even possible for me to just expand my partition?  I thought I'd seen instructions for that somewhere. I couldn't get this system back to frog-hair fine on my own, so I need to avoid an encore of this situation! :D

Bonzo


```
**df -h **
 Filesystem          Size  Used Avail Use% Mounted on 
 udev                7.8G  4.0K  7.8G   1% /dev 
 tmpfs               1.6G  1.1M  1.6G   1% /run 
 /dev/dm-1           901G  580G  276G  68% / 
 none                4.0K     0  4.0K   0% /sys/fs/cgroup 
 none                5.0M     0  5.0M   0% /run/lock 
 none                7.8G  160K  7.8G   1% /run/shm 
 none                100M   40K  100M   1% /run/user 
 /dev/sda1           236M   97M  127M  44% /boot 
 /home/abc/.Private  901G  580G  276G  68% /home/abc 
```
 

 ```
**df -i **
 Filesystem           Inodes  IUsed    IFree IUse% Mounted on 
 udev                2034397    490  2033907    1% /dev 
 tmpfs               2038328    519  2037809    1% /run 
 /dev/dm-1          59990016 567113 59422903    1% / 
 none                2038328      2  2038326    1% /sys/fs/cgroup 
 none                2038328      2  2038326    1% /run/lock 
 none                2038328      8  2038320    1% /run/shm 
 none                2038328     27  2038301    1% /run/user 
 /dev/sda1             62248    309    61939    1% /boot 
 /home/abc/.Private 59990016 567113 59422903    1% /home/abc 
```
 

 ```
**dpkg -l | grep linux **
 ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries 
 ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries 
 ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries 
 ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library 
 ii  linux-firmware                                        1.127.20                                            all          Firmware for Linux kernel drivers 
 ii  linux-generic                                         3.13.0.83.89                                        amd64        Complete Generic Linux kernel and headers 
 ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0 
 ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-headers-generic                                 3.13.0.83.89                                        amd64        Generic Linux kernel headers 
 ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP 
 ii  linux-image-generic                                   3.13.0.83.89                                        amd64        Generic Linux kernel image 
 ii  linux-signed-generic                                  3.13.0.83.89                                        amd64        Complete Signed Generic Linux kernel and headers 
 ii  linux-signed-image-3.13.0-79-generic                  3.13.0-79.123                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-3.13.0-83-generic                  3.13.0-83.127                                       amd64        Signed kernel image generic 
 ii  linux-signed-image-generic                            3.13.0.83.89                                        amd64        Signed Generic Linux kernel image 
 ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems 
 ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client 
 ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders 
 ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files) 
 ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies 
 ii  util-linux                                            2.20.1-5.1ubuntu20.7                                amd64        Miscellaneous system utilities 
```
 

 ```
**sudo apt update **
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                   
 Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                               
 Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                   
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                 
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                             
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources              
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources              
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]          
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages             
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                   
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages         
 Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                  
 Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                         
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [34.4 kB]     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages          
 Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B]   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en             
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [448 kB]   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources            
 Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources              
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources            
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                      
 Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages     
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                         
 Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,991 B] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages 
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [422 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages      
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en 
 Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en 
 Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                   
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources         
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US              
 Fetched 1,374 kB in 7s (185 kB/s)                                               
 Reading package lists... Done
``` 
 

 ```
**sudo apt upgrade **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```
 

 ```
**sudo apt-get autoclean **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done
```
 

 ```
**sudo apt-get clean**
 *[No output from this command]*
```
 

 ```
**sudo apt-get autoremove **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```
 

 ```
**sudo apt-get -f install **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2016-03-29
bonzo2; Hey !

You are finer than a frog's hair .. and that fat lady is sing'n your song !

As to expanding /boot ... oh boy ... that "can" be a can of worms. I strongly advocate leave well enough alone. The only time that /boot filling up is with new kernel installs ... it is no big deal at all to do terminal command
```

sudo apt-get autoremove

```
once you have verified that the new kernel boots and functions .

As of now, I do consider this little incident as "taken care of" .
I am open to any closing remarks or ANY questions in this regard, what we did, when and why .
 When you are ready though; Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]uh huh
[INDENT][INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
Hi there Bash,

Well the fat lady sung so loudly that the dog ran under the bed!

Couple of closing questions:

(1) Mindful that a bug was involved with my issue, did I personally contribute to the problem?  (I don't want to repeat bad behaviors!)

(2) Is the bottom line here that some files were only partially installed because they couldn't fit in the teeny partition?

(3) How does an Ubuntu forum member officially show immense gratitude?  Is there a system in place for that? If there are any lurkers around, please jump in! Bash seems very humble to me.

What a fantastic mood I'm in thanks to your good spirit and Ubuntu prowess.

Much gratitude,
Bonzo

---

### Post by Bashing-om on 2016-03-29
bonzo2; Wheeelll

1) Nope: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

2) Yeah .. The package manager attempted to install the -83 kernel .. no room to do so and not enough head room to operate in and broke the package management system . Once started there was no return without manually intervening and giving the package manager a bit of help .

3) Your appreciation of a job well done, and the assurance that this operating system of our choice is well supported is gratification enough. Payment is pass it on down the line. Others can benefit soon from your acquired knowledge.

[INDENT][INDENT]this is ubuntu
[INDENT][INDENT][INDENT]open source at it's best
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bonzo2 on 2016-03-29
You've got some class, Bash. 

I certainly will pay it forward and you, fine sir/madam, have sparked my interest in learning more.  

Ubuntu IS open source at it's finest.



Glad to be aboard!
Bonzo
```
**):P**
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You 
Thank You Thank You Thank You Thank You Thank You Thank You [SIZE=7][SIZE=3]
[/SIZE][/SIZE]Thank You Thank You Thank You Thank You Thank You Thank You
```

---

### Post by Bashing-om on 2016-03-29
bonzo2; :)


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

