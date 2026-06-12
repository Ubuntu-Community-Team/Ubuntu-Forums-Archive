---
title: "Partitioning problems"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by wildwobby on 2007-03-25
Ok, so windows crashed on this laptop so I thought screw it, im gonna install ubuntu. I burnt a 6.10 live cd of ubuntu on another machine and booted it up onto the laptop. Everything goes well until the partitioning. I got an error saying "error setting disk label" So I posted on the GParted forum and they told me to try the live gparted cd to make the partitions. So i boot  the gparted cd and make the partitions and there is some error creating the filesystem. I think it is still a GParted issue, but how do I fix it!?!?

thanks

---

### Post by notiones on 2007-03-26
If you are installing a fresh OS, then I would download the alternate install CD and boot up with  that. It will be much easier and faster than using the Live CD. I am going to assume partitioning will go easier as well. Failing all else, download the Knoppix Live CD and use qtparted. My fav is old fashioned fdisk, but it has  learning curve.

---

### Post by Sef on 2007-03-26
What are your computer specs?

---

### Post by wildwobby on 2007-03-26
Ok, where can I get the alternate CD image at?

The laptop is an almost 3 yearold Sony Vaio with a Centrino.

---

### Post by tommcd on 2007-03-26
To get the alternate CD go here:
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)
Choose "other installation options" from a mirror near you. Scroll down to find "alternate install CD". Choose "PC (Intelx86) alternate install CD. Also, be sure to burn the iso at a very slow speed.

---

### Post by notiones on 2007-03-26
You can download an installation CD @ [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). This should be all you need and not the "alternate" cd I suggested earlier. I used a fresh iso earlier today and it did everything I needed. Of course the alternate will work too. (see the above post). I would also recommend letting Ubuntu do the partioning for you during the install. Unless of course you are quite comfotable with that sort of thing. Make sure it deletes all of the partitions and starts from scratch too. You are really going to digg Ubuntu.

Good luck! 

Steve

---

### Post by wildwobby on 2007-03-26
Ok,

I tried the alternate CD.

During the partitioning part, I get an input/output error: could not write to disk.

I'm starting to think that it could be the hard-drive that crashes and doesn't work.

What do you think?

---

### Post by wildwobby on 2007-03-27
Gah, this is so frusturating!

---

### Post by notiones on 2007-03-27
At what point during partitioning did you get the error? Was it before anything really got partitioned or was it somewhere in the middle? You haven't changed anything in bios have you?

I would probably wipe out the drive completely and try one more time. My favorite method is to boot up wih a live CD, open a terminal, and type the following: 

# sudo dd if=/dev/zero of=/dev/hda (will overwrite entire disk!)

This assumes your drive is /dev/hda, which it should be. It might take a little while depending on disk size and access time. There are other things you can do, but this is probably the easiest/quickest and least likely to do anything to get you into trouble. I do this anytime I convert a previous Windows client. This will ensure Ubuntu has a nice clean slate to work with. I guess I am leaning toward a corrupt partition table at this point and not a bad drive. Probably as a result of using one of the partition tools. If your drive is ok, this will work and everything else will go smoothly. Since you are basically going to erase the entire drive, I would recommend letting Ubuntu do the partitioning automatically unless you have special needs. In my case, I like to set up separate partitions, but I would wait on this until you know everything is going to work.

It looks like you are doing this after work, so I will try and monitor the forum this evening in case you have any questions.

Steve

---

