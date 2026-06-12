---
title: "How to add unpartitioned space to root"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by bargi on 2008-02-13
Hi ,

I have near about 15GB of unpartitioned space in my system and I want it to add to my root directory...........how can I do this............

Please tell me step so that I am able to add it to root and also no data is lost and also settings...........

Thanks

---

### Post by erfahren on 2008-02-13
You can use [GParted](http://gparted.sourceforge.net/) - it's already included in the LiveCD (System > Admin > Partition Editor)

to work with your Ubuntu Partition(s) you'd need to do it from the CD enviroment since you can't work on mounted partitions

to make sure you get good instuctions though - you should post a screenshot of your current partitions in GParted - you can install it though the Synaptic Package Manager - (System > Admin) - search for "gparted". Or in the Terminal (under Apps > Accessories):
```

sudo apt-get install gparted

```

once you have it installed just launch it and take a screenshot (Alt+PrtScrn) and post it here.

---

### Post by bargi on 2008-02-13
Hi ,

I have attached the image........

I want to add /dev/sda8 to my root ..........

thanks

---

### Post by az on 2008-02-13
delete sda6 and sda8, resize sda7 to take up all of the space except for the 1 Gig for swap and then create a swap at the end of the drive.

Don't forget to edit fstab to point to the new swap space.

---

### Post by bargi on 2008-02-14
Hi az,

I have deleted sda8 but not able to delete sda6 of swap...... I have attached the image of gparted .........

The delete option is disable when I right click sda8 ......

How can I delete this swap space and also add the unpartitioned space  to sda7 with no loss of data ??????

Please give me steps to do it ......

Thanks

---

### Post by Partyboi2 on 2008-02-14
Make sure the partitions you are wanting to change are not mounted. So right click on the partition you want to work on and unmount it. Best to use the live cd to work on your partition as they can not be in use while you are working on them.

---

### Post by bargi on 2008-02-14
Thanks for reply !!!!!!

But using live CD will not delete my data from sda7 ????

Is there any harms of using live CD ........... since I have my project installed on linux and I don't want to loose data and its setting (since it took a long time for installation an configuration)..........also when I add unpartitioned  space to sda7 ,will there be loss of settings like environment variables etc............

Please help, since it can be risky............

thanks

---

### Post by Partyboi2 on 2008-02-14
As always suggested backup your files, just in case. With sda6 you will need to right click on it and turn swap off. Then try deleting it. Using the live cd will not delete your data from sda7 unless you delete the partition.

---

