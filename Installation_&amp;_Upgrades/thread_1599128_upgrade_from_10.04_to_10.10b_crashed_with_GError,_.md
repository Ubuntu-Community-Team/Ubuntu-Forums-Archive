---
title: "upgrade from 10.04 to 10.10b crashed with GError, broke system"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by pengpengpeng on 2010-10-17
hi,
i wanted to upgrade my ubuntu system to meerkat beta via update manager like i upgraded it the last 5+ times.

a bug showed up that i can recall from updating files previously:
some software installtions via update manager triggered the programm nicotine+ (i think is was something like man-lib or man-db that, when called by the installtion programm, would trigger nicotine too).
since i can close that nicotine+-window and the installation process isnt  bothered any further i didnt mind.

now with this upgrade, i had to close nicotine+ around 5 times since it got triggered together with some of the files that got updated/installed in this upgrade.

and then what happened:
GError
something about an "unrecognized image file", it concerned a py file that was named &quot;nicotine&quot;...  

so i waited for 10 mins and figured out that the update process had stopped.
i couldnt resist and logged out, wanting to delete nicotine from my system and to reinitialize the upgrade.
well, nothing works since then, grub only lets me choose different kernels which didnt help much as there was no way to startx.

my question is:

how can i reset this upgrade mess or bring this pending upgrade to an end?
can i do an upgrade via network, based on the emergency shell that comes up in some kernel-recoverymodes?
or should i burn a livecd, boot it and then do what? repair? try another upgrade? delete nicotine?


having 'consumed' ubuntu for years now i still wouldnt know what else to do then posting here.
google and forum search didnt help so i give up after ~2hrs. searching.

thanks in advance

---

### Post by pengpengpeng on 2010-10-19
okay,  now i tried using a 10.04 live cd.
i had no idea what to do so i started looking for something helpful,
eventually i came across 3 or 4 posts..

here is what i did (and i really have no idea at all what this means :P)

* live-cd booted up perfectly, then when the desktop-wallpaper is already up a message appeared: something about a severe error that cant be reproduced and that livecd would start a live session now...well, live mode is fine with me

* via network manager i configured a dsl connection and connected to internet 

* next i have to install cryptsetup and lvm2 to open my luks encrypted partition on which the broken ubuntu lies 

```
sudo apt-get install lvm2 cryptsetup
```* after installation i need to add the LKM (loadable linux kernel module) dm-crypt to the kernel

```
sudo modprobe dm-crypt
```* then i had to encrypt my partition, in this case its sda5, you will then be asked to enter the password to unlock partiton

```
sudo cryptsetup luksOpen /dev/sda5 crypt1
```* scanning for physical LVM volumes via

```
sudo vgscan
```* make the partition available (-ay) to kernel

```
sudo vgchange -ay nameofyourpartition
```* get information on logical volumes

```
sudo lvs
```* make a directory in /mnt called ie "repair"

```
mkdir /mnt/repair
```* mount your /root into a the new /mnt/repair directory 

```
mount /dev/nameofyourpartition/root /mnt/repair
```

* accessed it with

```
sudo chroot /mnt/repair su
```so, everything was there, so thats good when i want to backup  

but now: i get lots of error messages trying to 
"sudo apt-get upgrade" 
"sudo dpgk -a --configure" 
"sudo apt-get install -f" 

this is a waste of time, a broken ubuntu system cant be repaired, or can it?!  
after a reboot i tried once more to let grub do its thing, the ubuntu splash comes up, asking me to encrypt my luks partition, that works perfectly, after that some computing and a black screen.

im very sad and confused...anyone knows anything?

---

