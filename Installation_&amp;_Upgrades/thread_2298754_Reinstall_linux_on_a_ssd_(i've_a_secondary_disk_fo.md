---
title: "Reinstall linux on a ssd (i've a secondary disk for data only)"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by COUTIER_Eric on 2015-10-13
Hello,
For the moment i've lubuntu installed. Root is installed on an ssd. I've a 500Gb traditional disk for data formatted in ext4. This disk is mounted using fstab in /mnt/ddata. In this disk, i have created one folder for each users. Inside each folder, i've created folder "Videos", "Pictures", "Documents", "Downloads", etc... After that, in home folder of each user, i've deleted folders "Videos", "Pictures", etc... created by the distribution then replaced them by symlink to "/mnt/ddata/username/Videos", ...

For personal reasons, i want to completely reinstall my lubuntu by another flavor of ubuntu. I want absolutely format my ssd.

My question is : after complete reinstallation, can i remount the 500Gb, knowing that folders created on this disk have owners from the old linux. I imagine with sudo i can chown with new users but i'm not sure.

---

### Post by yancek on 2015-10-13
Save a copy of the current fstab file as that definitely will not be saved on a new install.
Make note of the owner:group and permissions for all the directories for the different users.
I'm sure you will need to go through the process again of removing the various directories for each user and creating the symlinks.
You should be able to set the owner and permissions for each user sub-directory after reinstalling and creating your new users.

---

### Post by oldfred on 2015-10-13
I only have one user, but use the same data partitions in several Ubuntu installs.
I script my linking, but now use a line liner.
After mounting, my data partition:
# All folders to be linked in /home are in /data as folders
for i in `echo /mnt/data/*`;do ln -s $i; done

If reusing the same users, keep track of order or internal UID/GID. Normally first user is 1000 and then each added user is one digit more. If you assign in different order you will mix them up.

---

