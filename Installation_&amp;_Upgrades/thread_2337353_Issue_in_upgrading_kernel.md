---
title: "Issue in upgrading kernel"
date: 2016-09-17
forum: Installation &amp; Upgrades
---

### Post by adagu on 2016-09-17
Hi,
I am using Ubuntu 14.04, having upgraded from 12.04. I am having issues trying to update my kernel version. This is what I see as my running kernel.

$ uname -a
Linux anirban-ThinkPad-X220 3.2.0-77-generic #112-Ubuntu SMP Tue Feb 10 15:22:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I have followed instructions from [http://askubuntu.com/questions/598483/how-can-i-use-kernel-3-19-in-14-04-now](http://askubuntu.com/questions/598483/how-can-i-use-kernel-3-19-in-14-04-now) to try to install a newer kernel. I can see these kernel when I run the command "dpkg --list | grep linux-image" . However, for some reason, the only one I see when booting is the 3.2.0-77-generic , and it always uses that. I have also tried editing /etc/default/grub by changing the GRUB_DEFAULT (using corresponing number from "grep menuentry /boot/grub/grub.cfg" ) but even then there is no change in the running kernel. I have also tried "sudo apt-get install --reinstall linux-generic" to no avail.

I am medium level user. My initial hunch is that maybe there are two locations where grub is stored? Here is the output of "fdisk"

$ sudo fdisk -l
```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b468


Device Boot Start End Blocks Id System
/dev/sda1 * 2048 976895 487424 83 Linux
/dev/sda2 976896 16601087 7812096 83 Linux
/dev/sda3 16603134 45897727 14647297 5 Extended
/dev/sda4 45897728 500115455 227108864 83 Linux
/dev/sda5 16603136 26365951 4881408 82 Linux swap / Solaris
/dev/sda6 26368000 45897727 9764864 83 Linux
```

I am new to this forum. Please let me know if I should post it in any particular subforum. Thanks for any help.
-adg

---

### Post by Bucky Ball on 2016-09-17
Welcome. Wondering if there's a specific purpose you want to do this. Is there? Or just curious?

Yes, you can use newer kernels, but it is generally done to provide hardware drivers that aren't present in your current kernel (and it can work the other way, to, and a new kernel will break an installed driver or manually installed PPA because it is not intended to run on that kernel version). When you have installed the new kernel it should appear in the list at boot without you fiddling about with fstab. As an intermediate user, I'd be careful and *make sure you make a copy of the original fstab* before you change it too much.

To upgrade to a newer kernel you can use the kernel .deb files. It is a matter of three or four or five clicks once downloaded, reboot and you're done. You may be making this a little more complicated than it needs to be. Have a [look here and take your pick]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). :)

Another way to upgrade the kernel is to upgrade the OS to 16.04 LTS, of course. :)

Also, have you just done a regular update??? That will drag in any newer kernel version for your release of Ubuntu. You can use Software Updater or a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

If you want the newer hardware stack and the .5 release, think this gives it to you after 'sudo apt-get update' (always run that first).

```
sudo apt-get dist-upgrade
```

This will NOT upgrade your release to a newer one, just the software in it.

---

### Post by ian-weisser on 2016-09-17
Please show us the output of:
```
ls /boot
sudo apt-get update
sudo apt-get upgrade
dpkg -l | grep linux-
```

---

### Post by deadflowr on 2016-09-17
You have four linux partitions.
Do you have more than one OS installed?

---

### Post by adagu on 2016-09-17
Hi,
thanks all for the very prompt replies. I initially wanted to install VirtualBox and got stuck with an error message "Kernel driver not installed". Tracing back from there it seemed during virtualbox installations it is not installing the drivers corresponding to my kernel. I might be mistaken in my diagnosis though. I agree, I might just be stumbling around a bit too much with my dangerous "little knowledge" :)

@Bucky Ball: I ran the the commands you suggested and tried attaching the output (includes the commands also). Didn't work, so here is the Google Drive viewing link: [https://drive.google.com/file/d/0BxplwsnZR4NfLV9tcHNZMEhHU0E/view?usp=sharing](https://drive.google.com/file/d/0BxplwsnZR4NfLV9tcHNZMEhHU0E/view?usp=sharing)

  
@ian-weisser: I ran the dist-upgrade. Does not seem to change the running kernel.

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
$ uname -r
3.2.0-77-generic

```


@deadflowr : No, the only OS is Ubuntu 14.04 (corrected typo here). The partitions were created when installing (/tmp etc), possibly overkill on my part. One of the partitions /dev/sda1 was created when I was trying to fix the setup, having accidentally deleted the kernel.Using "blkid" I see this :

```
$ sudo blkid
/dev/sda1: UUID="5dd394ee-1654-4767-b3bc-b8f78e07ffcb" TYPE="ext4" 
/dev/sda2: UUID="d201c059-069f-49b7-aa44-3119932c32b9" TYPE="ext4" 
/dev/sda4: UUID="3c13e640-7916-42e7-b34a-20ed31c5b485" TYPE="ext4" 
/dev/sda5: UUID="42a03d24-b1fc-4ad8-b0af-c8adca4b9a0a" TYPE="swap" 
/dev/sda6: UUID="020e01fd-fdca-431d-884c-73846fea2bf4" TYPE="ext4" 

```


```
$ ls -lah /media/anirban/5dd394ee-1654-4767-b3bc-b8f78e07ffcb/
total 23M
drwxr-xr-x  4 root root 7.0K Mar  2  2015 .
drwxr-x---+ 4 root root 4.0K Sep 17 09:11 ..
-rw-r--r--  1 root root 778K Feb 10  2015 abi-3.2.0-77-generic
-rw-r--r--  1 root root 138K Feb 10  2015 config-3.2.0-77-generic
drwxr-xr-x  3 root root 7.0K Mar  2  2015 grub
-rw-r--r--  1 root root  14M Mar  2  2015 initrd.img-3.2.0-77-generic
drwx------  2 root root  12K Sep  3  2012 lost+found
-rw-r--r--  1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root 2.8M Feb 10  2015 System.map-3.2.0-77-generic
-rw-------  1 root root 4.8M Feb 10  2015 vmlinuz-3.2.0-77-generic
```

---

### Post by Bucky Ball on 2016-09-17
Are you installing this stuff from the official repositories (Software Centre or Ubuntu Software, not sure what Ubuntu uses now) or grabbing PPAs, .deb and .tar files and what not from third-parties? Virtualbox is in the repos. It should install without an issue from there (and I have it installed this way and working faultlessly on two machines currently). :-k

Rule of thumb: Always check the official repos first. Less chance of issues. And please use code tags for terminal output. See the green link in my signature (or look at how they appear by editing your first post which deadflowr fixed for you or the last which I added some to the last code block and see how they're used).

Important note: In your first post you say

> I am using Ubuntu 14.04, having upgraded from 12.04. I am having issues trying to update my kernel version. This is what I see as my running kernel.

In your last, you state:

> ... the only OS is Ubuntu 16.04.

Which is it??? If you are running 16.04 you've managed to regress the kernel to an older one by the looks as that kernel is for either 14.04 or 12.04, not sure which. If you do have 14.04 installed, back to my original question. :)

Why are you wanting to upgrade to a newer kernel? I'm figuring its because you thought that's why Virtualbox wouldn't install. I suggest you try installing Virtualbox from the official repositories and see what happens.

Be advised, though, that looks like you've done a lot of 'experimentation' there and who knows whether this would be a smooth process at this stage.

---

### Post by adagu on 2016-09-17
Thanks for pointing out, used code tags now. Sorry also for the typo, it is 14.04 (edited answer). Yes, I did install virtualbox using aptitude, I assume that is fine?

---

### Post by ian-weisser on 2016-09-17
> **adagu said:**
> @ian-weisser: I ran the dist-upgrade. Does not seem to change the running kernel.

Thanks, that rules out a couple possibilities.
But it does not rule out others.
Please provide the rests of the information asked for in Post #3.

---

### Post by deadflowr on 2016-09-17
Post the output for 
```
cat /etc/fstab
```
because this:
```
$ ls -lah /media/anirban/5dd394ee-1654-4767-b3bc-b8f78e07ffcb/
total 23M
drwxr-xr-x  4 root root 7.0K Mar  2  2015 .
drwxr-x---+ 4 root root 4.0K Sep 17 09:11 ..
-rw-r--r--  1 root root 778K Feb 10  2015 abi-3.2.0-77-generic
-rw-r--r--  1 root root 138K Feb 10  2015 config-3.2.0-77-generic
drwxr-xr-x  3 root root 7.0K Mar  2  2015 grub
-rw-r--r--  1 root root  14M Mar  2  2015 initrd.img-3.2.0-77-generic
drwx------  2 root root  12K Sep  3  2012 lost+found
-rw-r--r--  1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root 2.8M Feb 10  2015 System.map-3.2.0-77-generic
-rw-------  1 root root 4.8M Feb 10  2015 vmlinuz-3.2.0-77-generic
```
does not give us any idea where that file system is located within the operating system structure.

With the new knowledge:
> The partitions were created when installing (/tmp etc), possibly overkill on my part. One of the partitions /dev/sda1 was created when I was trying to fix the setup,
you gave us, it seems like something about the partitions and the operating system as a whole are a mess.
the fstab file should better explain where those other partitions are suppose to be (ala /boot, or /var or /home?)

also two more commands that might help a little:
```
df -h
mount
```
these will show how the system is being mounted, more or less.

---

### Post by adagu on 2016-09-17
Sure. Here they are.

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=3c13e640-7916-42e7-b34a-20ed31c5b485 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
#UUID=5dd394ee-1654-4767-b3bc-b8f78e07ffcb /boot           ext4    defaults        0       2
# /tmp was on /dev/sda2 during installation
UUID=d201c059-069f-49b7-aa44-3119932c32b9 /tmp            ext4    defaults        0       2
# /usr/local was on /dev/sda6 during installation
UUID=020e01fd-fdca-431d-884c-73846fea2bf4 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=42a03d24-b1fc-4ad8-b0af-c8adca4b9a0a none            swap    sw              0       0

```

```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  1.2M  1.6G   1% /run
/dev/sda4       214G  139G   64G  69% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            7.8G   99M  7.7G   2% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda6       9.2G  1.4G  7.4G  16% /usr/local
/dev/sda2       7.4G  148M  6.9G   3% /tmp

```

```

$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda6 on /usr/local type ext4 (rw)
/dev/sda2 on /tmp type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=anirban)

```

---

### Post by deadflowr on 2016-09-17
Huh.
Well alright.
It seems like the /boot partition is #commented out.
So it's not in any use, at the moment.
Would probably explain the odd issues at hand.

I wonder if reinstalling grub while the /boot partition is disabled will move to using, what I would assume are the kernels installed with the / partition (dev/sda4)
Maybe try booting into the system like normal, then run
```
sudo grub-install /dev/sda
sudo update-grub
```
See if that allows you to boot the newer kernels.

Edit: Before you try re-installing grub, you might also want to double check the bootinfo.
See: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")
Perhaps that might giver even more insight.

---

