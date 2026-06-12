---
title: "Cannot mount partitions"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by cogitans on 2018-10-19
I just upgraded Ubuntu from 18.04.1 to 18.10.
Now the graphics are great.


 But as my OS is on a partition for itself I need to mount several  partitions to do some regular work on my system. I usually do this  through Nautilus.
 
But as I attempt to mount my drives in Nautilus I receive the error:

 
unable to access location
error mounting /dev/sdc1 at /media/User/Maxtor:mount(2)
system call failed: bad address

 
and if I try to mount through the terminal I receive the same error.

 So I went into Gparted to check up on my partitions. Every partition and harddrives are visible in here.

 
Now I'm stuck....


 ProblemType: Bug
DistroRelease: Ubuntu 18.10
Package: nautilus 1:3.26.4-0ubuntu7
ProcVersionSignature: Ubuntu 4.18.0-10.11-generic 4.18.12
Uname: Linux 4.18.0-10-generic x86_64
NonfreeKernelModules: talpa_vfshook talpa_pedconnector  talpa_pedevice talpa_vcdevice talpa_core talpa_linux talpa_syscallhook  nvidia_modeset nvidia
ApportVersion: 2.20.10-0ubuntu13
Architecture: amd64
CurrentDesktop: ubuntu:GNOME
Date: Fri Oct 19 10:32:31 2018
InstallationDate: Installed on 2018-09-07 (41 days ago)
InstallationMedia: Ubuntu 18.04.1 LTS "Bionic Beaver" - Release amd64 (20180725)
SourcePackage: nautilus
UpgradeStatus: Upgraded to cosmic on 2018-10-19 (0 days ago)
usr_lib_nautilus:

---

### Post by dino99 on 2018-10-19
Be sure that blkid output and fstab are matching.
Is your installation encrypted ?

---

### Post by cogitans on 2018-10-19
My HOME-UUID matches in fstab and blkid.

I'm sure why I was to check this, though, as the issue has nothing to do about booting.

Nothing in my OS or HOME is encrypted.

To summarize:
when I'm logged in to my system I am not able to access any of my other partitions than the system-partition. When ever I try to mount another partition than the system-partition I receive the initial stated error.

Update:
between my initial post and this reply I encountered an issue about not being able to show the desktop after a successful login.
I did some fumbling around and managed to gain access to my system again after installing lightdm from terminal.

Maybe this is a bug, too...

---

### Post by dino99 on 2018-10-19
After a dist-upgrade, also think about cleaning the system to purge old dependencies and settings.
Use gtkorphan & bleachbit (as root, carefully select settings)

---

### Post by cogitans on 2018-10-19
The installation did a cleanup afterwards and I've done cleanup through: autoremove, clean, gtkorphan and bleachbit.
But still nothing helps. I keep getting the same error about the address.

---

### Post by flocculant on 2018-10-19
Do you see anything in logs?

You could try opening a terminal and running journalctl -f

Now try mounting - do you see more information than system call failed: bad address there?

---

### Post by cogitans on 2018-10-19
Well, this command states (even as sudo):

 gnome-shell[3649]: unable to create directory 
'/run/user/1000/dconf': Permission denied.  dconf will not work properly

---

### Post by cogitans on 2018-10-19
Well, now i managed to use the command "journalctl -m" to get some information out of the system. But there's a whole lot of lines.

Which information should I look for?

---

### Post by cogitans on 2018-10-19
Now I went back to the basic by these commands:

sudo mkdir /mnt/sda4
sudo mount /dev/sda4 /mnt/sda4

which gave this result:
mount: /mnt/sda4: mount(2) system call failed: Bad address.

---

### Post by oldos2er on 2018-10-19
Moved to Installation & Upgrades since 18.10 is released.

---

### Post by cogitans on 2018-10-19
> Moved to Installation & Upgrades since 18.10 is released.
Alright.

But this is getting more and more strange.
I just inserted an USB-stick into my computer and when I try to access it I receive the same error: "system call failed: bad address".
So this must be a general error in the release, right?

---

### Post by cogitans on 2018-10-20
No, my logs don't tell any interesting tales unfortunately.

But the new thing is that I did a boot from an Ubuntu installation-usb. In here I tried mounting the partition. And everything worked alright. Luckily all the data is still on the partition (as expected).
So I went into Systemtools -> Disks to note all the settings.
Then I booted into normal mode again and checked the same settings in Disks. Surprise everything is the same. Quite strange...

Update:
now i did a test on editing the fstab to gives access to the partition in this way. But the result is the same: bad address.

---

### Post by cogitans on 2018-10-21
> **flocculant said:**
> Do you see anything in logs?

You could try opening a terminal and running journalctl -f

Now try mounting - do you see more information than system call failed: bad address there?

Hmm, it's getting even more strange now.

Today I've been trying to figure out a solution to an issue about Flatpak 

["Unable to update org.gnome.platform:
failed to run transaction for runtime/org.gnome.platform/x86_64/3.30: no such file or directory"]

and did some modifications on my system regarding Flatpak (maybe the source of these errors is the same [no such file = bad address]?). But with no luck.

At a later period of time during the day I did a test on going onto my partition in Nautilus. And now everything is both accessible and visible ????

THen I moved on to gain access to my containers in VeraCrypt. But now VeraCrypt tells me the exactly same error-messages as Nautilus did before: bad address.

---

### Post by cogitans on 2018-10-25
It turns out that it's Sophos Antivirus that hasn't been adopted to the new versions of the systemfiles:
[https://community.sophos.com/products/free-antivirus-tools-for-desktops/f/sophos-free-tools/108299/sophos-free-av-on-ubuntu-18-10/387331](https://community.sophos.com/products/free-antivirus-tools-for-desktops/f/sophos-free-tools/108299/sophos-free-av-on-ubuntu-18-10/387331)

---

### Post by vidtek on 2018-10-30
Cogitans-

I was having a similar issue since a recent windows10 update mounting ntfs partitions  see here;
[https://ubuntuforums.org/showthread.php?t=2404907]("https://ubuntuforums.org/showthread.php?t=2404907")

Cheers, Tony

---

