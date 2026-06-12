---
title: "server install with var &amp; home on other partition"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by eggzenbeanz on 2015-11-03
hello,

I want to install server edition, but with the /home & /var directories on a larger partition and / other directories on the smaller partition.

I can't see an option in the installer to select both var and home - there is a manual option though but I've not had any success with the format eg /home,/var etc

cheers

---

### Post by SeijiSensei on 2015-11-03
When you choose manual partitioning, you can specify the filesystem and mount point for each partition.  You will need three partitions, one for /, one for /home, and one for /var.  Set aside 10-40 GB for /.  How much you need for the other two depends on the size of the drive.  Usually /home should be the largest filesystem.  Unless you have lots of logs or big databases, /var need not be much bigger than the root partition.  I keep large logs on my virtual webserver at Linode; it's currently running about 15 GB.

---

### Post by eggzenbeanz on 2015-11-04
Thanks - That's not quite what I'm after. I want to know if the server installer will allow me to place var & home directories on the same partition. I can only see the option to place each var and home on separate partitions

cheers

---

### Post by Lars Noodén on 2015-11-04
You can only put them on separate partitions in the installation.  

Another option, but one of uncertain viability or safety, would be to make an extra partition.  Then boot with a rescue disc and move /var and /home to subdirectories there followed by symlinking /var and /home to the appropriate subdirectories.

---

### Post by SeijiSensei on 2015-11-04
The symlink approach is an option, but I don't understand why you are so committed to having a single partition.  Are you worried about the limit of four primary partitions?  That's easily solved by making one of them a large extended partition.  Otherwise, I suggest you follow the Unix standard of having one filesystem per mount point with separate partitions for /var and /home.

Perhaps you can explain to us why you want only one partition?

---

### Post by watfordjc on 2015-11-05
/home and /var would be mount points within /.
If they both were on the same partition then /var/tmp/ and /home/tmp/ would be the same directory, as would /home/username/ and /var/username/.

If you really want to do it, this is how I'd do it. Stick /var on a separate partition (a /var partition), and after the OS is installed enable the root account (if applicable), login as root (might have to set a password first), create /var/home/, move everything in /home/ to inside /var/home/ (keep permissions and everything), edit /etc/passwd and rename all instances of /home/ to /var/home/ (then save the file), delete /home/ (using rmdir will ensure it is already empty), create a symlink pointing from /home/ to /var/home/ (optional since it is no longer being used), logout as root, try logging in as your user, remove root's password and disable root account (if so desired).

There is one obvious issue with doing this: because /home/ is inside /var/ there isn't the safety of your files being on a separate partition from the OS files. Reinstalling could wipe out /var and everything inside it (including /var/home/).

There are alternative ways like those already mentioned, as well as creating an LVM on the physical partition and creating a LVM partition for /home and another LVM partition for /var.

---

