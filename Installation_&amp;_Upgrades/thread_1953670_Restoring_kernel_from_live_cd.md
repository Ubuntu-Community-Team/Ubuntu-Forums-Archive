---
title: "Restoring kernel from live cd"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by azyunomi on 2012-04-06
I accidentally removed an important kernel from my boot folder and now my system will not start.

I would like to be able to overwrite the kernels on my harddrive, right from my installation disk.

I am running into a few walls in trying to do this.  For example, when I try to follow the steps that I found on this page:

http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels[/URL]

On the 1st step of writing the command "sudo mount /dev/sda2 /mnt"

I get the error message "mount: you must specify the filesystem type"

Here is a look at my screen,  showing a few detail of what my system looks like:

[IMG]http://i66.photobucket.com/albums/h276/azyunomi/ubuntunotes32.jpg[/IMG]

Thank you for any help you make have to offer.

---

### Post by azyunomi on 2012-04-07
I solved this by using boot-repair.  I initialized boot-repair to reinstall grub.  Then when I saw that my grub looked relatively normal.  Initialized mbr repair, which apparently fixed my master boot record, and gave me my harddrive back.

So now its time to back up and confirm the fix by finding out if my system will reboot normally.  Plus it looks like I will have to check a few small things to bring my server back online.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

