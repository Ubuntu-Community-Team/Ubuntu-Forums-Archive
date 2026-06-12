---
title: "&quot;Could not calculate the upgrade&quot; 7.04--&gt;7.10"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by apathos on 2008-04-25
I'm returning to Ubuntu after almost a year away.  The documentation strongly suggests to progress through the upgrades (to 8.04) rather than a clean install.  

The update stops every time in the second step "Modifying the software channels", with this error message:

"Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."

Being an ubuntu newbie, can anyone help me? Or at least set me in the right direction?  I searched the forums for this error message, and didn't turn anything up.

Would it be of help to post those log files here?

-Jeff

---

### Post by Pumalite on 2008-04-25
You might have ran out of space in /boot

---

### Post by apathos on 2008-04-25
how do i verify this?  If so, how can I make more room?

---

### Post by Pumalite on 2008-04-25
Do you have a /boot partition?

---

### Post by Pumalite on 2008-04-25
You could post:
sudo fdisk -l

---

### Post by Pumalite on 2008-04-25
[http://ubuntuforums.org/showthread.php?t=764452](http://ubuntuforums.org/showthread.php?t=764452)

---

### Post by apathos on 2008-04-25
Here is sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         701       15290   117194175    7  HPFS/NTFS
/dev/sda2               1         700     5622718+   b  W95 FAT32
/dev/sda3           15291       30401   121379107+   5  Extended
/dev/sda5           15291       22939    61440529+  83  Linux
/dev/sda6           22940       26126    25599546   83  Linux
/dev/sda7           26127       29313    25599546   83  Linux
/dev/sda8           29314       30401     8739328+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by apathos on 2008-04-25
EDIT: Double-post

---

### Post by Pumalite on 2008-04-25
You do not seem to have a boot partition. These are other possible causes:
This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

I would wait and try again.

---

### Post by Lantesh on 2008-04-25
> **apathos said:**
> I'm returning to Ubuntu after almost a year away.  The documentation strongly suggests to progress through the upgrades (to 8.04) rather than a clean install.

I'm not sure where you read this, but it is incorrect.  While yes it is recommended that if you are going to upgrade that you must do it incrementally, upgrading in general is not preferred.  If you are having trouble with the upgrade then by all means do a clean install.  It will save you a big headache, and give you a more stable and less bloated system.

---

### Post by Pumalite on 2008-04-25
Have you tried this?:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by apathos on 2008-05-02
> **Pumalite said:**
> Have you tried this?:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

Well, the update manager never did work, but usingthose last two commands did, I'm writing this from FF3 in Ubuntu 8.04!

Thank you for the help Pumalite!

--Jeff

---

### Post by Pumalite on 2008-05-02
You are welcome. Good luck.

---

