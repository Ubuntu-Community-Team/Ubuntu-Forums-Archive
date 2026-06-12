---
title: "Mounting a partition as home"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by MaXqUE on 2007-02-10
The Ubuntu install when without a hitch. Great installer! 

What I now have is Ubuntu on one partition with a second swap partition. My standard setup is to have one other partition mounted as home so I partitioned my hard drive before I ran the installer --  In my case, my hard drive has three partitions:

/dev/hda1 is the root partition 
/dev/hda2 is swap
/dev/hda3 is mounted as /media


What I need to so is edit /etc/fstab so that /dev/hda3 mounts as home. So far I know how to do this. The tricky part is moving my user directory to what is now  /media without damaging what I've already configured.

Which incantation or variant on cp should I use to accomplish this? I would also like to expunge (shred -uv <directory>) this old directory since it will only take up space which wil be unaccessible after /hda3 is mounted as /home.

Help anyone?

cheeers
MaXqUE

---

### Post by housam on 2007-02-10
Read [this guide. ]("http://psychocats.net/ubuntu/separatehome")

---

### Post by MaXqUE on 2007-02-11
Thanks for the pointer, the instructions worked almost perfectly. The only things that didn't transfer were preferences like desktop configurations and Firefox bookmakrks. However it was no problem to go into hte backup I made and pull the bookmarks out.

However, one thing I've noticed in general about many hints and guides is that they do not explain the logic or the what the commands they are using do. I've been using Linux for a long time now but there werre things there that I had not previously run into nor needed to do.

Luckily, I didn't need to use the partitioning tool since the partitions were already made. So I could skip half way down and begin from there

Thanks again.
MaXqUE

---

