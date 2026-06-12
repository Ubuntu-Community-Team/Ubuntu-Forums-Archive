---
title: "Ubuntu 11.10 linux 3.0.0-13 has stopped booting"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by sdd on 2011-11-25
Please Help. I am having problems booting in to Ubuntu 11.10 with the 3.0.0-13 Linux kernel

It booted fine last night. Now I get two flashing lights (caps lock and the one next to it) almost immediately after selection in grub.

The rescue option does the same thing!

There is nothing on the console. The screen just stays purple. Hitting ESC has no effect.

I can boot using the previous version of the kernel 3.0.0-12. This boots normally. 

I used synaptic to re-install linux* where the version is 3.0.0-13 but this failed to complete with dependency errors.

How do I UN-install 3.0.0-13 and then RE-install.

Is there a repair option.

If I wait will 3.0.0-14 come alone and make all this unnecessary?

SDD

---

### Post by darkod on 2011-11-25
You completely remove with:

sudo apt-get --purge remove 'package name'

You install with:

sudo apt-get install 'package name'

although I have never tried installing kernels like that.

Yes, if you are willing to wait long enough (not sure how long but not long), a new kernel will come along.

So it's up to you whether you want to continue booting -12 until a new one comes without even trying to fix/reinstall -13.

---

### Post by sdd on 2011-11-25
I don't think I will try:

sudo apt-get --purge remove linux*

I do not know the correct package names and I am a bit of a coward:(

I will wait unless someone has another option! 

Bit irritating though. It was fine last night!

Thanks for the advice:D

---

### Post by darkod on 2011-11-25
You definitely DO NOT use remove linux*, that will remove all of them. :)

If I'm not wrong, the exact kernel name is:
linux-image-3.0.0-13-generic

All the kernels are installed in /boot (I think) and you can check what is there with:

ls /boot

---

### Post by bluexrider on 2011-11-25
> **sdd said:**
> Please Help. I am having problems booting in to Ubuntu 11.10 with the 3.0.0-13 Linux kernel

It booted fine last night. Now I get two flashing lights (caps lock and the one next to it) almost immediately after selection in grub.

The rescue option does the same thing!

There is nothing on the console. The screen just stays purple. Hitting ESC has no effect.

I can boot using the previous version of the kernel 3.0.0-12. This boots normally. 

I used synaptic to re-install linux* where the version is 3.0.0-13 but this failed to complete with dependency errors.

How do I UN-install 3.0.0-13 and then RE-install.



Is there a repair option.

If I wait will 3.0.0-14 come alone and make all this unnecessary?

SDD

Find your exact kernel, in terminal
 
[FONT=arial]**sudo dpkg --get-selections | grep linux-image**[/FONT]

Then 
To remove the kernel
[FONT=arial][B]sudo apt-get purge linux-image-3.0.0-13-generic

reboot[/B][/FONT]

---

### Post by sdd on 2011-11-26
Thanks to all who have responded.

I will take a backup of my stuff and then do a purge...

Regards

SDD

---

### Post by SchneiderIS on 2011-12-03
I have EXACTLY the same problem.   It came though right from the upgrade.

---

### Post by SchneiderIS on 2011-12-03
I think I have gotten past the issue.   Booting into -12 I then installed the recommended nvidia driver and all the other updates.  After a reboot everything processed through as it should.

The next thing I did was moved back to a gnome classic theme.  That though was not required.

---

### Post by sdd on 2011-12-10
OK 

3.0.0-13 still not working...
3.0.0-12 boots OK
Update manager says update to 3.0.0-14 :D

Fails to complete installation :( with a package error. No change to Grub!

Synaptic show 3.0.0-14 headers only so I remove them using synaptic. Start with clean slate!

sudo apt-get purge linux-image-3.0.0-13-generic

Reboot. Grub shows only 3.0.0-12 in boot menu. 

Install 3.0.0-14

sudo apt-get install linux-image-3.0.0-14-generic

Also install 3.0.0-14 headers using Synaptic.

Reboot. Grub shows 3.0.0-14 and 3.0.0-12 in boot menu. 

Boot from 3.0.0-14 - Same as 3.0.0-13. Kernel Panic!

Please don't close this issue it is a REAL problem!

Has anyone found a cure for this. It is driving me mad!

SDD:(

---

### Post by fibster on 2011-12-10
show us your 

ls /boot

does it look like this?

abi-3.0.0-12-generic         memtest86+.bin
abi-3.0.0-13-generic         memtest86+_multiboot.bin
config-3.0.0-12-generic      System.map-3.0.0-12-generic
config-3.0.0-13-generic      System.map-3.0.0-13-generic
grub                         vmcoreinfo-3.0.0-12-generic
initrd.img-3.0.0-12-generic  vmcoreinfo-3.0.0-13-generic
initrd.img-3.0.0-13-generic  vmlinuz-3.0.0-12-generic
lost+found                   vmlinuz-3.0.0-13-generic



I imagine yours is missing the initrd for -13


good luck,

fibster

---

### Post by sdd on 2011-12-10
That is correct for 3.0.0-13. I did not look at 3.0.0-14 just got fed up and kicked it out!

Also my grub config did not use the uuid for the boot drive.

Does any one know how to the the update manager to relode 3.0.0.14 again. It updated, failed but would not update again. It says I am up to date even though I have purged 3.0.0-13 and 3.0.0-14.

Or should I use synaptic. If so does any one know what are ALL the packages I should install.

SDD

---

### Post by Joshun on 2011-12-10
Hi,
If you want to update to the latest kernel image available, do
```
sudo apt-get install linux-image
```To update the initrd image, do:
```
sudo update-initramfs -u
```If for some reason, that still doesn't work, do:
```
sudo update-initramfs -c -k 3.0.0-14-generic
```Joshua

---

### Post by Joshun on 2011-12-10
If none of those work, what is the output of these commands:
```
file /usr/sbin/update-initramfs
``````
file /usr/sbin/update-initramfs.distrib
```In some cases, you have to link /usr/sbin/update-initramfs.distrib to /usr/sbin/update-initramfs.

If your output of 'file /usr/sbin/update-initramfs' is ```
/usr/sbin/update-initramfs: symbolic link to `/usr/sbin/update-initramfs.distrib'
```and the output of file /usr/sbin/update-initramfs.distrib is ```
/usr/sbin/update-initramfs.distrib: POSIX shell script text executable
```then do:

```
sudo rm /usr/sbin/update-initramfs
``````
sudo ln -s /usr/sbin/update-initramfs.distrib /usr/sbin/update-initramfs
```Then run the commands mentioned in the previous post again (sudo update-initramfs -c -k 3.0.0-14-generic and then sudo update-initramfs -u).

---

### Post by sdd on 2011-12-10
Joshua Still no luck 
(however the story has a happy ending. please read on)

After installing as instructed the grub dir looks like this:

drwxr-xr-x  3 root root    12288 2011-12-10 23:29 grub
drwxr-xr-x 25 root root     4096 2011-12-10 23:20 ..
drwxr-xr-x  3 root root     4096 2011-12-10 23:20 .
-rw-------  1 root root     1367 2011-11-21 21:30 vmcoreinfo-3.0.0-14-generic
-rw-r--r--  1 root root   730770 2011-11-21 21:29 abi-3.0.0-14-generic
-rw-r--r--  1 root root   135131 2011-11-21 21:29 config-3.0.0-14-generic
-rw-------  1 root root  2696015 2011-11-21 21:29 System.map-3.0.0-14-generic
-rw-------  1 root root  4660944 2011-11-21 21:29 vmlinuz-3.0.0-14-generic
-rw-r--r--  1 root root 13740675 2011-10-13 18:49 initrd.img-3.0.0-12-generic
-rw-r--r--  1 root root  4658096 2011-10-12 15:34 vmlinuz-3.0.0-12-generic
-rw-------  1 root root     1367 2011-10-07 21:08 vmcoreinfo-3.0.0-12-generic
-rw-------  1 root root  2694177 2011-10-07 21:02 System.map-3.0.0-12-generic
-rw-r--r--  1 root root   730503 2011-10-07 21:02 abi-3.0.0-12-generic
-rw-r--r--  1 root root   134754 2011-10-07 21:02 config-3.0.0-12-generic
-rw-r--r--  1 root root   176764 2011-05-03 00:07 memtest86+.bin
-rw-r--r--  1 root root   178944 2011-05-03 00:07 memtest86+_multiboot.bin

As you can see there is no initrd.img-3.0.0-14-generic

file initrd.img
--> initrd.img: broken symbolic link to `/boot/initrd.img-3.0.0-14-generic'

file /usr/sbin/update-initramfs
--> /usr/sbin/update-initramfs: symbolic link to `/bin/true'

file /usr/sbin/update-initramfs.distrib
-->/usr/sbin/update-initramfs.distrib: POSIX shell script text executable

So I did the following:
root@stuart-VPCF11Z1EI:~# sudo rm /usr/sbin/update-initramfs
root@stuart-VPCF11Z1EI:~# sudo ln -s /usr/sbin/update-initramfs.distrib /usr/sbin/update-initramfs
root@stuart-VPCF11Z1EI:~# sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
root@stuart-VPCF11Z1EI:~# sudo update-initramfs -c -k 3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic

I can now see initrd.img-3.0.0-14-generic in the /boot path and file initrd.img returns:
-->initrd.img: symbolic link to `/boot/initrd.img-3.0.0-14-generic'

However the problem STILL persisted....
 
I then went back to my grub.cfg to update it fixing the root=UUID stuff and adding the initrd - but then I thought lets let grub do it so I did an update-grub. 

When I checked the grub.cfg it was all fixed :D

I tried again an I can now BOOT to 3.0.0-14 :popcorn:

That is brilliant thanks so much.

Do you have any idea what the root cause is. It would be nice to think that it would be fixed for 3.0.0-15. At least I now have a path to fixing it even if it remains broken.

Once again Joshua a big thanks.

---

### Post by Joshun on 2011-12-11
I'm pleased its fixed, I know how frustrating it is when an otherwise brilliant operating system stops working. I think, in theory, a new kernel should be fine since update-grub is usually called automatically after an update. As for the cause, your file /usr/sbin/update-initramfs was a symlink to /bin/true, so the system thought the update-initramfs script was run successfully but in reality it did nothing (just ran dummy exe /bin/true). Now that you have linked update-initramfs to the proper file, in this case update-initramfs.distrib, the problem should be solved :)

---

### Post by ppeterb on 2011-12-22
The answer goes further back. Installers ubiquity and aptitude (and perhaps more) invoke a filtering process dpkg-divert. This looks at files coming in and can divert them to another location, rename them, or a bunch of other really ugly things. Do a man dpkg-divert for more information on the process. Use the command dpkg-divert --list to see how it affects your system

update-initramfs was diverted to update-initramfs.distrib in my system but I cannot find out why. The whole scheme is an amateurish undocumented crop of patches.

Copy or rename /usr/sbin/update-initramfs.distrib to remove .distrib to keep updates and installs operating. Use a dpkg-divert command (this is not easy, see the man) to implement a real fix - but be alert to the problem returning.

---

