---
title: "booting problem of 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by charanks on 2012-04-30
RECTENTLY i upgraded my system from 10.04 to 12.04 through online after completion of this process and i restart it but is showing under this way what to do






               GNU GRB VERSION 1.98-21 ubuntu3

minimal BASH-like line editing is supported for the first word,tab lists possible command completions .anywhere else TAB lists possible device or file completions.

grub>

possible commands are :

.[authenticate back groundcolor background_image badram boot break clear configfile continue cutmen echo export extract_entries_configfile extract_entries_source initrd insmod
linux.load font loopback ls lsfonts menuentry normal normal_exit probe return search search.file search.fs_label search fs_uuid set setparams shift source submenu 
terminal_input terminal_output test unset

---

### Post by garvinrick4 on 2012-04-30
Put in LIve CD (Ubuntu install Cd using Try Ubuntu) get internet working (firefox gets online)
Open a terminal and copy and paste these, going to install grub2 (grub-pc) from 12.04 and then update
and upgrade system while there and check for broken packages.
I am using sda5 for this [COLOR=Red]use your own install sda number[/COLOR].
Can get it by using this below in terminal
```
sudo fdisk -l
``` (lower case L above)

Copy and paste these now in terminal using your own sda[COLOR=Red]#[/COLOR] of Ubuntu Linux install in first copy and paste.
```
sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys

``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````

sudo chroot /mnt
``````
apt-get purge grub grub-pc
``````
grub-install /dev/sda
``````
update-grub
``````
dpkg --configure -a
``````
apt-get update; apt-get upgrade
``````
dpkg --configure -a
``````
exit
``````
sudo umount /mnt/dev/pts; sudo umount /mnt/dev; sudo umount /mnt/proc; sudo umount /mnt/sys; sudo umount /mnt

```Now reboot into hard drive and grub2 (grub-pc) from 12.04 should be in mbr of drive (first few sectors of drive where grub resides) and looking in[COLOR=Red] your linux partition for boot files[/COLOR]. (sda[COLOR=Red]# [/COLOR]your Ubuntu Linux install is in)

---

### Post by tomarcom on 2012-04-30
Load Windows 7, or another distro!
Rip Ubuntu 4.10 - 10.04
I don't know what happened but the last few releases have had alot of issues to sort out just to boot it.  Many other distros are not this flakey, or bloated.  I have used linux for 15 years and after trying 12.04 I'm done with Ubuntu.  There is no excuse for an LTS release to have all these issues.  Congrads.  you have ruind a once great OS!

---

### Post by garvinrick4 on 2012-04-30
> I don't know what happened but the last few releases have had alot of issues to sort out just to boot it.Have not had any issues with grub-pc of any kind just put it in sda where it belongs pointing towards
partition with boot files your sda# you want in control of booting. At install this is all done for you. If you need
assistance is easy to find here in these Forums. Going to have to say it is a user error. Please do not get
insulted putting grub-pc (grub2) into first few sectors of drive is quite simple. Just need to learn how once and you get it.
Many GUI apps nowadays to do it and of course the terminal if desire.

##Please start your own Thread if you desire to get involved.

---

### Post by Tomtompiper on 2012-04-30
Followed these instructions to the letter, and things have become worse, Grub now fails to load at all.  I have two choices, back up to DVD and reinstall, or wait for a solution. Before trying this I had attempted using a another method which had no effect, I shall attempt to use a PCLinuxos liveCD preform a rescue and see how that goes.:(

---

### Post by Tomtompiper on 2012-04-30
PCLinuxOS did not help, it could not recognise the Linux kernel. I shrunk a partition and installed Mint 12, it reinstalled Grub and found all of the Linux kernels, not an ideal solution, but better than losing all of my data. When I got back in video was broken, command line only, when I fixed that I now have no sound.  If you are thinking of upgrading and have not done so yet don't do it until you have checked everything on your machine is compatible with 12.4.

---

### Post by oldfred on 2012-04-30
The newest versions of grub2 need the same version for a simple reinstall of grub2. The chroot as posted should work from any version.

Download and run the Boot-Info from this, post link to report:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Or this may get you booting, by passing grub if system is otherwise ok.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

