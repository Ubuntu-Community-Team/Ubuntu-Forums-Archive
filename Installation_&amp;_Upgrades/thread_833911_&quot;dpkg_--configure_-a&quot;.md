---
title: "&quot;dpkg --configure -a&quot;"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by krsgypsy on 2008-06-19
when i receive the "updates available" icon in the notification tray, i click on it and go to the update manager.  from there i click "install updates".  this is when i receive the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i then go to the terminal and type "dpkg --configure -a" then hit the enter key.  thats when i receive the following message:

dpkg: requested operation requires superuser privilege


what do i do next?  what is a superuser?  this is my computer and i'm the one with the passwords, right?  doesn't that make me super enough ;D

thanks.   - kirt

---

### Post by iaculallad on 2008-06-19
As per instruction, you should do dpkg --configure -a but with sudo.

```
sudo dpkg --configure -a
```

---

### Post by krsgypsy on 2008-06-19
ok.  tried the command with "sudo" before it and (of course) it worked...but, a new problem.  this is the message i get:  


Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-18-generic (2.6.24-18.26) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by iaculallad on 2008-06-19
Post the output of:

```
df -h
```

Or better yet, try to clean your system first:

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hagantic42 on 2008-06-19
The apt get clean apt get autoremove didn't work for me. But, manually removing the files in /boot did. I used cd /boot then ls and then using the sudo rm command to manually remove previous kernal files worked.(by previous i mean all files with lower numbers) It freed up space for the "dpkg --configure -a" command to do its job  
hopes this helps

---

### Post by krsgypsy on 2008-06-23
ok, i typed "df -h" in the terminal & this is what i got in response:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             1.9G  639M  1.2G  36% /
varrun                505M  104K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   88K  505M   1% /dev
devshm                505M   12K  505M   1% /dev/shm
lrm                   505M   38M  468M   8% /lib/modules/2.6.24-18-generic/volatile
/dev/sda1              92M   87M  140K 100% /boot
/dev/sda9              49G   22G   26G  46% /home
/dev/sda8             9.4G  150M  8.8G   2% /opt
/dev/sda7             958M   18M  892M   2% /tmp
/dev/sda5             9.4G  2.8G  6.2G  31% /usr
/dev/sda6             1.9G  293M  1.5G  17% /var


i'm new to linux and not certain what most of this means.  any ideas?

i then typed "sudo apt-get clean".  i entered my password, then was returned to the prompt:

kirt@kirt-laptop:~$ sudo apt-get clean
[sudo] password for kirt:
kirt@kirt-laptop:~$ 

i then typed "sudo apt-get autoremove" but was told:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

back to square one?

i could try manually deleting from the /boot directory as suggested by hagantic42 but, am not confident enough in my ability to recognize which files are older or unnecessary.  these are the files in the /boot directory:

/boot/abi-2.6.20-16-generic
/boot/abi-2.6.22-14-generic
/boot/abi-2.6.24-16-generic
/boot/abi-2.6.24-17-generic
/boot/abi-2.6.24-18-generic
/boot/config-2.6.20-16-generic
/boot/config-2.6.22-14-generic
/boot/config-2.6.24-16-generic
/boot/config-2.6.24-17-generic
/boot/config-2.6.24-18-generic
/boot/initrd.img-2.6.20-16-generic
/boot/initrd.img-2.6.20-16-generic.bak
/boot/initrd.img-2.6.22-14-generic
/boot/initrd.img-2.6.22-14-generic.bak
/boot/initrd.img-2.6.24-16-generic
/boot/initrd.img-2.6.24-16-generic.bak
/boot/initrd.img-2.6.24-17-generic
/boot/initrd.img-2.6.24-17-generic.bak
/boot/initrd.img-2.6.24-18-generic
/boot/memtest86+.bin
/boot/System.map-2.6.20-16-generic
/boot/System.map-2.6.22-14-generic
/boot/System.map-2.6.24-16-generic
/boot/System.map-2.6.24-17-generic
/boot/System.map-2.6.24-18-generic
/boot/vmlinuz-2.6.20-16-generic
/boot/vmlinuz-2.6.22-14-generic
/boot/vmlinuz-2.6.24-16-generic
/boot/vmlinuz-2.6.24-17-generic
/boot/vmlinuz-2.6.24-18-generic

there are also two folders titled "grub" & " lost & found"

what do you think?  thanks.   -kirt

---

### Post by iaculallad on 2008-06-23
Try removing your OLD linux kernels using the Synaptics Package Manager. Try to search for the "linux-image" string (w/o quote) and delete the old ones to free spaces on your /boot directory and try retry the commands below:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

and try to delete the BAK files on your /boot directory.

---

### Post by krsgypsy on 2008-06-23
i tried opening the synaptic package manager but i got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-06-23
Launch your terminal and try to do this:

-Change directory to your boot directory:

```
cd /boot
```

-While in your /boot directory, issue the command below to delete the .bak files to some space.

```
sudo rm *.bak
```

-Re-issue the dpkg command:

```
sudo dpkg --configure -a
```

-Then try to open your Synaptics.

---

### Post by krsgypsy on 2008-06-23
ok, i followed these steps:

> **iaculallad said:**
> Launch your terminal and try to do this:

-Change directory to your boot directory:

```
cd /boot
```

-While in your /boot directory, issue the command below to delete the .bak files to some space.

```
sudo rm *.bak
```

-Re-issue the dpkg command:

```
sudo dpkg --configure -a
```

-Then try to open your Synaptics.

i am now in the synaptic package manager and have searched for "linux-image".  i have a list of files now but am not certain which files to remove.  i understand that i am supposed to remove the old files but i'm not sure which are old.

---

### Post by iaculallad on 2008-06-23
> **krsgypsy said:**
> ok, i followed these steps:



i am now in the synaptic package manager and have searched for "linux-image".  i have a list of files now but am not certain which files to remove.  i understand that i am supposed to remove the old files but i'm not sure which are old.

In order for you to see what kernel you're using, open your terminal and issue the command:

```
uname -a
```

That command will list your current kernel file and that's the one that will remain in your Synaptics. Mark the OLD kernels as "Mark for Complete Removal" and click on apply.

---

### Post by krsgypsy on 2008-06-23
i tried installing the updates from the package manager and was successful.  thank you very much for your time and help.  -kirt

---

### Post by iaculallad on 2008-06-23
> **krsgypsy said:**
> i tried installing the updates from the package manager and was successful.  thank you very much for your time and help.  -kirt

You're welcome. Go Ubuntu

---

### Post by flowdawg on 2008-06-24
Hi all,

Having the same problem, with this error message, I tried following these steps, but somehow it doesn't work for me. I suspect, dpkg thinks it needs to configure this kernel image, but there is no such package. Is there a way to reset dpkg, so it gets a clean slate?

```
flwidmer@flaptop-mk2:~$ cd /boot/
flwidmer@flaptop-mk2:/boot$ ls
abi-2.6.24-16-generic         memtest86+.bin
config-2.6.24-16-generic      System.map-2.6.24-16-generic
grub                          vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic
flwidmer@flaptop-mk2:/boot$ sudo dpkg --configure -a
Richte initramfs-tools ein (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25
Cannot find /lib/modules/2.6.25
update-initramfs: failed for /boot/initrd.img-2.6.25
dpkg: Unterprozess post-installation script gab den Fehlerwert 1 zurück
flwidmer@flaptop-mk2:/boot$ dpkg -l|grep linux-image
ii  linux-image-2.6.24-16-generic              2.6.24-16.30                                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.16.18                                       Generic Linux kernel image


```

---

