---
title: "How to install Ubuntu over existing Kubuntu?"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2010-02-03
I've been using Ubuntu for about 2 years now and I have a Kubuntu 9.04 on my Desktop PC. Now, I could apply all the updates and  download and install Gnome on Kubuntu .. However, due to restrictions on my internet connection, that isn't a practical option. What I do have is a shiny new Ubuntu 9.10 CD from which I would like to install ubuntu 9.10 on my desktop. I would like to install Ubuntu 9.10 OVER the existing Kubuntu installation. However, I don't know how to do this.. 
Here's what the partitions  look like when I started the installer.
What must I do to erase the Kubuntu installtion? 
I have a 160 GB hard drive on which XP and Kubuntu 9.04 are installed. There is also another 40GB hard drive. As I've said before, I want to install over the Kubuntu installation  ( I don't want more than 2 OSes on my PC) so the 40 GB harddrive should be left alone. 
PS.. although the screenshot shows the existing installtion to be 9.04, I can't ever remember upgrading to 9.04. I think it's 8.10. I'll post check and post back).

---

### Post by darkod on 2010-02-03
You have two options:
1. You could use the manual partitioning, in which case you select /dev/sda5 and click on the Change button at the bottom, then set the filesystem as ext4, mount point as /, and tick the format box to wipe the previous install. Of course, this would DESTROY all data on /dev/sda5.
Then you also select /dev/sda6 and click the Change button, select swap area and mount point swap, and that's it.

2. The other option is to use the guided install of 9.10 but then first you need to boot with 9.10 cd to the live desktop (Try Ubuntu option), open Gparted and delete /dev/sda5 and /dev/sda6, then also the extended partition that was holding them. That will create unallocated space.
After that boot with the ubuntu cd and select Install Ubuntu, and in step 4 tell it to use Largest Available Free space which will use the unallocated space and create a default guided install.

---

### Post by mahela007 on 2010-02-03
thanks for the reply. What about grub? will the Ubuntu installer take care of that?

---

### Post by darkod on 2010-02-03
Yes, grub2 will be installed by the installer. Since you have two drives it's probably better to check in the last screen of the installer, before you click on Install, click on Advanced and check where grub2 will get installed. It should be on the same disk.
So, if your 160GB disk is called /dev/sda, it should also say /dev/sda for grub2 destination, if /dev/sdb, then /dev/sdb.

---

