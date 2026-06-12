---
title: "Swap partition"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Smush on 2008-01-20
Hi I was told in partition magic to create a swap partition for linux of no more than 500MB but when I was reading the Ubuntu howto on dual booting it said the swap should be same as your amount of ram. So in the partition editor (on the installation wizard from live CD) I have tried changing it but it will only let me decrease not increase:confused:

---

### Post by torgrot on 2008-01-20
Is there any free space left to increase it?  I wouldn't worry to much about swap space, it really all depends on how much ram you have.  I don't think I have ever seen mine above 20MB and I have 1 GB of ram.

torgrot

---

### Post by Pumalite on 2008-01-20
The size of /swap is only important in laptop because of the issue of hibernating.

---

### Post by Smush on 2008-01-20
Yeah There plenty of free space... well i have assigned all the free space when I set up windows so if anything went wrong I still had a partition with all my files on so because I have assigned it a drive letter does that make it used?

Also I have 4527MB of unsuable space it says is that OK?

And I have 2GB of ram should I free some space that I had assigned to a drive letter to store my data on (not Windows files)

EDIT: But what if i wanted to hibernate my PC?

---

### Post by Pumalite on 2008-01-20
If you have a laptop and you wanted hibernation, then /swap should be equal to RAM.

---

### Post by Smush on 2008-01-20
Ok I want to put ubuntu on the 50Gb partition I made for it but when I tick manual and click next, select the partition and click next again I get the message "No root file system is defined, please correct this from the partitioning menu" :confused:

---

### Post by Pumalite on 2008-01-20
You have to use the button 'Edit Partition' and in the Window that opens assign 15000 and use '/' as mount point.

---

### Post by Smush on 2008-01-20
15000? 15GB? was going to do 50 so I can have the OS on it and my work I do on that OS

---

### Post by Pumalite on 2008-01-20
15000 is around 12 GB

---

### Post by Smush on 2008-01-20
oh OK I remember 1024MB in a Gb right? but do i only need to define space I need for the OS or also the space I want for personal files etc?

---

### Post by Pumalite on 2008-01-20
I would make /swap next, mount point 'swap', and the rest for '/home', mount point '/home'

---

### Post by Smush on 2008-01-20
Sorry you have lost me here I am new to this whole process

---

### Post by Pumalite on 2008-01-20
After you make your first partition (inside your space), you go back and do the next: /swap and then you go back and do /home. Your space is left with 3 logical partitions: '/', /swap, and /home. Then you proceed to install.

---

### Post by Smush on 2008-01-20
[http://www.picoodle.com/view.php?img=/4/1/20/f_Screenshotm_802ef4f.png&srv=img34](http://www.picoodle.com/view.php?img=/4/1/20/f_Screenshotm_802ef4f.png&srv=img34)

What do you mean by your space? In the screen shot above "/dev/sda3" is the partition I created in Windows with partition magic can I not put it on that?

Because when I right click the white area and click new partition table it says other partitions will be deleted

---

### Post by Pumalite on 2008-01-20
That partition has to be divided in the three partitions I mentioned.

---

### Post by Pumalite on 2008-01-20
Google: psychocats and when there, look for 'partitioning' (sorry I'm at my Apple laptop; cannot give you the link)

---

### Post by Smush on 2008-01-20
so this?
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Also why is my firefox out of proportion on my screen like the close button is almost off the screen? As is the button on toolbar to restart, switch off, lock etc.

And finally I just read an article on which Linux distro suites which needs. But my question here is can I only get the Beryl effects (desktop cube, minimize effect etc) with Ubuntu?

---

