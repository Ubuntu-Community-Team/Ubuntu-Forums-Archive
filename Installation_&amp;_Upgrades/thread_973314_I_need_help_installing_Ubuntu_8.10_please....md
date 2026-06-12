---
title: "I need help installing Ubuntu 8.10 please..."
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by The Noob on 2008-11-06
Well more to re-assure myself that im doing this right.I have read other things but like my name says...so i am trying to dual boot with vista pre-installed and i cant seem to shrink the partition it only allows 6 gigs? but i have 250 gigs also i have defragged it 3 times.

---

### Post by Pumalite on 2008-11-06
You have to allocate space for Ubuntu with the Vista partitioner first. You cannot use the Ubuntu Live CD to 'shrink' Vista.

---

### Post by The Noob on 2008-11-06
> **Pumalite said:**
> You have to allocate space for Ubuntu with the Vista partitioner first. You cannot use the Ubuntu Live CD to 'shrink' Vista.Sorry i should have been more specific. i used the vista partitioner, i have Ubuntu on a CD still, but i am stuck on partitioning the HD on vista.

---

### Post by Pumalite on 2008-11-06
At the partitioner; you have to go 'Manual' and pick the free space and make 3 'New' partitions:
10 GB for '/'
The rest minus your RAM for /home
Your amount of RAM for /swap
Then proceed with the installation.

---

### Post by The Noob on 2008-11-06
im sorry i didn't really understand what you typed(are you saying i should use gparted?)because the vista one isnt working it does not let me shrink it well it lets me shrink only 6 gigs i need more but it does not let me)

---

### Post by Pumalite on 2008-11-06
You can also make one large partition out of the free space and make it 'mount point' '/'

---

### Post by Roger Hoo on 2008-11-06
> **The Noob said:**
> Well more to re-assure myself that im doing this right.I have read other things but like my name says...so i am trying to dual boot with vista pre-installed and i cant seem to shrink the partition it only allows 6 gigs? but i have 250 gigs also i have defragged it 3 times.

y not use the tool DISKMAN, it can change the partions not affecting the system,i dont'know it has English version.

---

### Post by The Noob on 2008-11-06
dudes im going hysterical i know little of computers and doing stuff on them keep it more simple please.so how can i shrink my vista partition ? Becasue its not letting me shrink it to my desire, it only has 6 gigs available? any solutions

---

### Post by Pumalite on 2008-11-06
Maybe you should turn PageFile to '0'. You can turn it after the partitioning to its original size.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by The Noob on 2008-11-06
Alright thanks,ill try those steps and post back here when im done

---

### Post by The Noob on 2008-11-08
Well those steps only made it worse...i can [COLOR="Red"]only[/COLOR] shrink 413MB.Also am i suppose to use perfect disk to shrink? Because i used the vista partitioner.

---

### Post by caljohnsmith on 2008-11-08
As mentioned earlier by Pumalite, it is better if you can use Vista's partitioner to do the resizing, but since you can't, you can use Ubuntu's partition editor gparted. You just have to make sure you have either your Vista Install CD or a Vista Recovery CD that you can download from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), because after using gparted you'll need to run a command from the Vista CD in order to update Vista's partition table to get Vista booting OK again. To use gparted, just boot your Live CD, select the option "try Ubuntu without making changes", and when you get to the desktop, go to System > Admin > Partition Editor. 

Give that a shot and let me know how it goes. :)

---

