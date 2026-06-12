---
title: "GRUB install failed...Now what?"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stuart.reinke on 2009-06-27
Hi folks,

I tried to install Karmic Alpha2 last night. Installation went off without a hitch until the end when it was time to install Grub2. 

The error read "Executing update-grub failed  Fatal error" 

I did use the boot option that was suggested in the release notes. (probably did it wrong)

I know this is not a new problem and this bug has been reported several times. 

I reinstalled grub with my alt. install cd and can get Hardy to boot again.

Should I try to change the grub I currently am using to create a dual boot? (assuming the rest of the installation is ok)   or

Should I attempt a reinstall of Karmic?  or

Should I install Jaunty and upgrade?   or

Leave the testing to someone more experienced :(

---

### Post by ronacc on 2009-06-27
probably the safest thing to do at this point would be to add a boot stanza to your existing grub menu.lst . If you are testing on your main box make sure you have good backups of your important data , Use your hardy install to mount your Karmic partition and if it looks ok try to boot it from your hardy grub .There are several threads in this forum about grub2 and how to handle problems with it in this forum if you choose to try a reinstall . I just let A2 install grub2 as I would on a normal install (did not use the option from the release notes ) and the only thing it got wrong was the UUID for the karmic install which I corrected using the live cd . If you do choose to reinstall read the threads here on grub2 first so you'll be ready .

---

### Post by stuart.reinke on 2009-06-27
> **ronacc said:**
> probably the safest thing to do at this point would be to add a boot stanza to your existing grub menu.lst. ... Use your hardy install to mount your Karmic partition and if it looks ok try to boot it from your hardy grub .... I just let A2 install grub2 as I would on a normal install (did not use the option from the release notes ) and the only thing it got wrong was the UUID for the karmic install which I corrected using the live cd . If you do choose to reinstall read the threads here on grub2 first so you'll be ready .

What is the UUID? I notice it is the same in all the stanzas referring to Hardy. Will it be the same for Karmic?

I think I'll try to edit grub menu.lst first. Will have to use a Jaunty live cd to look over the Karmic partition. (Hardy has no support for ext4)

---

### Post by ronacc on 2009-06-27
the UUID is the identifier of the partition , it will be unique for each partition on your system .you can find the UUID by going to ( in your jaunty live cd)  places>computer and mount your karmic partition , that will put an icon for that partition on your desktop , rt click on the Icon and select properties then volume  , you will see the UUID for that partition . you will also have to change the kernel# in the boot stanza to the kernel # for karmic if you modify your existing menu.lst .

---

### Post by psyke83 on 2009-06-27
The workaround for GRUB2 didn't work for me either, but I posted another method in the linked bug report [here]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/385995/comments/11").

---

