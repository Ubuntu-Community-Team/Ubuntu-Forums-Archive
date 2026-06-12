---
title: "symlinking usr"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by nzadLithium on 2007-12-24
hey I got a new disk today
i have it all setup. im using it to hold all home folders. I want to move my /usr directory onto this drive and then either somehow mount the /usr folder on the new drive so that it is still the /usr directory or symlink it to acheive the same thing. 
Will either of these work?

In both of these ways this is how i would set it up.
disk 1 is root with empty home and usr folders
new disk holds is mounted to empty /home on disk1
then on new disk folder /usr is mounted to /usr folder on disk1

new disk would essentially be like this
-cmaster (my home folder)
-nicholas (another home folder)
-usr (the usr folder)

I would prefer not to create a seperate partition for the usr directory on this new disk as then i could no longer use that space for files. (unless i moved them all there as root user which would be stupid)

---

### Post by nzadLithium on 2007-12-25
yeah! it worked me ftw or something :D

i did it like this
1. reboot into recovery
2. make directory on new disk called usr
3. cp -dpR /usr/* /home/usr (my new disk is mounted to /home)
4. mv /usr /usr_old
5. ls -s /usr /home/usr

reboot and its good to go :D

i'll probably leave my old usr directory there for a few days just in case anything goes funny. (dunno whether theres anything dodgy about using a sym link like that)

if its still all good then ill delete it. Yay! more root disk space for me :D and i might actually be able to install UT2004 now that i have usr on a bigger disk :D

---

