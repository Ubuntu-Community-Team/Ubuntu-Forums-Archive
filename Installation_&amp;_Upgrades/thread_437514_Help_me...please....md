---
title: "Help me...please..."
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-05-08
Well i completely screwed up my ubuntu installation but luckily i have my home partition separate.  i would like to reinstall ubuntu using my home partition how would i go about doing this?

im writing this from the live cd so please give me some help anybody i have no os right now

---

### Post by mikewhatever on 2007-05-08
I suppose you want to reinstall formatting root and swap, but not /home.

---

### Post by Opeth115 on 2007-05-09
yes i do i want jusdt reinstall ubuntu with my home partition being used so i don't loose all of my stuff

---

### Post by tommcd on 2007-05-09
Reinstall from the live CD. When you get to partitioning, choose "manually edit partition table". You will see your partitions listed. 
Choose to reformat /root, choose ext3 file system, and / mount point
Choose to reformat swap as swap, mount it as swap.
Do not reformat /home, mount it as /home.
Do not format any other partitions you want to keep, such as a windows partition. If you leave a windows partiton alone it will be mounted under /media.
Hope this helps.

---

### Post by Opeth115 on 2007-05-09
ok i did that but im getting this error

The ext3 file system creation in partition #1 of SCSI3 (0,0,0) (sda) failed.

---

### Post by tommcd on 2007-05-09
Did you choose to reformat it? Can you list your partitions please? Do you have a dual boot system? Also, I assume you have just one hard drive correct?

---

### Post by Opeth115 on 2007-05-09
yes i have one 400 gig hard drive.  my partitions according to the installer are:


/dev/sda1
/dev/sda3 (my home parition)
/dev/sda5 swap

it dosn't let me check the box for my swap partition eaither only my home and root and my home i don't want to format

and no i don't have a dual boot system only ubuntu for me =)

---

### Post by tommcd on 2007-05-09
Make sure you selected "manually edit partition table" (3rd option listed here):

[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

You don't have to reformat swap if it is already formatted as swap. Just choose to mount it as swap. If you can not reformat and reinstall ubuntu on /dev/sda1, and mount it as /, then choose to delete / and swap. This will leave free space. Choose to create new partitions for / and swap. Make them the same size they were before, and mount them as /, and swap, respectively.
It should let you reformat / though.

---

