---
title: "/boot partition too small"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by Kilarin on 2014-08-14
A few months ago I did a fresh install of xubuntu 14.04, and set it up with full disk encryption following the very useful instructions here: [http://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/](http://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/)

On that link they stated that 200 meg was plenty for the /boot partition, so I upped mine above that (to 286) and everything has been working just fine.  

BUT, this evening a software update came through and when I tried to install it I was informed that my /boot partition was too small by about 9 meg.  Seems I've gotten myself into a mess here because my /boot partion is immediately followed by my encrypted partition:

[img]https://cdn.mediacru.sh/uuDntL5hX_z6.png[/img]

I tried shrinking sda1 (the almost never used windows partition) and moving the /boot to take up that space, but GParted gave me a dire warning that moving the beginning of my boot partition would almost certainly stop the computer from booting.  (duh!)  And GParted can't shrink the encrypted drive because, being encrypted, it looks like it is all used.

Is there any option here better than backing up the entire encrypted drive and then rebuilding the encrypted partition and leaving some room at the beginning to expand the end of the /boot partition?  Is there any way to shrink and move the encrypted drive?  OR, to safely shrink the end of sda1 and move the beginning of the boot partition?

Andy advice would be GREATLY appreciated!

---

### Post by ian-weisser on 2014-08-14
286 MB should indeed be plenty of space.
List the files on your /boot drive.
If you have more than two kernels installed, remove the ones you are not using.
*USE THE PACKAGE MANAGER* to remove installed kernels. Do not delete individual files manually - that makes things much worse.

This is a known bug (search for "/boot" in this forum) that affects encrypted and LVM installs.

---

### Post by Kilarin on 2014-08-15
thank you!!!!
I ran this to clear out the old kernels:
```
current=`uname -r` && uninstall="" && for version in `dpkg -l linux-image* | grep ii | awk '{ print $2}'`; do if [[ "$version" < "linux-image-$current" ]]; then uninstall=$uninstall" $version"; fi; done && sudo apt-get purge $uninstall -y && sudo update-grub2
```
Worked like a charm, /boot is down to 44.5meg, my software update worked without a hitch, and all is well, all is well, and all manner of things shall be well!

thank you!

---

### Post by mörgæs on 2014-08-15
Good, please mark the thread 'solved'.

---

