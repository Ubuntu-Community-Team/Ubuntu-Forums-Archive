---
title: "where can i get fat32"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by DCDraco on 2006-09-23
o.k. where can download fat32. I know my friend tried gparted and did not work somethig about win XP not accepting it, darn XP.

---

### Post by K.Mandla on 2006-09-23
FAT32 is a file system, not a program to download. Can you explain what you're trying to do? It sounds like you want to repartition your drive for a dual boot. Is that right?

---

### Post by DCDraco on 2006-09-23
ya thats right I want to have a dual boot.

---

### Post by K.Mandla on 2006-09-23
There are some great instructions here. ...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Aside from that, the idea is to free up space on your drive, then shorten the XP partition to make space for Ubuntu. I would suggest GPartEd, but it sounds like you've already tried it.

---

### Post by DCDraco on 2006-09-23
see i alright have the hard drive partitioned 36GB for XP and 56GB for saving data. I want to partition this part and then set up Ubuntu and have about 10GB to share between XP and Ubuntu linux.

---

### Post by K.Mandla on 2006-09-23
You have a couple of options. If you can get your hands on Partition Magic or a similar Windows program, you can set up that 10Gb shared area that way. Otherwise the GPartEd live CD usually works well. 

The last area should be left unpartitioned for the Ubuntu installer. (Or that's the easiest way, anyway.)

Make sure you have defragmented and cleaned up your XP area before you partition off that extra area. It won't shrink that partition if there's still data there.

And remember that repartitioning in XP can take a loooong time.

---

### Post by DCDraco on 2006-09-23
I don't understand about;

Make sure you have defragmented and cleaned up your XP area before you partition off that extra area. 

What i have at the moment is running XP on that 36GB part. It the 56GB part that needs to be partitioned. Do I need to be worried about loosing XP part? I have just downloaded gparted thanx. It is an ios file so what to do with this?

Thanx so much for the help.

---

### Post by K.Mandla on 2006-09-23
So is your XP area already partitioned to 36Gb? Is the 56Gb part completely empty? If so, you're almost ready to build your dual boot.

(No, don't worry about the XP part. It'll be all right.)

The ISO file needs to be burned to create an installation CD. Try [these instructions]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by DCDraco on 2006-09-23
yes that is  right the 56GB is empty at the moment it is set up that it is a second drive to save data on. I can save the data there to memeroy stick because i basically have nothing on there. Then it will be completly empty. It appears in windows as an E: drive with 56GB free space. As well I have already burned the iso of gparted to cd. I will read the site you sent me.

---

### Post by K.Mandla on 2006-09-23
Great! You probably won't need GPartEd after all. If that 56Gb partition is empty, you can boot the Ubuntu alternate CD and get started installing.

When you install, make sure it installs to the second drive. it should detect Windows and set up Grub for a dual boot.

[These]("http://users.bigpond.net.au/hermanzone/p3.htm") are probably the most detailed instructions I've ever seen for a dual boot. [This]("http://www.ubuntuforums.org/showthread.php?t=179902") should give you ideas on how to install to two drives.

---

### Post by DCDraco on 2006-09-23
THank you so much I will let you know what happens hope all goes well we will see. I will do the reading first then give it a go. But one very last question. When I boot to install I get two opptions multi boot and i think boot to cd, which do i do?

---

### Post by K.Mandla on 2006-09-23
If I understand you correctly, I think you want "Install Ubuntu". The other options are to check the CD for defects or to install a server (and a couple of others). I don't think you want a server, so just start with the top option.

Make sure you're not installing from the live (or "desktop") CD. I don't know if installing a dual boot is an option from the live CD.

---

### Post by DCDraco on 2006-09-23
I want to make it clear that i only have one hard drive. I have burned to dvd the Ubuntu 6.06 LTS DVD. Will this do?

---

### Post by K.Mandla on 2006-09-23
Yup. That should work fine.

---

