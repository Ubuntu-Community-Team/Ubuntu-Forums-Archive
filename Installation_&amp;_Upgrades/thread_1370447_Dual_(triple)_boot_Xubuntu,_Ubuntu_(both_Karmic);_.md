---
title: "Dual (triple) boot Xubuntu, Ubuntu (both Karmic); XP; Grub/Grub 2"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Schaeufele on 2010-01-02
Hello there,

I have the following problem:

I had Win XP (seldomly used) and Ubuntu 9.10 (Karmic) as update from 9.04 (Jaunty) as update from 8.10 (Intrepid) as update from 8.04 (Hardy).
As my laptop is fairly vintage (Toshiba Satellite 3000-1GB) I thought of trying out Xubuntu 9.01 (Karmic). So I went ahead and installed it on a new partition of my harddisk. 
After installation GRUB worked fine, showing me a list of Xubuntu, Ubuntu and XP along with some other option (memtest et al). However. Ubuntu was no longer the default system so I tried to change it in Ubuntu using the StartUp-Manager. This did not display Xubuntu and after some looking around I klicked on "Restore old settings" (or something like that) which then lead to Karmic disappearing.
I then rebooted into Xubuntu (Karmic)  and after looking around in various forums updated to GRUB 2 using the terminal. In the process I was told that "grub-pc" had been uninstalled.
On rebooting Ubuntu is now gone from the GRUB menue completely, Xubuntu and XP are still there.

I have attached the output of the boot-info script. Below is the output of sudo fdisk -l:

---
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3649    29310561    7  HPFS/NTFS
/dev/sda2            3650       10638    56139142+   f  W95 Ext'd (LBA)
/dev/sda5            6082        9422    26836551    7  HPFS/NTFS
/dev/sda6            3650        5959    18555012   83  Linux
/dev/sda7            5960        6081      979933+  82  Linux swap / Solaris
/dev/sda8            9423       10638     9767488+  83  Linux
---

sda2: WinXP
sda5: NTFS data partition shared between Linux and WinXP
sda6: Ubuntu 9.10 (Karmic)
sda7: Swap partition supposedly used by both Ubuntu and Xubuntu
sda8: Xubuntu 9.10 (Karmic)

Another bit of info is, that all sda's could be mounted under Ubuntu, but not under Xubuntu. Under Xubuntu only sda8 can be mounted. When trying to mount any of the other sdas (sudo mount /dev/sda?) I get the following errors:

---
mount: can't find /dev/sda? in /etc/fstab or /etc/mtab
---

When I encountered this problem the first time in Xubuntu, I installed ntfsprogs via Synaptic Manager and that worked once. After rebooting it has has never worked again, even after reinstalling ntfsprogs with Synaptic. 

[B][I]What I want to achieve is the following:
[/I][/B] 
On boot GRUB should display Ubuntu 9.10 as the default OS, then Xubuntu 9.10 as the next one; and WinXP and memtest et al in the back.
Alternatively I'd like to get rid of Xubuntu again as I have found no difference in speed between Ubuntu and Xubuntu and have Ubuntu and XP (and memtest et al) in GRUB. 

Can anyone help?

Kind regards
Schaeufele

---

### Post by kansasnoob on 2010-01-02
> **Schaeufele said:**
> Hello there,

I have the following problem:

I had Win XP (seldomly used) and Ubuntu 9.10 (Karmic) as update from 9.04 (Jaunty) as update from 8.10 (Intrepid) as update from 8.04 (Hardy).
As my laptop is fairly vintage (Toshiba Satellite 3000-1GB) I thought of trying out Xubuntu 9.01 (Karmic). So I went ahead and installed it on a new partition of my harddisk. 
After installation GRUB worked fine, showing me a list of Xubuntu, Ubuntu and XP along with some other option (memtest et al). However. Ubuntu was no longer the default system so I tried to change it in Ubuntu using the StartUp-Manager. This did not display Xubuntu and after some looking around I klicked on "Restore old settings" (or something like that) which then lead to Karmic disappearing.
I then rebooted into Xubuntu (Karmic)  and after looking around in various forums updated to GRUB 2 using the terminal. In the process I was told that "grub-pc" had been uninstalled.
On rebooting Ubuntu is now gone from the GRUB menue completely, Xubuntu and XP are still there.

I have attached the output of the boot-info script. Below is the output of sudo fdisk -l:

---
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3649    29310561    7  HPFS/NTFS
/dev/sda2            3650       10638    56139142+   f  W95 Ext'd (LBA)
/dev/sda5            6082        9422    26836551    7  HPFS/NTFS
/dev/sda6            3650        5959    18555012   83  Linux
/dev/sda7            5960        6081      979933+  82  Linux swap / Solaris
/dev/sda8            9423       10638     9767488+  83  Linux
---

sda2: WinXP
sda5: NTFS data partition shared between Linux and WinXP
sda6: Ubuntu 9.10 (Karmic)
sda7: Swap partition supposedly used by both Ubuntu and Xubuntu
sda8: Xubuntu 9.10 (Karmic)

Another bit of info is, that all sda's could be mounted under Ubuntu, but not under Xubuntu. Under Xubuntu only sda8 can be mounted. When trying to mount any of the other sdas (sudo mount /dev/sda?) I get the following errors:

---
mount: can't find /dev/sda? in /etc/fstab or /etc/mtab
---

When I encountered this problem the first time in Xubuntu, I installed ntfsprogs via Synaptic Manager and that worked once. After rebooting it has has never worked again, even after reinstalling ntfsprogs with Synaptic. 

[B][I]What I want to achieve is the following:
[/I][/B] 
On boot GRUB should display Ubuntu 9.10 as the default OS, then Xubuntu 9.10 as the next one; and WinXP and memtest et al in the back.
Alternatively I'd like to get rid of Xubuntu again as I have found no difference in speed between Ubuntu and Xubuntu and have Ubuntu and XP (and memtest et al) in GRUB. 

Can anyone help?

Kind regards
Schaeufele

Wow, lots of goofy things here (BTW XP is on sda1 not sda2):

First of all regarding your old Ubuntu (I think the older one would be on sda6), even though it's recognized as 9.10 the menu.lst still shows 8.10 and the old kernel.

Then the newer install on sda8 contains both legacy grub and grub2 files/dirs.

So I think we should hand boot back to the older Ubuntu on sda6. What do you think?

I'd also like to upgrade it to grub2 (my way, not the automated way that mixes files). What do you think of that?

If you prefer keeping legacy grub we can do that too.

---

### Post by Schaeufele on 2010-01-02
Hi Kansasnoob,

Thank you for your reply, much appreciated, I gather there is hope even for me... :-)

>So I think we should hand boot back to the older Ubuntu on sda6. What do you think?

That is the intention really. But how?

>I'd also like to upgrade it to grub2 (my way, not the automated way that mixes files). What do you think of 
>that?

Great idea, would be all for that. Again, how do I do that?

Best regards
Schaeufele

---

### Post by kansasnoob on 2010-01-02
**First and foremost tell me you have an Ubuntu Live CD! If not don't proceed!** I'd also like to know what the newest version and flavor of Ubuntu Live CD you have is.

Please copy-n-paste these commands either using the Live CD or booted into your (X)ubuntu (we'll talk about that more later). Also do me a big favor and post the entire text of the terminal here just in case something goes wrong!

First we need to mount and chroot sda6:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now we'll backup the old grub directory and do the package changes, install grub, etc:

```
mv /boot/grub /boot/grub_legacy
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub grub-common
```

```
apt-get update && apt-get install grub-pc
```

```
grub-install /dev/sda
```

```
update-grub
```

Wait until it says, "done". It will only find itself **not XP or the other *buntu**, that's normal we'll take care of that on the initial boot!

Now we'll exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Don't worry about errors following that last command.

Now you can reboot, and as I said above you'll only be able to boot Ubuntu, in fact you probably won't even see the menu. BTW in grub2 if the menu is hidden and you need to see it you have to press the space bar rather than the Esc key as you did in legacy grub.

Anyway after the first boot go to terminal and run:

```
sudo update-grub
```

Again, wait until it says, done. That should find both XP and the other *buntu. Then we'll work from there on some other issues.

If this fails for any reason we'll revert back to your legacy grub, OK? It's honestly not difficult :)

Also I want to see the output of:

```
sudo parted /dev/sda print
```

---

### Post by kansasnoob on 2010-01-02
BTW if all goes well I'd expect to see a ridiculously long list of kernels associated with your old Ubuntu. That's good! Just be patient and we'll hack away at this a chunk at a time.

---

### Post by Schaeufele on 2010-01-02
>**First and foremost tell me you have an Ubuntu Live CD! If not don't proceed!** I'd also like to know 
>what the newest version and flavor of Ubuntu Live CD you have is.

Ok, I have a live CD containing Xubuntu 9.10 (Karmic). I made that one yesterday and used it install Xubuntu.
 So I will now make an Ubuntu 9.10 (Karmic) live CD as well and then follow your instructions (downloading already).

>Please copy-n-paste these commands either using the Live CD or booted into your (X)ubuntu (we'll talk 
>about that more later). Also do me a big favor and post the entire text of the terminal here just in case 
>something goes wrong!

Ok, will do. Do you recommend using the live CD or rather using the booted system, i.e. Xubuntu?

---

### Post by Schaeufele on 2010-01-02
Ok, terminal log below:

---

jan@jan-laptop:~$ sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for jan: 
root@jan-laptop:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@jan-laptop:/# ln -s /bin/true /sbin/initctl
root@jan-laptop:/# mv /boot/grub /boot/grub_legacy
root@jan-laptop:/# mkdir /boot/grub
root@jan-laptop:/# apt-get --purge remove grub grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  grub* grub-common* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4,461kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 180836 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
root@jan-laptop:/# apt-get update && apt-get install grub-pc
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release.gpg                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [31.1kB]                        
Ign [http://les-ejk.cz](http://les-ejk.cz) jaunty Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://les-ejk.cz](http://les-ejk.cz) jaunty/multiverse Translation-en_GB
Ign [http://les-ejk.cz](http://les-ejk.cz) jaunty Release
Ign [http://les-ejk.cz](http://les-ejk.cz) jaunty/multiverse Packages
Ign [http://les-ejk.cz](http://les-ejk.cz) jaunty/multiverse Packages
Hit [http://les-ejk.cz](http://les-ejk.cz) jaunty/multiverse Packages
Fetched 308B in 2s (146B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5227BEBD68436DDF
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 434kB/1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]
Fetched 434kB in 0s (603kB/s)   
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 180641 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...

Creating config file /etc/default/grub with new version

root@jan-laptop:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@jan-laptop:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@jan-laptop:/# exit
exit
jan@jan-laptop:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
jan@jan-laptop:~$

---

### Post by Schaeufele on 2010-01-02
Hi Kansasnoob,

Ok, rebooted and as you suspected there was no grub menue. So I pressed space, did not see any menue come up. BUT Ubuntu (not Xubuntu) than came up. I logged in under my Username and my usual desktop appeared, however, only to completely crash after a few seconds. The screen completely crashed (only some coloured blocks) and in the end there was only a blinking cursor.
So I rebooted again and this time the grub menue appeared showing kernels 16, 15, 14 and 16 again. No WinXP. I chose kernel 16 and logged in as before and the machine crashed as before.
I then tried kernel 16 in recovery mode, this got me halfway through the boot process and then got stuck.
After that I tried kernel 14 (not recovery mode) and was able to log in again only to crash again after a few seconds as above.

Currently I am using the Xubuntu 9.10 (Karmic) live CD.

What's next now? :confused:

Best regards
Schaeufele

---

### Post by Schaeufele on 2010-01-02
Just tried the remaining commands and here is the terminal log:

---

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD1200BEVE-0 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  30.0GB  30.0GB  primary   ntfs            boot
 2      30.0GB  87.5GB  57.5GB  extended                  lba
 6      30.0GB  49.0GB  19.0GB  logical   ext3
 7      49.0GB  50.0GB  1003MB  logical   linux-swap(v1)
 5      50.0GB  77.5GB  27.5GB  logical   ntfs
 8      77.5GB  87.5GB  10.0GB  logical   ext3

ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2010-01-02
So can you boot into your old Ubuntu?

It looks like you should, if so run:

```
sudo update-grub
```

to pick up XP and Xubuntu.

Then we can look at other tweaks.

---

### Post by kansasnoob on 2010-01-02
> ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

That's typical from the Live CD. You must be booted into the OS when you run "update-grub" for grub2 to pick up the other operating systems.

As far as your machine crashing on the new kernels give me just a minute. That's why I didn't want to remove the newer Xubuntu just yet!

Remember I noticed that you were still booting the old Intrepid kernel in legacy grub.

Give me a few minutes to gather my thoughts.

---

### Post by Schaeufele on 2010-01-02
> **kansasnoob said:**
> 

Remember I noticed that you were still booting the old Intrepid kernel in legacy grub.

Give me a few minutes to gather my thoughts.

Well, before installing Xubuntu and going through the process I described earlier (hitting the "restore old" button in StartUp Manager), the grub menue displayed the "new" kernels for Xubuntu and Ubuntu on sda6. So I do believe that I was running on kernels 14, 15 or 16. Only after screwing up grub with StartUp Manager the 8.XXXXX appeared. I then updated grub under Xubuntu and then only Xubuntu could be booted. 
Where does grub get the kernel info from?

---

### Post by kansasnoob on 2010-01-02
First you did nothing wrong, we should be able to sort this out!

Lets start by getting you booting the Xubuntu as I'd assume that's easier and faster to work with than the Live CD (basically similar steps as before), from the Live CD:

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc
```

```
grub-install /dev/sda
```

If that returns any errors:

```
grub-install --recheck /dev/sda
```

As before exit and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc
```

That should get you back to where we started, that is booting only Xubuntu and XP.

Then I'll start explaining what's going on and we'll find a solution.

---

### Post by Schaeufele on 2010-01-02
Hmm, running into problems with grub-install:

---

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ grub-install /dev/sda
cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-install --recheck /dev/sda
rm: cannot remove `/boot/grub/device.map': Permission denied
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 

---

I am still running Xubuntu from the live CD.

---

### Post by kansasnoob on 2010-01-02
> **Schaeufele said:**
> Well, before installing Xubuntu and going through the process I described earlier (hitting the "restore old" button in StartUp Manager), the grub menue displayed the "new" kernels for Xubuntu and Ubuntu on sda6. So I do believe that I was running on kernels 14, 15 or 16. Only after screwing up grub with StartUp Manager the 8.XXXXX appeared. I then updated grub under Xubuntu and then only Xubuntu could be booted. 
Where does grub get the kernel info from?

Well according to the menu.lst from "old-ubuntu":

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
```

You were still booting the Intrepid kernel 2.6.27-*. And even the new-xubuntu grub2 saw it as Intrepid:

```
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638
	linux /boot/memtest86+.bin 
```

Lets just concentrate on sorting things out one thing at a time. I'll post some more info in a moment.

And BTW the Intrepid kernel was 2.6.27-*, Jaunty is 2.6.28-*, and Karmic is 2.6.31-*.

---

### Post by kansasnoob on 2010-01-02
> **Schaeufele said:**
> Hmm, running into problems with grub-install:

---

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ grub-install /dev/sda
cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ grub-install --recheck /dev/sda
rm: cannot remove `/boot/grub/device.map': Permission denied
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 

---

I am still running Xubuntu from the live CD.

I goofed!!!!!!!!! Sorry:(

I left out the chroot part, so do this:

```
sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

If needed:

```
grub-install --recheck /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc
```

---

### Post by Schaeufele on 2010-01-02
Hmm, no success, please see below:

---

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda8 already mounted or /mnt busy
mount: according to mtab, /dev/sda8 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ grub-install --recheck /dev/sda
rm: cannot remove `/boot/grub/device.map': Permission denied
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 

---

---

### Post by kansasnoob on 2010-01-02
I goof more often when I get in a hurry.

I think it would be helpful for you to understand that mount and chroot process:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

That hardly explains it all, but sometimes it's not ALL needed so I type it and unfortunately goof :(

Anyway for now I want to get you booting the new Xubuntu and I want to explain some of the problems with the older Ubuntu so we can try to sort it out.

When you ran apt-get update while chroot in "old-ubuntu" there were several errors due to there still being some Jaunty repos. I guess we need to figure that out, but the question still lingers - why were you still booting an Intrepid kernel after upgrading to Jaunty and then to Karmic?

I'm also curious why the new Xubuntu had both legacy grub and grub2 files if it was a fresh install? I thought all fresh installs of Ubuntu Karmic had grub2 by default, maybe not so with Xubuntu.

---

### Post by kansasnoob on 2010-01-02
> **Schaeufele said:**
> Hmm, no success, please see below:

---

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda8 already mounted or /mnt busy
mount: according to mtab, /dev/sda8 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ grub-install --recheck /dev/sda
rm: cannot remove `/boot/grub/device.map': Permission denied
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ 

---

Well, I'm too slow posting. You were mounted but I left out the chroot part so individually:

```
sudo mount /dev/sda8 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo chroot /mnt
```

Then:

```
grub-install /dev/sda
```

```
grub-install --recheck /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc
```

Since I do this every day I sometimes forget others don't know what to do after an error, sorry :(

---

### Post by kansasnoob on 2010-01-02
Sorry for the boo-boo there. You see that was all because I left off the chroot part of that and, of course, if the computer were right in front of me I'd say oops, and just add that.

Since you weren't totally unmounted combining the commands with && fails and after one link in the command fails it all fails. That's why a proper script is written with a bunch of "if", "fi", etc.

Sorry again.

---

### Post by Schaeufele on 2010-01-02
Ok, here come my works:

---
ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda8 already mounted or /mnt busy
mount: according to mtab, /dev/sda8 is already mounted on /mnt
ubuntu@ubuntu:~$ grub-install /dev/sda
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ grub-install --recheck /dev/sda
rm: cannot remove `/boot/grub/device.map': Permission denied
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$ ls -l
total 0
drwxr-xr-x 2 ubuntu ubuntu 60 2010-01-02 19:16 Desktop
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Documents
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Downloads
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Music
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Pictures
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Public
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Templates
drwxr-xr-x 2 ubuntu ubuntu 40 2010-01-02 19:17 Videos
ubuntu@ubuntu:~$ cd ..
ubuntu@ubuntu:/home$ cd ..
ubuntu@ubuntu:/$ ls -l
total 6
drwxr-xr-x   2 root root 2435 2009-10-28 20:16 bin
drwxr-xr-x   4 root root   60 2009-10-28 20:19 boot
dr-xr-xr-x  10 root root 2048 2009-10-28 20:25 cdrom
drwxr-xr-x  15 root root 3840 2010-01-02 19:17 dev
drwxr-xr-x 139 root root  600 2010-01-02 20:49 etc
drwxr-xr-x   3 root root   60 2010-01-02 19:15 home
lrwxrwxrwx   1 root root   33 2009-10-28 20:11 initrd.img -> boot/initrd.img-2.6.31-14-generic
drwxr-xr-x  19 root root 5628 2009-10-28 20:16 lib
drwxr-xr-x   2 root root    3 2009-10-28 20:06 media
drwxr-xr-x  21 root root 4096 2010-01-01 22:28 mnt
drwxr-xr-x   2 root root    3 2009-10-28 20:06 opt
dr-xr-xr-x 141 root root    0 2010-01-02 19:15 proc
drwxr-xr-x  20 root root  317 2009-10-28 20:11 rofs
drwx------   2 root root   46 2009-10-28 20:06 root
drwxr-xr-x   2 root root 3540 2009-10-28 20:16 sbin
drwxr-xr-x   2 root root    3 2009-10-19 23:05 selinux
drwxr-xr-x   2 root root    3 2009-10-28 20:06 srv
drwxr-xr-x  12 root root    0 2010-01-02 19:15 sys
drwxrwxrwt   7 root root  200 2010-01-02 20:50 tmp
drwxr-xr-x  13 root root  100 2009-10-28 20:06 usr
drwxr-xr-x  19 root root  120 2009-10-28 20:12 var
lrwxrwxrwx   1 root root   30 2009-10-28 20:11 vmlinuz -> boot/vmlinuz-2.6.31-14-generic
ubuntu@ubuntu:/$ sudo mount /dev/sda8 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
mount: /dev/sda8 already mounted or /mnt busy
mount: according to mtab, /dev/sda8 is already mounted on /mnt
ubuntu@ubuntu:/$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# exit
exit
ubuntu@ubuntu:/$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc
umount: /mnt/dev/pts: not mounted
ubuntu@ubuntu:/$ sudo umount /mnt/dev/sda8 && sudo umount /mnt/dev && sudo umount /mnt/proc
umount: /mnt/dev/sda8: not mounted
ubuntu@ubuntu:/$ sudo umount /dev/sda8 && sudo umount /mnt/dev && sudo umount /mnt/proc
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:/$ cd /mnt/dev/pts
ubuntu@ubuntu:/mnt/dev/pts$ ls -l
total 0
ubuntu@ubuntu:/mnt/dev/pts$ sudo umount /mnt/dev/pts
umount: /mnt/dev/pts: not mounted
ubuntu@ubuntu:/mnt/dev/pts$ 

---

So I managed to install grub un sda8 (Xubuntu) it seems. Now let's reboot...

---

### Post by Schaeufele on 2010-01-02
Right, seems to have worked, I'm now back in Xubuntu booted from sda8. Seems to work fine. The system monitor tells me I am running kernel 2.6.31-16.

And now?  :-)

---

### Post by kansasnoob on 2010-01-02
It's time for a discussion. Sorry again for my boo-boo! Have you read what I said so far about your old Ubuntu?

If you look at the Boot Info script results you can see that you were still booting the Intrepid kernel, eh? I posted some about that previously so please take time to read back if necessary.

Now, **we're just discussing** at this point, so don't just jump into anything, OK?

As I said, if you look back at post #7:

[http://ubuntuforums.org/showpost.php?p=8598195&postcount=7](http://ubuntuforums.org/showpost.php?p=8598195&postcount=7)

You can see that there were several instances of Jaunty repos in there when you ran "apt-get update". That's not good.

**Now remember we're just discussing here!** Given the fact that your old Ubuntu was still booting an Intrepid kernel and was holding onto some Jaunty repos it appears that your old Ubuntu was somewhat borked.

Since you can boot the Karmic kernel in the new Xubuntu install I'm thinking we should go for broke and try to aggressively clean up the old Ubuntu through a "mount & chroot", starting by fixing the sources.list which requires using the nano text editor which can be confusing the first time around, and then trying an "apt-get dist-upgrade".

I'd give that a 50% chance of success at best! Maybe 80% if the computer were right in front of me.

Another option would be to try and get the Intrepid kernel to boot, but I think that's foolish. We should however consider what data you have to backup and such.

---

### Post by kansasnoob on 2010-01-02
Feel free to PM me using the forums.

Just keep it brief and point me back here or to another thread at the forums.

---

### Post by Schaeufele on 2010-01-02
>If you look at the Boot Info script results you can see that you were still booting the Intrepid kernel, eh? I 
>posted some about that previously so please take time to read back if necessary.

I am still of the opinion that the last time I checked (which may have been yesterday, but not sure) via System-Info that I was indeed running a Karmic kernel. The older kernels only reappeared when I klicked around in the StartUp-Manager. However, I am not an experienced user and may be on the wrong track here.

>You can see that there were several instances of Jaunty repos in there when you ran "apt-get update". 
>That's not good.

I have mounted sda6 (old Ubuntu) as you described earlier and included sources.list therefrom below:

---

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://les-ejk.cz/ubuntu](http://les-ejk.cz/ubuntu) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe multiverse
deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) jaunty main

---

Please disregard the Jaunty sources, these come from me trying to get my PC talk to my Garmin GPS. I needed these resource for that, however, in the end it did not work. This whole process involved quite a bit of installation and deinstallation, however, Ubuntu worked fine after that.

**>Now remember we're just discussing here!** Given the fact that your old Ubuntu was still booting an 
>Intrepid kernel and was holding onto some Jaunty repos it appears that your old Ubuntu was somewhat 
>borked.

You may be right there. :-)

>Since you can boot the Karmic kernel in the new Xubuntu install I'm thinking we should go for broke and 
>try to aggressively clean up the old Ubuntu through a "mount & chroot", starting by fixing the sources.list 
>which requires using the nano text editor which can be confusing the first time around, and then trying 
>an "apt-get dist-upgrade".

>I'd give that a 50% chance of success at best! Maybe 80% if the computer were right in front of me.

Well, I'd go if only for me learning. Provided that we do not damage WinXP which I need as a fallback position (and since I can't remember where I got half of the stuff installed in it from)!

>Another option would be to try and get the Intrepid kernel to boot, but I think that's foolish. We should 
>however consider what data you have to backup and such.

That I would also go for just to verify that my old Ubuntu indeed ran the Intrepid kernel. The data I have in *buntu is backed up already, so no worries there.

Let's go?

---

### Post by kansasnoob on 2010-01-02
Since you said this:

> I have mounted sda6 (old Ubuntu) as you described earlier and included sources.list therefrom below:

Given my earlier goof up (I apologize again) you've looked at this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And you managed to do a mount and chroot on your own. That's awesome!

That said I can't imagine anything you did in the new Xubuntu changing the Ubuntu menu.lst. We could look by doing a mount & chroot of sda6 from Xubuntu and running:

```
ls /boot/grub_legacy
```

Remember that's where we saved your old Ubuntu old /boot/grub files!

You could look around there for a menu.lst backup and see if it really ever updated to the Jaunty or Karmic kernel. I doubt it.

Sadly I'm old, and I'm tired, so I must basically give up for about 10 or 12 hours.

---

### Post by Schaeufele on 2010-01-02
Hello Kansasnoob,

Ok, I'll try that tomorrow, need to grab some sleep too now...

Thanks again for your help and will revert with the outcome!

Best regards
Schaeufele

---

### Post by Schaeufele on 2010-01-03
Hi kansasnoob,

Unfortunately I encountered another problem which necessitates me going back to windows before doing anything else to my system(s). As you will remember Xubuntu is working now, but wind is not in grub. How do I get it in there?

Best regards
Schaeufele

---

### Post by kansasnoob on 2010-01-03
> That I would also go for just to verify that my old Ubuntu indeed ran the Intrepid kernel. The data I have in *buntu is backed up already, so no worries there.

OK, we'll start by trying to get old Ubuntu to boot.

We can do that either one of two ways. I rather prefer #1, feel free to discuss this more if you'd like.

#1. We could hand boot back to sda6 again, only with the old legacy grub and the existing menu.lst. Remember we saved the old /boot/grub as /boot/grub_legacy so:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Note: that may show something like "already exists".

```
mv /boot/grub /boot/grub_backup
```

```
mv /boot/grub_legacy /boot/grub
```

```
apt-get --purge remove grub-pc
```

```
apt-get install grub
```

Note: if that fails you may need to "apt-get update && apt-get install grub" but we updated the package list yesterday so I doubt it.

```
grub-install /dev/sda
```

Now we'll need to use a grub shell:

```
grub
```

```
root (hd0,5)
```

```
setup (hd0)
```

Should show something like this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Then:

```
guit
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

#2. **(Only if you decided NOT to do #1) **You could run "sudo update-grub" in Xubuntu and see if it picks up the 2.6.27-11 kernel on sda6. If so you could just try to boot it and see what happens.

If "update-grub" fails to pick up that kernel you could add a custom entry to the Xubuntu grub.cfg by editing "/etc/grub.d/40_custom". We know what the old menu.lst entries were:

> title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7547643f-b9ba-4ee7-ad34-6f01d6ad7638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

Grub2 syntax is different so (if I get this right, remember grub2 is kind of new to all of us) we'd want to use gedit:

```
sudo gedit /etc/grub.d/40_custom
```

You should see:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

So just below that add:

```
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
```

Then of course click on Save & File > Quit. Then run:

```
sudo update-grub
```

So it gets added to the grub.cfg. If you choose this option I know we'll need to make other changes. This would be just a temporary move.

---

### Post by kansasnoob on 2010-01-03
> **Schaeufele said:**
> Hi kansasnoob,

Unfortunately I encountered another problem which necessitates me going back to windows before doing anything else to my system(s). As you will remember Xubuntu is working now, but wind is not in grub. How do I get it in there?

Best regards
Schaeufele

Should just be able to run:

```
sudo update-grub
```

in Xubuntu.

I was already typing when you posted :)

---

### Post by Schaeufele on 2010-01-03
Hmm, does not seem to have found WIndows:

---

an@jan-laptop:~$ sudo update-grub
[sudo] password for jan: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

---

---

### Post by kansasnoob on 2010-01-03
> **Schaeufele said:**
> Hmm, does not seem to have found WIndows:

---

an@jan-laptop:~$ sudo update-grub
[sudo] password for jan: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

---

Oh, I forgot that Xubuntu had a mix of both legacy grub and grub2 files. Since it found a menu.lst it won't update the grub2 files.

Did you already try to change old Ubuntu back to legacy grub as I instructed above? If so it should boot Windows OK.

If not we need to clean up the Xubuntu grub while booted into Xubuntu, but don't do this if you've already handed grub back to old Ubuntu:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

---

### Post by kansasnoob on 2010-01-03
If you follow those previous steps to fix grub2 in Xubuntu I'd like to see the output of:

```
cat /boot/grub/grub.cfg
```

Just to see what it recognizes in the old Ubuntu.

---

### Post by Schaeufele on 2010-01-03
Firstly I have left the boot on Xubuntu (sda8) and updated grub. This works fine now, all the desired option are there. I fixed the problem I had and for which I thought I needed WinXP by simply mounting the relevant XP parts into Xubuntu. I could then do the fixing there. Nice, eh?

Method #2 in post #29 worked, the options were added to the grub start menue. However, when trying them out on reboot, I get the error "Load kernel first". Then the grub menue appears again. Booting the "old" Ubuntu with the xx28xx kernel produced a hanging boot (the Ubuntu symbol just stays), booting with the Karmic kernel works but the system completely crashes after a few seconds as described earlier.

So, how do we fix this then? This is fun!  :-)

An here comes the grub.cfg (from before manually adding the 8.10 options):

                                       #
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    [LEFT]#[/LEFT]
    [LEFT]# It is automatically generated by /usr/sbin/grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    [LEFT]#[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s /boot/grub/grubenv ]; then[/LEFT]
    [LEFT]  have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ ${prev_saved_entry} ]; then[/LEFT]
    [LEFT]  saved_entry=${prev_saved_entry}[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root=(hd0,8)[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set 5e70f684-7bf1-47c9-af2a-0ab652542d06[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=640x480[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  if terminal_output gfxterm ; then true ; else[/LEFT]
    [LEFT]    # For backward compatibility with versions of terminal.mod that don't[/LEFT]
    [LEFT]    # understand terminal_output[/LEFT]
    [LEFT]    terminal gfxterm[/LEFT]
    [LEFT]  fi[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]if [ ${recordfail} = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/white[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-16-generic" {[/LEFT]
    [LEFT]        recordfail=1[/LEFT]
    [LEFT]        if [ -n ${have_grubenv} ]; then save_env recordfail; fi[/LEFT]
    [LEFT]    set quiet=1[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,8)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 5e70f684-7bf1-47c9-af2a-0ab652542d06[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5e70f684-7bf1-47c9-af2a-0ab652542d06 ro   quiet splash[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.31-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {[/LEFT]
    [LEFT]        recordfail=1[/LEFT]
    [LEFT]        if [ -n ${have_grubenv} ]; then save_env recordfail; fi[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,8)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 5e70f684-7bf1-47c9-af2a-0ab652542d06[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5e70f684-7bf1-47c9-af2a-0ab652542d06 ro single [/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.31-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-14-generic" {[/LEFT]
    [LEFT]        recordfail=1[/LEFT]
    [LEFT]        if [ -n ${have_grubenv} ]; then save_env recordfail; fi[/LEFT]
    [LEFT]    set quiet=1[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,8)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 5e70f684-7bf1-47c9-af2a-0ab652542d06[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5e70f684-7bf1-47c9-af2a-0ab652542d06 ro   quiet splash[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.31-14-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {[/LEFT]
    [LEFT]        recordfail=1[/LEFT]
    [LEFT]        if [ -n ${have_grubenv} ]; then save_env recordfail; fi[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,8)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 5e70f684-7bf1-47c9-af2a-0ab652542d06[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5e70f684-7bf1-47c9-af2a-0ab652542d06 ro single [/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.31-14-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {[/LEFT]
    [LEFT]    insmod ntfs[/LEFT]
    [LEFT]    set root=(hd0,1)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set d0a84e28a84e0d82[/LEFT]
    [LEFT]    drivemap -s (hd0) ${root}[/LEFT]
    [LEFT]    chainloader +1[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro grub-install /dev/sda quiet splash[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single grub-install /dev/sda[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro grub-install /dev/sda quiet splash[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-15-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single grub-install /dev/sda[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-15-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro grub-install /dev/sda quiet splash[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-14-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single grub-install /dev/sda[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.31-14-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.28-16-generic (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro grub-install /dev/sda quiet splash[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.28-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode) (on /dev/sda6)" {[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root=(hd0,6)[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638[/LEFT]
    [LEFT]    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single grub-install /dev/sda[/LEFT]
    [LEFT]    initrd /boot/initrd.img-2.6.28-16-generic[/LEFT]
    [LEFT]}[/LEFT]
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
        [LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]

---

### Post by kansasnoob on 2010-01-03
> Method #2 in post #29 worked, the options were added to the grub start menue. However, when trying them out on reboot, I get the error "Load kernel first". Then the grub menue appears again. Booting the "old" Ubuntu with the xx28xx kernel produced a hanging boot (the Ubuntu symbol just stays), booting with the Karmic kernel works but the system completely crashes after a few seconds as described earlier.

So, how do we fix this then? This is fun!

An here comes the grub.cfg (from before manually adding the 8.10 options):

Well, I'm glad we got Windows booting. As I said having both legacy grub and grub2 files/directories mixed keeps grub2 from updating properly. If grub2 is working properly you should hardly ever have to edit anything after the initial setup, maybe just run "sudo update-grub" occasionally to recognize a change.

Now remember it's kernel #2.6.27-11-generic in old Ubuntu that we're trying to boot. Since you said that grub.cfg was from before editing /etc/grub.d/40_custom I want you to run:

```
cat /boot/grub/grub.cfg
```

And just be sure the bottom of the list looks like this:

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 7547643f-b9ba-4ee7-ad34-6f01d6ad7638
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7547643f-b9ba-4ee7-ad34-6f01d6ad7638 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/40_custom ###

If that kernel does show up try booting it, that's not a fix but it would be a bit easier for both of us if we could work on old Ubuntu with it actually booted rather than working thru a chroot.

If you must work thru a chroot give this another look:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course you'll be mounting /dev/sda6 but remember what I say there:

> the commands below are just a string of commands connected by "space&&space" but if one part of the string fails it stops the whole process so if you encounter any failure message look at the list of individual commands
MOUNT:
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

REMEMBER: exit

UNMOUNT:
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

Anyway the first thing we need to do is get rid of those Jaunty repos in your Karmic sources.list. Having those in there really horses things up! If you can boot into old Ubuntu then you can use gedit:

```
sudo gedit /etc/apt/sources.list
```

And then you can either just comment out the Jaunty lines or remove them altogether. Gedit is fairly simple to use, just be careful and remember to Save, then File > Quit.

When I say "comment out" that means adding a # to the beginning of the line like in this sample you can see that "deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner" is commented out:

> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

If you can't get booted into old Ubuntu then you'll have to mount and chroot the rascal and use the nano text editor. Nano is OK once you're used to it but it can be confusing the first time around so please create a simple backup first by running:

```
cat /etc/apt/sources.list
```

That provides a "read only" version so copy-n-paste that somewhere in case you goof so you have a backup you can use just in case!

Note: You've probably already noticed that we don't need sudo when we're chroot because we are already root as indicated by the terminal prompt changing from "$" to "#".

So to edit that with nano in a chroot:

```
nano /etc/apt/sources.list
```

To navigate in nano you need to use the arrow keys. Using backspace, tab, or enter will hose things! You can paste into nano but you can't copy from it! So I'd just use "comments" (ie: #) as described above.

Be sure you've "arrowed" your way from top to bottom and commented out all of the Jaunty sources, then with the cursor all the way at the bottom press CTRL + x at the same time, then you'll be asked "Save modified buffer?":

[ATTACH]142360[/ATTACH]

I typed y for Yes and then I'm asked "File name to write: /etc/apt/sources.list" so I just hit enter:

[ATTACH]142361[/ATTACH]

Note: if you think you screwed up at any time usin nano just hit Ctrl + x as described above but then type n for No and the file should be unchanged, then you can start over again.

When you're done run:

```
cat /etc/apt/sources.list
```

And post the results here please. Then lets see how updates go:

```
apt-get update
```

Hopefully no errors, then:

```
apt-get upgrade
```

That will show a list of packages and "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded", of course I can't be sure whether or not you should say yes to proceed or not without seeing the results. I do need to see the results regardless of what you decide. Same thing with:

```
apt-get dist-upgrade
```

That's somewhat more aggressive but quite often needed in these situations. I also need to see what this shows:

```
apt-get -f install
```

Which will provide info about unresolved dependencies.

Other potentially helpful commands:

```
uname -r
```

Provides some kernel info.

```
apt-cache show linux-image
```

More kernel info.

```
apt-cache search linux-image
```

Lots more kernel info.

```
apt-get autoclean
```

Cleans up unused .debs.

```
apt-get clean
```

is more radical, and will remove .deb files even for packages currently installed. But most of the time you probably don't need the .debs any more.

```
dpkg --configure -a
```

Is another command that helps resolve package conflicts.

No doubt this is going to involve quite a little back-n-forth between us. Something I've yet to figure out in Karmic is how to reconfigure X.

They're now using what they call bulletproof X and a lot of the old configuration files are no longer used.

---

### Post by kansasnoob on 2010-01-03
Oh, something I keep meaning to mention and always forget, if you want to convert that Xubuntu to Ubuntu you don't need to reinstall.

Look at this section:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Like for pure Gnome (aka: Ubuntu):

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Schaeufele on 2010-01-09
Ok, here we go. This is the output of apt-get update and apt-get upgrade through chroot to sda6:

jan@jan-laptop:~$ sudo mount --bind /dev /mnt/dev
jan@jan-laptop:~$ sudo mount --bind /proc /mnt/proc
jan@jan-laptop:~$ sudo mount --bind /dev/pts /mnt/dev/pts
jan@jan-laptop:~$ sudo cp /ect/resolv.conf /mnt/etc/resolv.conf
cp: cannot stat `/ect/resolv.conf': No such file or directory
jan@jan-laptop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
jan@jan-laptop:~$ sudo chroot /mnt
root@jan-laptop:/# apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB          
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg [189B]         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release [44.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages [129kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources [39.7kB]       
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages [77.9kB]  
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources [18.8kB]  
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B]
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages [45.0kB]    
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages [14B] 
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources [12.4kB]     
Get: 16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources [14B]  
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages [19.4kB]
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources [3,367B] 
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources [575B] 
Fetched 448kB in 14s (30.7kB/s)                                                
Reading package lists... Done
root@jan-laptop:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
  firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support gcalctool gimp gimp-data gnome-screensaver libasound2
  libgimp2.0 libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 libpq5
  linux-libc-dev tzdata xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
23 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 23.5MB of archives.
After this operation, 913kB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main tzdata 2009u-0ubuntu0.9.10 [689kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libgssapi-krb5-2 1.7dfsg~beta3-1ubuntu0.1 [108kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libkrb5-3 1.7dfsg~beta3-1ubuntu0.1 [337kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libkrb5support0 1.7dfsg~beta3-1ubuntu0.1 [39.5kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libk5crypto3 1.7dfsg~beta3-1ubuntu0.1 [102kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5-branding 3.5.7+nobinonly-0ubuntu0.9.10.1 [206kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libasound2 1.0.20-3ubuntu6.1 [391kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main xulrunner-1.9.1-gnome-support 1.9.1.7+nobinonly-0ubuntu0.9.10.1 [40.6kB]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main xulrunner-1.9.1 1.9.1.7+nobinonly-0ubuntu0.9.10.1 [7,995kB]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5-gnome-support 3.5.7+nobinonly-0ubuntu0.9.10.1 [90.0kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5 3.5.7+nobinonly-0ubuntu0.9.10.1 [943kB]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox 3.5.7+nobinonly-0ubuntu0.9.10.1 [73.4kB]
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe firefox-3.0 3.5.7+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe firefox-3.0-branding 3.5.7+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe firefox-3.0-gnome-support 3.5.7+nobinonly-0ubuntu0.9.10.1 [73.3kB]
Get: 16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-gnome-support 3.5.7+nobinonly-0ubuntu0.9.10.1 [73.3kB]
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main gcalctool 5.28.2-0ubuntu1 [205kB]
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libgimp2.0 2.6.7-1ubuntu1.1 [594kB]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main gimp-data 2.6.7-1ubuntu1.1 [1,981kB]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main gimp 2.6.7-1ubuntu1.1 [4,388kB]
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main gnome-screensaver 2.28.0-0ubuntu3.2 [4,169kB]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libpq5 8.4.2-0ubuntu9.10 [76.0kB]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-libc-dev 2.6.31-17.54 [743kB]
Fetched 23.5MB in 6min 2s (64.6kB/s)                                           
Preconfiguring packages ...
(Reading database ... 180865 files and directories currently installed.)
Preparing to replace tzdata 2009s-0ubuntu0.9.10 (using .../tzdata_2009u-0ubuntu0.9.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2009u-0ubuntu0.9.10) ...

Current default time zone: 'Europe/London'
Local time is now:      Sat Jan  9 13:44:28 GMT 2010.
Universal Time is now:  Sat Jan  9 13:44:28 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 180865 files and directories currently installed.)
Preparing to replace libgssapi-krb5-2 1.7dfsg~beta3-1 (using .../libgssapi-krb5-2_1.7dfsg~beta3-1ubuntu0.1_i386.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.7dfsg~beta3-1 (using .../libkrb5-3_1.7dfsg~beta3-1ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.7dfsg~beta3-1 (using .../libkrb5support0_1.7dfsg~beta3-1ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libk5crypto3 1.7dfsg~beta3-1 (using .../libk5crypto3_1.7dfsg~beta3-1ubuntu0.1_i386.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace firefox-3.5-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-branding_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-branding ...
Preparing to replace libasound2 1.0.20-3ubuntu6 (using .../libasound2_1.0.20-3ubuntu6.1_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace xulrunner-1.9.1-gnome-support 1.9.1.6+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1-gnome-support_1.9.1.7+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement xulrunner-1.9.1-gnome-support ...
Preparing to replace xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.1.6.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Preparing to replace firefox-3.5-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5-gnome-support_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
Preparing to replace firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5 ...
Preparing to replace firefox 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-3.0 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0 ...
Preparing to replace firefox-3.0-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0-branding_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0-branding ...
Preparing to replace firefox-3.0-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.0-gnome-support_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-3.0-gnome-support ...
Preparing to replace firefox-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-gnome-support_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace gcalctool 5.28.1-0ubuntu1 (using .../gcalctool_5.28.2-0ubuntu1_i386.deb) ...
Unpacking replacement gcalctool ...
Preparing to replace libgimp2.0 2.6.7-1ubuntu1 (using .../libgimp2.0_2.6.7-1ubuntu1.1_i386.deb) ...
Unpacking replacement libgimp2.0 ...
Preparing to replace gimp-data 2.6.7-1ubuntu1 (using .../gimp-data_2.6.7-1ubuntu1.1_all.deb) ...
Unpacking replacement gimp-data ...
Preparing to replace gimp 2.6.7-1ubuntu1 (using .../gimp_2.6.7-1ubuntu1.1_i386.deb) ...
Unpacking replacement gimp ...
Preparing to replace gnome-screensaver 2.28.0-0ubuntu3.1 (using .../gnome-screensaver_2.28.0-0ubuntu3.2_i386.deb) ...
Unpacking replacement gnome-screensaver ...
Preparing to replace libpq5 8.4.1-1 (using .../libpq5_8.4.2-0ubuntu9.10_i386.deb) ...
Unpacking replacement libpq5 ...
Preparing to replace linux-libc-dev 2.6.31-16.53 (using .../linux-libc-dev_2.6.31-17.54_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up libkrb5support0 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libk5crypto3 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libkrb5-3 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libgssapi-krb5-2 (1.7dfsg~beta3-1ubuntu0.1) ...

Setting up libasound2 (1.0.20-3ubuntu6.1) ...

Setting up xulrunner-1.9.1 (1.9.1.7+nobinonly-0ubuntu0.9.10.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Setting up xulrunner-1.9.1-gnome-support (1.9.1.7+nobinonly-0ubuntu0.9.10.1) ...

Setting up gcalctool (5.28.2-0ubuntu1) ...

Setting up libgimp2.0 (2.6.7-1ubuntu1.1) ...

Setting up gimp-data (2.6.7-1ubuntu1.1) ...
Setting up gimp (2.6.7-1ubuntu1.1) ...

Setting up gnome-screensaver (2.28.0-0ubuntu3.2) ...

Setting up libpq5 (8.4.2-0ubuntu9.10) ...

Setting up linux-libc-dev (2.6.31-17.54) ...
Setting up firefox-3.5-branding (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0-branding (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.5 (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Please restart all running instances of firefox-3.5, or you will experience problems.

Setting up firefox-3.5-gnome-support (3.5.7+nobinonly-0ubuntu0.9.10.1) ...

Setting up firefox (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0 (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.0-gnome-support (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-gnome-support (3.5.7+nobinonly-0ubuntu0.9.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
root@jan-laptop:/#

---

### Post by Schaeufele on 2010-01-09
I will now exit chroot, unmount and then try to start Ubuntu Karmic on sda6...

---

### Post by Schaeufele on 2010-01-09
Well, this has partly worked, Ubuntu on sda6 does not crash as hard anymore. The display still breaks after a few seconds, but I can still see the desktop and the computer reats to ctr+alt+delete and can be shut down.
I'll now try apt-get dist-upgrade.

---

### Post by Schaeufele on 2010-01-09
Ok, here we go again:

jan@jan-laptop:~$ sudo bash mount_sda6.sh
root@jan-laptop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic
  linux-image-2.6.31-17-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0MB of archives.
After this operation, 172MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-image-2.6.31-17-generic 2.6.31-17.54 [28.8MB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-generic 2.6.31.17.30 [3,314B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-image-generic 2.6.31.17.30 [3,322B]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-headers-2.6.31-17 2.6.31-17.54 [9,531kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-headers-2.6.31-17-generic 2.6.31-17.54 [674kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main linux-headers-generic 2.6.31.17.30 [3,316B]
Fetched 39.0MB in 12min 57s (50.3kB/s)                                         
Selecting previously deselected package linux-image-2.6.31-17-generic.
(Reading database ... 180865 files and directories currently installed.)
Unpacking linux-image-2.6.31-17-generic (from .../linux-image-2.6.31-17-generic_2.6.31-17.54_i386.deb) ...
Done.
Preparing to replace linux-generic 2.6.31.16.29 (using .../linux-generic_2.6.31.17.30_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.31.16.29 (using .../linux-image-generic_2.6.31.17.30_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.31-17.
Unpacking linux-headers-2.6.31-17 (from .../linux-headers-2.6.31-17_2.6.31-17.54_all.deb) ...
Selecting previously deselected package linux-headers-2.6.31-17-generic.
Unpacking linux-headers-2.6.31-17-generic (from .../linux-headers-2.6.31-17-generic_2.6.31-17.54_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.31.16.29 (using .../linux-headers-generic_2.6.31.17.30_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-17-generic          
 *  nvidia (96.43.13)...                                                        nvidia (96.43.13): Installing module.
..................
......
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-generic (2.6.31.17.30) ...
Setting up linux-generic (2.6.31.17.30) ...
Setting up linux-headers-2.6.31-17 (2.6.31-17.54) ...
Setting up linux-headers-2.6.31-17-generic (2.6.31-17.54) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.31.17.30) ...
root@jan-laptop:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@jan-laptop:/# uname -r
2.6.31-17-generic
root@jan-laptop:/# apt-cache show linux-image
Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.31.17.30
Depends: linux-image-generic (= 2.6.31.17.30)
Filename: pool/main/l/linux-meta/linux-image_2.6.31.17.30_i386.deb
Size: 3312
MD5sum: 52d188feea90110733d515c464b12d39
SHA1: 0979553bf035a5b5d80bca54843df40bfd09728c
SHA256: 781f9bc3593f2c2e9546bc97d8600d5fca7ea9e20eac5e5565e08704a7baeacf
Description: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.31.16.29
Depends: linux-image-generic (= 2.6.31.16.29)
Filename: pool/main/l/linux-meta/linux-image_2.6.31.16.29_i386.deb
Size: 3266
MD5sum: 43fd9e27f0b68674c8602fb5d5b37baa
SHA1: f51cac09934eb5dfde32cc575cfd2057f646e382
SHA256: b6e4151ce3dc59756ba237f9febe07635724bafd9e77cdace87e9922674aa56e
Description: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.31.14.27
Depends: linux-image-generic (= 2.6.31.14.27)
Filename: pool/main/l/linux-meta/linux-image_2.6.31.14.27_i386.deb
Size: 3152
MD5sum: c88bff4d9be492f55ab49c928ba40750
SHA1: 06bb78883cb63903392e9b0a6885838b0b32bcd7
SHA256: 5fb40b090593a3b5bafce3c71fb0135698eb2aad8400a7149b0a8d66df8d718e
Description: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

root@jan-laptop:/# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del firefox-3.0-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Del firefox-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.3kB]
Del firefox-3.0-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Del firefox 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.4kB]
Del firefox-3.0 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.2kB]
Del xulrunner-1.9.1-gnome-support 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [40.6kB]
Del firefox-3.5-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 [206kB]
Del firefox-3.5-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [90.0kB]
Del xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [7,994kB]
Del firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 [943kB]
Del tzdata 2009s-0ubuntu0.9.10 [688kB]
root@jan-laptop:/# dpkg --configure -a
root@jan-laptop:/# exit
exit
jan@jan-laptop:~$ sudo bash umount_sda6.sh

---

### Post by Schaeufele on 2010-01-09
And now for the reboot...

---

### Post by Schaeufele on 2010-01-09
And still no success, Ubuntu starts and then the desktop crashes. However, the systems reacts to keystrokes.

Perhaps the X server does indeed need to be reconfigured?  :confused:

---

### Post by Schaeufele on 2010-08-29
"Solved" the problem now:

Saved data by mounting broken system under Xubuntu and deleted Ubuntu... :-(

No ideal, but Xubuntu still working a treat...

Cleaned up GRUB with Synaptic, looks nice now.

All the best
Schaeufele

---

