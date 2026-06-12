---
title: "ubuntu mini.iso preseed issues BIG issues"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by rizza on 2007-05-05
Hello Everyone who reads this I hope someone can help.

I'm a long time debian user aka 2.2 on. By no manner a master though. Anyway...I'm using preseeding to create auto install setups for multiple machines for a non-profit. I've used preseeding on debian for a little while and have gotten used to it functionality. Ubuntu used the debian installer as its alternate installer so I thought that preseeding should work the same. Well so far not true. 

1) boot options like install auto=true don't seem to work. I still get prompted for keyboard setup. This command delays these options to allow preseeding this setup after the setup of networking is complete for download of preseed files. Does anyone know why and how to fix this?

2) Partitioning automatically whole disk asks for a 'yes' no matter how I try to get around it. Any ideas would be great.

3) I use apt-cacher to speed up installs locally. I can't seem to get ubuntu installer to use this during installation. Again. Ideas on a fix would be great.

Now just to clarify my conclusions that cause these questions/problems. I use basically the same preseed file short of changing specific things that different  between debian and ubuntu. For example ubuntu-standard and ubuntu-desktop instead of standard and desktop for debian. And the repository my apt-cacher uses.

This preseed works correctly with no questions with debian installer not ubuntu's interpretation.

PLEASE HELP! I'm out of ideas that explain these issues.

d-i debian-installer/locale string en_US
d-i console-keymaps-at/keymap select us
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string set-me-please
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/wireless_wep string
d-i mirror/country string enter United States
#d-i mirror/http/hostname string 
d-i mirror/http/hostname string 192.168.1.124:3142
d-i mirror/http/directory string /apt-cacher/http.us.archive.ubuntu.com/ubuntu (This becomes /apt-cacher/http.us.debian.org/debian)
d-i mirror/http/proxy string
d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/choose_recipe select All files in one partition (recommended for new users)
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select Finish partitioning and write changes to disk
d-i partman/confirm boolean true
d-i clock-setup/utc boolean true
d-i time/zone string US/Mountain.
d-i apt-setup/non-free boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true
d-i debian-installer/allow_unauthenticated string true
d-i passwd/root-login boolean false
d-i passwd/user-fullname string user
d-i passwd/username string user
# Normal user's password, either in clear text
d-i passwd/user-password password user
d-i passwd/user-password-again password user
# or encrypted using an MD5 hash.
#d-i passwd/user-password-crypted password [MD5 hash]
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
tasksel tasksel/first multiselect standard, gnome-desktop (debian evuivalent used here as well)
d-i pkgsel/include string openssh-server mc
popularity-contest popularity-contest/participate boolean false
d-i finish-install/reboot_in_progress note
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
#xserver-xorg xserver-xorg/config/monitor/lcd boolean true
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1024x768 @ 60 Hz

---

### Post by kerry_s on 2007-05-05
are you using the mini.iso net installer? 
it is the closest to debian installer,

feisty-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/)

edgy-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)

dapper-> [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/)

---

### Post by rizza on 2007-05-06
Thanks for the quick reply. I'm way ahead of you though. I only use mini.iso. Everything should be downloaded right then no old debs to update after the install. There seems to be some differences between the 2 installers. The questions asked for a regular install no preseeding are even different I'm frustrated!!! I can't find any justification for these changes in ubuntu installer compared to debians installer. most importantly these net/mini.iso installers aren't used by first time users. I hope someone has a fix/answer to these problems.

---

### Post by zvacet on 2007-05-06
[http://www.psychocats.net/ubuntu/minimal#barebones]("http://www.psychocats.net/ubuntu/minimal#barebones")

---

### Post by paljas on 2007-05-07
Hi Rizza,

I am also struggling with your step 2. Problem one, I solved with:

LABEL staff
    kernel ubuntu-installer/i386/linux
    append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw  debian-installer/locale=en_US console-setup/layoutcode=us netcfg/get_hostname=unassigned-hostname preseed/url=http://etc.etc.  --

(assuming you also use pxe booting)

BTW: I use the installer from the alternate CD (7.04), is there any difference compared to  the mini.iso?

---

### Post by rizza on 2007-05-07
Thanks for your reply. I'll try that tonight. Now hopefully someone has an answer to the other problems...I hope.

As for the differences between alternate cd image and mini iso, The mini iso only has the things necassary to start the installer and networking. Everything else it needs from the net or package server. The alternate has packages on the disk like base install in the case of debian net install cd. Size difference is HUGE. Mini iso is about 8-9 mb total the others are way bigger as you problably already know. Also usb support is out as far as I can tell I couldn't mount my usb thumb drive using ubuntu mini iso. The good thing about mini iso is that your installing packages straight from the source making updates after install minimal if any.

---

### Post by placatedmayehm on 2007-05-08
Hi Rizza,

My site is currently using Debian installs via netinst isos and preseed-over-http.  (I'm slowly moving my boss to Ubuntu.)  Anyway, I've been deeply entrenched in setting up our infrastructure to do the Debian installs and am looking to do preseeds w/ Ubuntu come this fall, so your questions are quite relevant.

Concerning the still prompting for keyboard problem:  have you tried adding something like "debconf/priority=critical" to your install boot string?  What is your full boot string?  Just "install auto=true"?

As for apt-cacher, you might try setting up the path_map in the server's apt-cacher.conf to make things easier.  Mine is currently:

```
path_map = debian ftp.at.debian.org/debian ftp.us.debian.org/debian ; security security.debian.org ; ubuntu archive.ubuntu.com/ubuntu
```

This gives a set of preseed lines like this (debian/etch, since I've not setup ubuntu yet):
```
d-i mirror/http/hostname string 152.X.X.X:3142
d-i mirror/http/directory string /ubuntu
```
(I x'd out the IP we're using, since it's not quite secured to the outside world just yet.)  O:)

Hope this helps!
-pm

---

### Post by rizza on 2007-05-08
good news! Paljas post work perfectly. ThankYou sooo much. I still don't like the fact that auto=true doesn't work but Paljas's fix does the trick. Also my problems with partman and auto creating the partition is also fixed. It seems ubuntu installer can't or won't use /dev/disc/.. device identification. All I had to do was change it to traditional /dev/hda or what ever type of disc your partitioning.  Also placing my preseed/url last on my boot line works. I don't know why that matters. It never did in debian. Again thanks to everyone who has/is participating in this forum thread I hope to continue to add to it as I can and reply to it as well. Hopefully some of what we learn can be compiled into a small how-to type of thing that can make this unnecasary for other in the future. At this point there seems to be to many variants between the two installers (debian & ubuntu) to just use the debian doc for preseeding in ubuntu.

---

### Post by paljas on 2007-05-08
Hi Rizza,

Exactly what partman lines do you have in your preseed file? Are you using 7.04?

(i'm afraid this autoinstall is gonna be a long road. It's undocumented, although it seems
diffent than the debian stuff. Will I be able to included some ldap info, after fixing this partman stuff?)

I will try the mini.iso installer now, as the possibility remains that one is different.

Cheers,

---

### Post by rizza on 2007-05-09
Hello Paljas

My partman lines are identical to the ones list on my first post I just changed /dev/disc/disc...etc to /dev/hda for first ide device. Thats it, it works now as it did under debian the original way.

---

### Post by kschwerd on 2007-05-17
Just a quick note. Not sure if this was planned and not sure if there are any unknown consequences to doing this, but you can specify

d-i partman-auto/disk string /dev/?da

That will work for both IDE and SATA drives.  As I have not found any other mention of this on the Net, I am not sure what other issues may arise by doing this, though.  If you try this and find an error, please let me know.

---

