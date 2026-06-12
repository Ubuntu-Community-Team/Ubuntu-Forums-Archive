---
title: "How can I access the partitioning tool from the alternate install CD?"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by SolidAndShade on 2011-09-08
Hello,

Can anyone tell me the name of the program that acts as the partitioner on the alternate install CD? I want to run it from the shell and use it to partition logical volumes on RAID arrays, because it appears that it is the only menu-based program capable of doing so - I'd rather use it than use the vgcreate and pvcreate commands. Thanks for any help.

---

### Post by Mark Phelps on 2011-09-08
One tool is the Gnome Partition Editor, know as GParted. It used to be installed by default, but it might not be anymore since the Disk Utility seems to be the default. You should be able to find it in the Software Center.

---

### Post by SolidAndShade on 2011-09-08
I know about GParted and Disk Utility, as well as some curses-based partitioners that are in the repositories. However, nothing I've found can do the job that the partitioner on the alternate install CD does; the other tools can't create LVM volumes. I've searched everywhere and I can't find the name of the partitioning program that's on the alternate install CD or how to run it outside of the install CD. That's what I'm trying to figure out. Thanks.

---

### Post by oldfred on 2011-09-08
The alternative install is not a liveCD. To  make room for extra drivers they remove the liveCD & graphical parts.

You can use command line tools or just download any live CD that has gparted. But if installing with RAID or LVM other tools must be used.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by Hakunka-Matata on 2011-09-08
Are you speaking of mdadm? 
sudo apt-get install mdadm.
Start it from a Terminal

---

### Post by SolidAndShade on 2011-09-08
mdadm is a plain command line tool, not the curses tool used on the alternate install CD. On the alternate install CD, there is a curses-based partitioning tool that can create and edit LVM volumes. I haven't been able to figure out what that tool is called and how I can run it from a regular shell.

---

### Post by Hakunka-Matata on 2011-09-08
The question was plain, but I didn't know the name of the tool in the alternate .iso and I hadn't installed via alternate since I didn't know what alternate was!  Alright, i'm about to see what it looks like....

---

### Post by SolidAndShade on 2011-09-08
[IMG]http://1.bp.blogspot.com/_uF5DvOBRjKw/S-ETM4H2v2I/AAAAAAAABOk/AuEK8zGSH1s/s1600/u104-3.png[/IMG]

This is what the partition tool on the alternate install CD looks like. If you can find the name of the program, I'd really appreciate it.

---

### Post by Teh_Messiah on 2012-03-06
I have a similar problem and also require the partition a partition editor.
I have a silicon image SIL3114 raid adaptor which has made a raid5 array but gparted doesnt see the array, it only sees the 4 individual HDDs.
I dont want to load up the processor with mdadm, I want to use the raid card to do the processing.
When I installed xubuntu 10.04 from the livecd yesterday it recognised the array but after install it didn't.
I should have done the partitioning manually during install and I could have done it then however I assumed I could have done it after install and now discovered that I cant!
Please help?

---

