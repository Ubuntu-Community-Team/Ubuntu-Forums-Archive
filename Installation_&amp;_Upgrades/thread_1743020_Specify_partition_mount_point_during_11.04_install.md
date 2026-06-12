---
title: "Specify partition mount point during 11.04 installation"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by barbwire on 2011-04-29
Does anyone know if it's possible to manually specify the mount point for partitions during the 11.04 installation?

Every other release has allowed me to type in my desired mount point but now it seems that I am only able to select one of the mount points in the drop down.

I can (I suppose) manually add the partitions to /etc/fstab after install but I thought I might be missing something.


Thanks.

---

### Post by dino99 on 2011-04-29
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by kansasnoob on 2011-04-29
That's due to a bug that was found too late to get it fixed prior to release, but I did get it in the release notes:

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Boot,%20installation%20and%20post-install](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Boot,%20installation%20and%20post-install)

> The manual mount point entry box in the desktop installer's partitioner does not accept keyboard input. The drop-down still works, so various standard mount points may be selected, and copying and pasting within the entry box also works. This was noticed too late to be corrected for 11.04. In the meantime, you can mount partitions manually later, use copy-and-paste, or use the alternate install CD.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

---

### Post by barbwire on 2011-04-29
Great - I'll try the copy & paste trick - thanks.

---

### Post by zebieksterc on 2011-05-03
It`s too bad that you have this kind mistakes! It`s better to fix before realising it! It`s an installer not somekind of ordinary program.

 One big mistake of your side and system with data could be deleted :(. This step of OS should be tested tested and all, also small mistakes fixed! 

I think that we could wait some more days. It`s my opinion. :)

Good luck

---

### Post by Bucic on 2011-05-03
:roll:

---

### Post by Bucic on 2011-05-08
Is it fixed already in the image files currently downloadable from the official ubuntu site?

---

### Post by calmness on 2011-05-08
It still hasn't been fixed.  I downloaded it a couple of hours ago and it is still the same.

---

### Post by Bucic on 2011-05-08
Thanks for the info!

---

### Post by kansasnoob on 2011-05-08
It will NOT be fixed in Natty.

---

### Post by Bucic on 2011-05-31
So there is no way to use a custom mount point like */var/lib/games* ?

---

### Post by kansasnoob on 2011-05-31
> **Bucic said:**
> So there is no way to use a custom mount point like */var/lib/games* ?

Did you bother reading the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

If you begin the installation from the live desktop you can open the text editor and then "copy-n-paste" from there.

It's already fixed in OO alpha 1.

---

### Post by Bucic on 2011-06-01
> **kansasnoob said:**
> Did you bother reading the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

If you begin the installation from the live desktop you can open the text editor and then "copy-n-paste" from there.

It's already fixed in OO alpha 1.
TBH no, I didn't, sorry :oops: I thought what has been written here is all there is to it (copying from the drop-down dialogue). Thanks for the tip.

---

