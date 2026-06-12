---
title: "Trouble with GRUB"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by aSquirtle117 on 2012-10-28
I total hard drive crash a few weeks back and instead of trashing the computer (its old, but its got new RAM, and its not that old) I decided to just get a new hard drive. I've been a windows user all my life but I really like the idea of open source software and Linux based operating systems. I have a good friend who strongly advocated for them. I decided to go with Ubuntu because it seemed to fit my needs the best.

On my fist two attempts to install I ended up with error: file not found and GRUB rescue. After the third install attempt it worked fine. I loved the operating system, I had heard it was good but I really fell in love. I left the computer fairly idle for a few weeks, it isn't the primary household computer and more of an experiment at this point. Then after and update It sent me back to GRUB rescue. I had a friend of mine work on it and he wasn't able to do anything except change the error to just error 2. (whatever that means). I was ready to give debian or red hat a try but I really like Ubuntu so I wanted to try to fix it one more time. 

After some more research I was able to install and run boot-repair from a live disk. Everything seemed to go well as I went through the instructions and I got to the end and rebooted the computer without the live disk. Back to file not found and GRUB rescue. Here is the link boot-repair gave me to post for help [http://paste.ubuntu.com/1312960](http://paste.ubuntu.com/1312960) At the end of boot-rescue it also recommended creating a separate boot partition. I am not confident in my computer abilities enough to create a partition but I am willing to give it a try. What do you think I should do?

---

### Post by oldfred on 2012-10-28
Welcome to the forums.

We seem to be finding the issue with grub & large / (root) partitions. You could add a small /boot partition, but I often suggest smaller / with separate /home or data partitions. 

Since it is just a new install, you can quickly test if a smaller / will work. From liveCD to make sure partitions are not mounted, and you may still have to click on swap and right click swap off as liveCD like to use swap, just shrink the current sda1 or / partition to something less than 100GB. If that works you can reinstall or just move /home or create another partition for data so you still use full drive.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If a new install, it may just be easier to reinstall, but if you want to learn how to copy a folder to a partition.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you want to reinstall you do have to use manual install or Something Else to have the option to add more than the default of / & swap.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

