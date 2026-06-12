---
title: "Unable to update linux-image 2.6.35-28 kernel"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by kopiluac on 2011-04-23
Hope this is the best place to post this issue in the forums.

Recently, I encountered a problem updating my kernel for ubuntu 10.10: linux-image-2.6.35-28-generic. Any time I attempt to install software or otherwise update my Ubuntu, I'm getting the following error: "The installation or removal of a software package failed." Also: "dpkg: error processing linux-image-2.6.35-28-generic (--configure): subprocess installed post-installation script returned error exit status 2"
So far apt-get commands are completely useless for trying to correct this issue.
 Details are below. Any and all suggestions are welcome. Thank you.

```
installArchives() failed: (Reading database ...  (Reading database ...  5% (Reading database ... 10% (Reading database ... 15% (Reading database  ... 20% (Reading database ... 25% (Reading database ... 30% (Reading  database ... 35% (Reading database ... 40% (Reading database ...  45% (Reading database ... 50% (Reading database ... 55% (Reading  database ... 60% (Reading database ... 65% (Reading database ...  70% (Reading database ... 75% (Reading database ... 80% (Reading  database ... 85% (Reading database ... 90% (Reading database ...  95% (Reading database ... 100% (Reading database ... 194807 files and  directories currently installed.) 
Preparing to replace libtiff4-dev 3.9.4-2ubuntu0.3 (using .../libtiff4-dev_3.9.4-2ubuntu0.4_amd64.deb) ... 
Unpacking replacement libtiff4-dev ... 
Preparing to replace libtiffxx0c2 3.9.4-2ubuntu0.3 (using .../libtiffxx0c2_3.9.4-2ubuntu0.4_amd64.deb) ... 
Unpacking replacement libtiffxx0c2 ... 
Preparing to replace libtiff4 3.9.4-2ubuntu0.3 (using .../libtiff4_3.9.4-2ubuntu0.4_amd64.deb) ... 
Unpacking replacement libtiff4 ... 
Processing triggers for man-db ... 
Setting up linux-image-2.6.35-28-generic (2.6.35-28.50) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-28.49 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-28.49 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
 * dkms: running auto installation service for kernel 2.6.35-28-generic         
 *       fglrx (8.780)...         [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
/etc/default/grub: 9: quiet: not found 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-28-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libtiff4 (3.9.4-2ubuntu0.4) ... 
No apport report written because MaxReports is reached already
Setting up libtiffxx0c2 (3.9.4-2ubuntu0.4) ... 
Setting up libtiff4-dev (3.9.4-2ubuntu0.4) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-2.6.35-28-generic 
Setting up linux-image-2.6.35-28-generic (2.6.35-28.50) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-28.49 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-28.49 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
 * dkms: running auto installation service for kernel 2.6.35-28-generic         
 *       fglrx (8.780)...         [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
/etc/default/grub: 9: quiet: not found 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-28-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 

```

---

### Post by mörgæs on 2011-04-23
I think you should boot the machine and try 

```

sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by kopiluac on 2011-04-23
Thanks, but I've already tried both those commands (as well as some others) from terminal with no change in the kernel. I've even tried booting into the previous kernel, updating and then rebooting into the original kernel afterward. In both cases synaptic continues to throw the same error. It does appear to still download and install my security updates, but I'm afraid that with this kernel being screwed up, dpkg is more and more jacked every time I do an update or install a new app. 

Further suggestions?

---

### Post by KegHead on 2011-04-23
Hi!

This works for me:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo aptitude install linux-image -f

or

sudo apt-get install linux-image -f

Please advise

KegHead

---

### Post by kopiluac on 2011-04-24
Thanks for the reply. As I said, apt-get commands have been futile for some reason. They simply aren't working and I'm too much of a noob to understand why. Here's the reoccurring error from terminal:

```
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image (2.6.35.28.36) ...
Errors were encountered while processing:
 linux-image-2.6.35-28-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If you require more detailed information, let me know and I'll run these again from command line and paste the results. 

Thanks so  much.

---

### Post by KegHead on 2011-04-25
OK,

Try the following:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.12-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.12-maverick/)

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

KegHead

---

### Post by matt_symes on 2011-04-25
Hi

```
etc/default/grub: 9: quiet: not found 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-28-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2
```

You are missing a grub file. Open a terminal and type 

```
sudo touch /etc/default/grub
```

Then try to reconfigure again. That may work, maybe not. If not you will need to get the grub file from somewhere and put in /etc/default directory. This is mine...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Kind regards

---

### Post by kopiluac on 2011-04-27
You were right. Found this thread earlier:
 [http://forums.linuxmint.com/viewtopic.php?f=18&t=68802&p=397986](http://forums.linuxmint.com/viewtopic.php?f=18&t=68802&p=397986)
 
which details the fix. But I couldn't decipher it completely and was afraid of screwing with grub anyway. A good friend of mine prescribed these commands and they resolved the issue easily.

[COLOR=Sienna]sudo[/COLOR] [COLOR=#990000]mv /etc/default/grub /etc/default/grub.bak
sudo [/COLOR][COLOR=#990000]cp /usr/share/grub/default/grub /etc/default/
sudo [/COLOR][COLOR=#990000]update-grub

[COLOR=Black]Will mark this thread "SOLVED!"

Thanks so much for your help.
[/COLOR]

[/COLOR]

---

### Post by mörgæs on 2011-04-27
Good that you got it fixed. 
'Solved' is in the 'thread tools' menu.

---

### Post by kopiluac on 2011-04-27
Thanks. Got it marked in thread tools now.
Have a great day!

---

