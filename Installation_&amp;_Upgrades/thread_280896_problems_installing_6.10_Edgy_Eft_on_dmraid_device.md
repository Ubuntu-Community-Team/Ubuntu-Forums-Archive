---
title: "problems installing 6.10 Edgy Eft on dmraid device"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by xaarr on 2006-10-20
Hello,

i have problems installing the ubuntu 6.10 RC (1) on a dmraid device.

After using gentoo on my bios-raid system (needed 2 months of installing/probing, because dmraid) i will install ubuntu as my main system because i will not spend so many time in my system install/updates.

i used this german description: [http://www.realriot.de/wiki/index.php/FakeRaidHowto_Ubuntu](http://www.realriot.de/wiki/index.php/FakeRaidHowto_Ubuntu)

i have changed the apt-get install

```
apt-get install ubuntu-base linux-amd64-generic ubuntu-desktop dmraid grub
```

to this - because imho renamed packages:

```
apt-get install base-files linux-generic ubuntu-desktop dmraid grub
```

but the install runs not without errors:

```

root@ubuntu:/# apt-get install base-files linux-generic ubuntu-desktop dmraid grub 2>&1 > /aptout.txt
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "de_DE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "de_DE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "de_DE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.


[....]


dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gconf-editor depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.0); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libgnome-window-settings1 depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 python-gnome2
 libgnome-menu2
 python-gmenu
 gnome-menus
 alacarte
 avahi-daemon
 bluez-utils
 libcamel1.2-8
 libebook1.2-9
 bug-buddy
 libpanel-applet2-0
 contact-lookup-applet
 dbus-1-utils
 libgnome-desktop-2
 libgdl-1-0
 libgdl-1-common
 libtotem-plparser1
 python-gnome2-desktop
 python-gnome2-extras
 deskbar-applet
 dmraid
 libecal1.2-7
 libedata-book1.2-2
 libedata-cal1.2-6
 evolution-data-server
 yelp
 ekiga
 eog
 libnautilus-extension1
 evince
 libgtkhtml3.8-15
 gtkhtml3.8
 libedataserverui1.2-8
 libexchange-storage1.2-2
 liblpint-bonobo0
 evolution
 evolution-exchange
 evolution-plugins
 evolution-webcal
 libgnome2.0-cil
 f-spot
 file-roller
 firefox-gnome-support
 gcalctool
 gconf-editor
 libgnome-window-settings1
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can going wrong ?

I think more package names are diffrent in the new Edgy Eft.

Any ideas ?

And: thanks for the great ubuntu project !

Daniel Stobbe.

PS: sorry for the bad englisch.

---

### Post by Aberrix on 2006-10-21
for 6.10, I just enabled the universe respositories and then searched via synaptic for dmraid and the newest version was there and installed with no problems. Try giving that a shot.

---

### Post by xaarr on 2006-10-25
Hello Aberrix,

i has installed dmraid, the drives are correct in /dev/mapper/ as "isw_abc*" mapped.
and i have installed "debootstrap".

the live-cd installer hangs, if i select the raid-device.

i has tryed this:

```
mkdir /target
mount /dev/mapper/isw... /target
mkdir /target/boot
mkdir /target/boot/grub

mkdir /target/dev
mount --bind /dev /target/dev
mkdir /target/proc
mount -t proc proc /target/proc
mkdir /target/sys
mount -t sysfs sysfs /target/sys

cd /target

debootstrap breezy /target
cp /etc/apt/sources.list etc/apt
chroot /target
apt-get update
apt-get install ubuntu-base linux-amd64-generic ubuntu-desktop dmraid grub
```

but the last apt-get install failed.

can you give me a tip for an other way ?

best regards,
Daniel

---

### Post by T.Louis on 2006-10-25
Even though my German is not that good, I tried to look through it and just read this instead:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This worked for me, hope it helps.

---

### Post by Aberrix on 2006-10-25
Okay, an update... dmraid completely sucks. So does that How-to FakeRAID guide also... I wasted my entire Saturday morning last weekend trying to get it working... the end result.

I finally used the alternate-install CD, setup the RAID that way and it worked PERFECT! I was up and running in less than 15 minutes as compared to screwing with dmraid and that how to for over 6 hours in the morning...

Use the alternate-install CD to setup your RAID, you won't regret it.

---

### Post by T.Louis on 2006-10-25
> **Aberrix said:**
> Okay, an update... dmraid completely sucks. So does that How-to FakeRAID guide also... I wasted my entire Saturday morning last weekend trying to get it working... the end result.

I finally used the alternate-install CD, setup the RAID that way and it worked PERFECT! I was up and running in less than 15 minutes as compared to screwing with dmraid and that how to for over 6 hours in the morning...

Use the alternate-install CD to setup your RAID, you won't regret it.

No offence, but just cause the FakeRAID wiki did not work for you, dosen't mean it sucks. :-D

---

### Post by Aberrix on 2006-10-25
> **T.Louis said:**
> No offence, but just cause the FakeRAID wiki did not work for you, dosen't mean it sucks. :-D

Okay, I am sorry for the comment and take it back. I am sure it worked for others, but I pulled my hair out for hours trying to get it to work.

I still recommend using the alternate-install CD Vs. trying to use dmraid.

---

### Post by T.Louis on 2006-10-25
> **Aberrix said:**
> Okay, I am sorry for the comment and take it back. I am sure it worked for others, but I pulled my hair out for hours trying to get it to work.

I still recommend using the alternate-install CD Vs. trying to use dmraid.

I understand, done the same thing on other problems (pulled my hair out that is). It's best summarize in this icon: ](*,).         
;)

---

### Post by xaarr on 2006-10-25
> **T.Louis said:**
> 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

This worked for me, hope it helps.

happy thanks for this:

```
# For Edgy ubuntu-base has been removed, instead install ubuntu-minimal and ubuntu-standard
```

^^this is missing in the german version.

but now i wait for the final with my next try. :-D 

Thanks, and i will report..

---

### Post by wkulecz on 2006-10-25
After reading up on dmraid ("fakeraid") and mdadm I wonder why anyone would choose dmraid over mdadm unless you needed to share partitions on a raid array with windows.

Mdadm and the alternate install CD worked great for me.  I had troubles setting up a second array as raid5 but it turned out my SIL680 raid controller is corrupting data -- even a single ext3 drive.  I don't know if the controller is bad (it seemed to work with windows) or the SIL680 driver in broken or my new MB may not support this 5V PCI card (I need to look into this, just haven't had time)  I ordered some IDE to SATA adaptors ($13 ea. from newegg) so I can use my four SATA ports to setup the raid5.

--wally.

---

### Post by at0mic on 2006-10-25
> **wkulecz said:**
> After reading up on dmraid ("fakeraid") and mdadm I wonder why anyone would choose dmraid over mdadm unless you needed to share partitions on a raid array with windows.

Mdadm and the alternate install CD worked great for me.  I had troubles setting up a second array as raid5 but it turned out my SIL680 raid controller is corrupting data -- even a single ext3 drive.  I don't know if the controller is bad (it seemed to work with windows) or the SIL680 driver in broken or my new MB may not support this 5V PCI card (I need to look into this, just haven't had time)  I ordered some IDE to SATA adaptors ($13 ea. from newegg) so I can use my four SATA ports to setup the raid5.

--wally.


You need dmraid for already established chipset raids that init from bios . eg = nnvidia sata raid.

---

### Post by Bloodypriest on 2006-10-25
To solve the problem of installing edgy through debootstrap, you need to populate fstab BEFORE doing

apt-get install base-files linux-generic ubuntu-desktop dmraid grub

Also, if you have a faulty bios, there is a chance your dmraid arrays won't activate with the dmraid version that is in the repositories. You will need the dmraid version that's posted in this bug report:
[https://launchpad.net/bugs/54246](https://launchpad.net/bugs/54246)

---

### Post by xaarr on 2006-10-28
my new try fails, too.

the pre-install-scripts from dmraid, at, ubuntu-standard returns errors. ubuntu-standard fails because missing configured at package.

(i used the final desktop cd)

my next try is installing on a ide non raid hd, and then copying the installation-partition to the dmraid disc and creating a initrd-file with dmraid support.

i can not understand, why the dmraid driver is not supported by the installer. i know so many users, who use bios-raid - but not with ubuntu.
i think, it's no problem to support a special kernel with dmraid included, so i can boot with kernel parameter "dodmraid", so the 
dmraid driver is loaded at boot time. or why is the dmraid driver not in the standard ubuntu kernel integrated ?
thats only my opinion.

why i not use linux soft raid:

if i use linux software-raid, i must use the special partiton type for raid. with bios-raid or real raid controller i have normal type 0x83 linux partition. i can remove one harddisc (raid1) and us the hd with an other win machine and ext3-driver.


i will not stop trying before ubuntu boots on my machine.

greets,
Daniel

---

### Post by xaarr on 2006-10-30
hello,

now i have installed edgy !

my way in short words:

my raid mirror drives: sda & sdb

-install with alternate-cd and the installer to sda
-after install boot the desktop cd
-make the raid-mirror-drives equal
     # dd if=/dev/sda1 of=/dev/sdb1
     # dd if=/dev/sda2 of=/dev/sdb2
     # dd if=/dev/sda3 of=/dev/sdb3
-install dmraid
-create chroot-dir "/target" with "/" & "/boot" & dev & proc
-chroot to /target
-install dmraid
-edit fstab: change /Dev/sdax to /dev/mapper/isw_abcdeVolume0x
-install grub to /dev/mapper/isw_abcdeVolume0

reboot and have fun

i think, this way is workable on more systems.

best regards ant thanks for all tips,
Daniel.

---

### Post by aoberoi on 2006-11-19
I'm also having similar problems installing Edgy on a machine with a  software raid.

So, I've tried the HowTo's for "fakeRAID" but i dont get very far because the writer of the howto's system is quite different and im unsure of what steps to use and which to ignore.

I need some help on how to get Edgy installed so ill describe my system:

I have 2 300GB Seagate drives in a VIA VT8237 sata raid controller set up in raid0. i already have an 85GB partition set up for windows that is active and boots. I have a 232gb NTFS partition which is for documents and settings in windows (that i will be trying to share in linux using ntfs-3g). Asl there is an extended partition that is 6GB that has 2 logical partitions in it. The first is 5GB and i wish to mount that as /home in Ubuntu. The second is 1GB and i wish to use that as swap space. then i have another 6GB partition which i would like to use as root. The rest of the hard disk is unallocated.

In the end I may be adding more OSs to the machine. Specifically Vista. I have read some triple boot setup procedures and it seems that the best way to have one bootloader menu that you can use to choose from any OS is to first boot with windows xp NTLDR and when Vista installs it will import the contents of boot.ini from NTLDR. Keeping this in mind, I will be keeping my windows partition active so that i can do a chain load into ubuntu using the procedure described in [this page]("http://www.thinkwiki.org/wiki/How_to_setup_boot_loaders#Using_the_NT_Boot_Loader_to_boot_Linux").

To clarify what position Im in right now, I tried using this [HowTo]("https://help.ubuntu.com/community/FakeRaidHowto") and got as far as making my partitions and formatting them to the filesystems i want. After this, I tried using Ubiquity and the initially i was given the option to use my /dev/mapper/pdc******** device but then when it got to the partition manager (looks like gparted) the device is not listed in the drop down in the upper right corner. instead all i see is 2 300GB disks sda and sdb. The instructions frm there confuse me because I dont have a /boot partition and once again, I will be only installing the bootloader to my root partition because I will be booting with NTLDR.

From my understanding, using mdadm means that any partitions on the raid will not be usable form other OSs. In my case, i need to use Windows on the machine as well so this will not work for me.

As for installing using the alternate install CD; i tried doing this, (selecting text setup) and there was really no difference in which partitions were seen.

Any help would be greattttttly appreciated as i have spend many days on this problem.

---

