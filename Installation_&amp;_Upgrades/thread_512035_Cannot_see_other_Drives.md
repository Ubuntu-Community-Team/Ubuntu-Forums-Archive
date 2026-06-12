---
title: "Cannot see other Drives"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by LinuxHawk on 2007-07-28
Hello.
I have 4 Hard Drives (not partitions, physical drives, 3 IDE and 1 SATA) on my PC.
I just installed the 4th one (SATA) and installed K-Ubuntu on the entire 300GB.
Works great so far, except I cannot see, therefore access my data from the other drives.
When I look in dev/disks/ I see the 2 Data disks (each have 3 partitions) but all the partitions have a picture of a lock on the icons showing them. Indicating that K-Ubuntu sees these as locked and inaccessible.

Any ideas on how I can get full access to all my drives?
Thanks in advance...

---

### Post by Pumalite on 2007-07-28
sudo chmod 777 /dev/disks/xxx

---

### Post by LinuxHawk on 2007-07-28
I tried and get:
chmod: cannot access `/dev/disks/xxx': No such file or directory

Any other ideas?

---

### Post by Pumalite on 2007-07-28
xxx means you have to apply whatever applies to you. Go to '/' in your file browser. Find Media. Doble click on it. See what you have on it.

---

### Post by LinuxHawk on 2007-07-29
/Media ONLY has the CDROM and FLOPPY.
I have to go to the /dev/disk/
Then I can look by ID, label, path, uuid
And in any case it shows them all locked.
I found a utility that I cannot find again, I do not remember what it is called, and it showed me the disks as hdda, hddc etc.
I tried the [sudo chmod 777 /dev/disks/hdda] and it did not work, then the system locked up.
Konquer did not load up, several re-boots later it still froze and was messed.
Since this was a new install, I just re-installed Kubuntu.
Now I find myself staring at the same issue.
This is strange as I am trying Ubuntu rather that Mepis, PCLinuxOS, both wich auto detected and mounted my additional drives.

I know there was a KDE tool that I was able to use in Mepis that allowed me to enable my drives which were visible but just not active after the install.

Thanks in advance...

---

### Post by Pumalite on 2007-07-29
I'm running Feisty Fawn which, when you bring Nautilus up shows all the drives for you to mount. You should have something similar in Kubuntu 7.04. Otherwise start looking at your BIOS. Enable 'Enhanced support fo PATA+SATA'. What motherboard do you have?. Chipset?. What kind of drives?. How many?. In Konqueror it's called 'Storage Media'.

---

### Post by LinuxHawk on 2007-07-29
Thanks for the quick and thoughtful reply.
I do know that the drives and bios is enabled.
This is dual booting with another drive that Grub sees right away. 
I can at startup choose to run Windows XP, Freespire linux, or SuSE.
They all see and can access the other 2 drives that I have my data on.
I also can boot to CD and run Meips Live and it to sees and can access the drives and copy info from them to a USB drive.

Again thanks for the interest in helping.
I have never had a Linux issue as this before.
I have been running mostly Linux for over 3 years now, mostly using it, not command line stuff.
I like Linux, cause I just install and it works.
But this KUbuntu, which I have been reading about, it troubling me.
Thanks again for any advice...  Michael from Florida.

---

### Post by Pumalite on 2007-07-29
When you bring up Konqueror, one of the options is 'Storage Media'; if they are locked you could open a Terminal on them and change permissions. Is that not possible?. This might help:

pumalite@pumalite-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdc2 on /media/disk type ext3 (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/disk-1 type ext2 (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/disk-2 type ext3 (rw,noexec,nosuid,nodev)
pumalite@pumalite-desktop:~$ [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LinuxHawk on 2007-07-29
I get the following...

michael@michael-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
michael@michael-desktop:~$

The issue is that they do NOT show up in storage media.
Only a folder with CDROM0, and FLOPPY0.
I have to go up to root then dev then open a folder (directory) disk.
Ubuntu did not find the disks and place them under storage media.
Strange huh?

And right clicking and trying to change permissions is ghosted out.

---

### Post by Pumalite on 2007-07-29
What motherboard do you have? Chipset? BIOS?

---

### Post by LinuxHawk on 2007-07-29
It is an Asus MB   K8VSE Deluxe if it means anything?

But: OK, if I go to Start, System Settings, and then to Advanced tab I can see a better pic.
Plus I can see the drives here, but they are unmounteed.
 More info...
I can get to Admin mode for the Disk and file system settings.
Have you seen this? I believe it is more of a KDE thing and if you are a Gnome person, then it may not make sense to you.
There are lots of things to try, but lots of ways to blow things up also...

---

### Post by Pumalite on 2007-07-29
If you see the drives, they would be mounted already if ntfs-3g and fuse were installed. But we can get to that later. You are right I'm a Gnome person, so my knowledge of Kubuntu is limited, but I have Konqueror installed. If you are seeing your drives, then your system sees them and that means there must be a way to mount them. I mount them with Nautilus, but Konqueror must provide for the same.

---

### Post by LinuxHawk on 2007-07-29
OK, with some playing I am 90% there.
I have managed to mount them and I can Read (copy data) from them.
However I cannot write to them.
I had to add them in an administrative mode and they belong to root.
Only root has write permissions.
How can I modify the permissions to allow RW Access.
I tried it in the command line with CHMOD command in a root terminal, but it tells me there is no directory with the name I have.
It is really a partition on a hard drive.
Is there an easy way?
Perhaps if I did it in Gnome... (I have Gnome installed) you could show me and it would stick (permissions) no matter what GUI I used.

Thanks again.

---

### Post by LinuxHawk on 2007-07-29
Got it...   Thanks

---

### Post by Pumalite on 2007-07-30
Glad it worked for you! Good luck.

---

