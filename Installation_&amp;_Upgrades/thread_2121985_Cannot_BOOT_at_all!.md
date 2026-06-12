---
title: "Cannot BOOT at all!"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by JDuchows on 2013-03-03
Hello, I did something really stupid! When asked to clean up /boot, I nuked it all, so I no longer have vmlinuz-3.5.0-26-generic and it just boots me into grub which I have no idea what to do with. I tried reparing the Install with 12.10 CD but stopped half-way and now when I try it again, it tells me that there is no OS on the drive and my best bet is to reformat and reinstall. This I absolutely CANNOT do, 'cause I have four months of very important data on that drive! Please can anyone help? I see my old directory, but I can't get to it cause I have no permission. Is there any way to take it off the drive, or to restore the old system. All I see is grub> or being asked to reformat the drive. I do see all the old partitions and such and my home directory but can't get to them. Please, pleaes help.... I really need to get it up and running tonight! Thanks!

Regards, John

---

### Post by JDuchows on 2013-03-03
Arggghhhh.... I've tried using the Boot-Repair and can't say I've made any progress :-((. After running it, it no longer even boots into grub; it just comes up with Missing Operating System and Operating System Not Found. Also, when I now run Boot-Repair and go into Advanced, the sections on Grub are blanked out. I have the following five links which show what happened...

[http://paste.ubuntu.com/5583747/](http://paste.ubuntu.com/5583747/)
[http://paste.ubuntu.com/5583798/](http://paste.ubuntu.com/5583798/)
[http://paste.ubuntu.com/5583803/](http://paste.ubuntu.com/5583803/)
[http://paste.ubuntu.com/5583847/](http://paste.ubuntu.com/5583847/)
[http://paste.ubuntu.com/5583854/](http://paste.ubuntu.com/5583854/)

I think the OS might now be beyond help :-(( - could someone please tell me how to at least access my old directories on the existing partitions to get the data off. That would really be great! Thanks!

---

### Post by oldfred on 2013-03-03
Boot-Repair will not automatically add back kernels you deleted.

But I think it will help you chroot into your system and from a chroot, you can run updates that will add the most current kernel & update grub to use that kernel.

       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
drs305 chroot to reinstall kernel
[http://ubuntuforums.org/showthread.php?t=1641599](http://ubuntuforums.org/showthread.php?t=1641599)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      
 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

---

### Post by SuperFreak on 2013-03-03
You should be able to access all directories by booting off a Live disk(DVD) or Live USB of Ubuntu. If you don't have the original installation DVD or USB you will have to burn it off of another computer [http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop"). It may not be essential but it would probably be best to make the disk/USB the same version as your original OS and the same flavour(32 or 64 bit)

edit:Follow OldFred's advice he got here first with better information

---

### Post by JDuchows on 2013-03-03
Indeed, I have done so and can see them. The problem being that than it tells me I can't access them owing to lack of permission.

---

### Post by JDuchows on 2013-03-03
I am still stuck - quite way, way over my head here! I did the fdisk and my Linux is on /dev/sda1 and * as Boot. I also have /dev/sda2 which is Extended and /dev/sda5 which is LVM. I did sudo mount /dev/sda1 /mnt and it worked. I followed with ***sudo mount --bind /dev  /mnt/dev*** and it said mnt/dev does not exist. So, I didn't get very far there :(. I have no idea how to use chroot. I looked it up but when I tried chroot --userspec=Kmicic (my user name) it told me the operand was missing.

---

### Post by JDuchows on 2013-03-03
Okay, please in just simple words, as if speaking to a child (one of my fave Galaxy Quest quotes) could some please explain to me how to access and offload all my files from /dev/sda1 or /dev/sda2 or /dev/sda5 which is where I think the're sitting? I will then happily just reformat and reinstall. Most of the advice above is way, way over my head :-).

---

### Post by black veils on 2013-03-04
ok this should be possible.

the lvm partition/s will have to be treated differently from regular.

on the live disc, open **terminal** and paste in ```
gksudo nautilus
``` or replace nautilus with whichever file manager you are using,

find and copy your files to an external device or burn to data cd/dvd with k3b.

[COLOR=#008000]*for the remaining lvm:*[/COLOR]

open **terminal** again

1. Install lvm2
```
sudo apt-get install lvm2
```
2. Load the necessary module(s)
```
sudo modprobe dm-mod
```
3. Scan your system for LVM volumes and identify in the output the volume group name that has your volume
```
sudo vgscan
```
4. Activate the volume
```
sudo vgchange -ay MyVolumeGroupName
``` replace MyVolumeGroupName with the result from previous command.
5. now go into the file manager and click the lvm drive(s), this will mount them and ask for password, provided you know the password, you should be able to access and navigate to the files.

if any permission problems happen, try opening the file manager with root privileges using ```
gksudo nautilus
```

---

### Post by oldfred on 2013-03-04
+1 on black veils post.

Frankly I assumed you were a much more knoledgeable user, since you were using LVM. I will not use LVM on a desktop as it is a lot more complex.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

### Post by JDuchows on 2013-03-07
Oh no, sorry to have given you that impression :-) - I was using LVM merely because Ubuntu told me to do so during the initial install process. I pretty much just followed all the default recommendations... Thanks for staying with me and for your patience... Still trying!

---

