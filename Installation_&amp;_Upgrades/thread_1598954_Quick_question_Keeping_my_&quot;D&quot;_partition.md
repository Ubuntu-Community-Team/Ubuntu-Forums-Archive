---
title: "Quick question: Keeping my &quot;D&quot; partition"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by swimon on 2010-10-17
Hello, 

I'm stuck in the beginning of the installation process of Ubuntu 10.10

My computer has a "C"-partition, which only contains my windows operating system. This one can be erased.

And a "D"-partition, which contains my movies en music and such, I would like to keep this one. 

Both are ntfs.

I'm not familiar with Linux partitions and filesystems. So I'm not sure what options to choose in the "advanced" partition option?

Btw: I think my "C" partion translates to "sda1" and "D" translates to "sda5" in Linux language :-)

Grtz

---

### Post by 73ckn797 on 2010-10-17
> **swimon said:**
> Hello, 

I'm stuck in the beginning of the installation process of Ubuntu 10.10

My computer has a "C"-partition, which only contains my windows operating system. This one can be erased.

And a "D"-partition, which contains my movies en music and such, I would like to keep this one. 

Both are ntfs.

I'm not familiar with Linux partitions and filesystems. So I'm not sure what options to choose in the "advanced" partition option?

Btw: I think my "C" partion translates to "sda1" and "D" translates to "sda5" in Linux language :-)

Grtz

When in the partitioning section of the installation, I believe you can designate the sda5/D drive to not be used. That is the default setting. It will be accessible after install is complete. I would recommend that you create a separate partition and designate it "/home" & leave it ntfs to keep your documents in. You may be able to designate the sda5 partition as the /home but do not mark it for formatting. I do not know whether being a ntfs partition will react as the /home since I have not tried that. If you later have to reinstall Ubuntu you can reuse the/home partition without loss of data.

Look here: [https://help.ubuntu.com/10.04/installation-guide/index.html](https://help.ubuntu.com/10.04/installation-guide/index.html)

---

### Post by swimon on 2010-10-17
I'm still not sure what I have to do. Can't seem to find it in the link you supplied either.

/dev/sda
[INDENT]/dev/sda1[/INDENT]
[INDENT]/dev/sda5[/INDENT]

sda1: 
I guess I need to select to format it, but what filesystem should I use and what mount point?

sda5:
You suggested I shouldnt format it, make it NTFS and mount point /home. But I can only choose mount point /dos or /windows. What should I choose?

thanks

---

### Post by Rubi1200 on 2010-10-17
Hi,
to give us a better idea of what you are seeing, use the LiveCD and open System > Administration > GParted and take a screenshot to post here. Visuals always help when offering advice :)

---

### Post by swimon on 2010-10-17
[IMG]http://i54.tinypic.com/29favis.png[/IMG]

Is this what you asked for? It's not the same screen as I get during the installation though... (but cant make screenshot of that)

---

### Post by Rubi1200 on 2010-10-17
Thanks for the screenshot.

Okay, let me get this straight; you want to delete/get rid of Windows on the C drive (sda1) but keep your movies etc. on the D drive (sda5)?

This is not a problem.

Use the GParted tool and delete the partition on sda1 and leave it unformatted.

Then start the installer on the Desktop and when it comes time to install choose the option to install to the largest continuous free space. Ubuntu will then do the rest for you.

Alternatively, start the installer and when you get to manual partitioning choose to format sda1 as Ext4 and the mount point as / (this is the root file system in Linux). 

When you get to the final screen just before install make sure there is no mention of sda5 or #partition 5 of ...mentioned; if there is go back and do it again or ask here first.

However, please make a backup of your data before you start because there is always a chance something could go wrong.

Also, are you sure you want to get rid of Windows completely?

---

### Post by swimon on 2010-10-17
okay thanks, i'll try what you just said

but i'll have to make a backup first just to be sure then

yeah, i'm sure i want to remove windows all together, this is an old computer, want to use it for playing around with linux and such.

thanks for helping.

---

### Post by swimon on 2010-10-17
Thanks, I think I did it, it's installing right now. 

I used this tutorial too: [http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Because I needed to configure a swap area and such as well...

Grtz!

---

### Post by Rubi1200 on 2010-10-18
Glad you got it working :)

Enjoy, and don't forget to post on the forums if you ever need help with anything.

---

