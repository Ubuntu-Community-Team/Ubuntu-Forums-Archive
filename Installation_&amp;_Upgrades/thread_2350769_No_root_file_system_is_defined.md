---
title: "No root file system is defined"
date: 2017-01-27
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2017-01-27
Hi all,

I have 2 drives. I installed Win10 in sda (HD), and I want to install Ubuntu in sdb (SSD 128Gb).
I booted from a Live Ubuntu USB drive.
I just partitioned sdb with Gparted like this: root=20Gb, Primary, ext4. home=20Gb, Primary, ext4. swap=32Gb, swap, ext4.
I chose "Something else" (at the bottom) to install.
I selected sdb to install Ubuntu.
I chose sda from the dropdown menu below to choose the device for the bootloader.

When I click on the continue button, it pops up a message saying: "No root file system is defined. Please correct this from the partitioning menu."

What exactly this means?
And where is the "partitioning menu" anyway?

Thanks,

---

### Post by #&amp;thj^% on 2017-01-27
There should be a text field box below that option...and it should be (by you the installer) set to [/] without the brackets.
Maybe this will help also...my routine gose something like this:

  ```
  create an ext4 partition (huge space)
    select mounting point (/) and set as primary drive
    create a swap partition
    and set it as logical

    create bios reserved partition 
```

And yours may/will look something like this.

---

### Post by javierdl on 2017-01-27
[ATTACH=CONFIG]273415[/ATTACH]

The attached image is not of my installation, but shows the same options.
And there is no options that would help in that pop up window either.

---

### Post by deadflowr on 2017-01-27
> **javierdl said:**
> [ATTACH=CONFIG]273415[/ATTACH]

The attached image is not of my installation, but shows the same options.
And there is no options that would help in that pop up window either.

Highlight sda1, then select change.
Then set/reset the file system type (ext4) and then toggle the dropdown for the mountpoint to /
then click OK, or yes or whatever it is to exit.

---

### Post by #&amp;thj^% on 2017-01-27
Great Picture to give me ....It will now help you (See Screenshot)
Where I have circled in red..click that and more options will now be seen by you.
1. So click on the device or partition so it now highlighted>>>2. Next click on the change button below...3. Now edit it as you want.
HINT>>>Mount Point should look like this (/) without ()
There should be a screenshot coming to help you visually...forums are acting up today.

---

### Post by javierdl on 2017-01-27
[ATTACH=CONFIG]273417[/ATTACH]

Exactly, deadflowr!
It's on the lower right corner of the attached image.

What "Mount point" should I choose for a partition just to keep personal files?
Also, should I make partitions for "/var", "/tmp", or something else?

---

### Post by #&amp;thj^% on 2017-01-27
No  "partitions for "/var", "/tmp", or something else" will be created during the install.

---

