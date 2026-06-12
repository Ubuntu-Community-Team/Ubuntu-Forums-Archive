---
title: "Install on software RAID 5"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Eladon on 2007-02-28
OK, I have spent 3 hours just googling, and searching the wiki & forums with no avail.  I have found copious information specific to fakeraid, other distros, or simple raid 1, none of which was applicable.

All I want to know is the proper way to go about installing **everything** to a pure software Raid 5 (ho hardware raid at all, i.e. no fakeraid & no windows partition, etc).  I have 3 SCSI hard drives, and that's it.

I have already tried a million combinations of things using the alternate 6.10 CD, and I could go into a bunch of detail of what I have done so far, but I'm hoping that there is a guide somewhere that I have missed that someone can point me to, rather than reinvent the wheel.

---

### Post by modulok on 2007-02-28
[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)
[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)
[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

those are the links I used to make a software raid5 storage array, I bet you would have to boot using the ALT cd and manually create the raid 5 first, then install on the partitions you make.

good luck, let me know if you are successful.

---

### Post by Yoooder on 2007-02-28
I presume you're aware of this.  But just to reiterate, it's generally a bad idea to put any OS straight into a RAID array, since any problems with your array stand a good chance of making a recovery a huge chore.

I personally use an old 10GB for my root partition and OS, then map my /var, /home, and other main folders to my RAID array.  I'm also running LVM with my RAID array as the main physical volume, so I have 2 logical layers to worry about (making running straight from the array an even worse idea).

Good luck though :)

---

### Post by Yoooder on 2007-02-28
...One other note/idea.  The Ubuntu LiveCD is a living distro that you can install packages too.  You might be able to setup your raid array and install directly to it---however getting it to boot correctly would be tricky.

---

### Post by vividvew on 2007-02-28
I am inclined to agree w/ Yoooder. Booting to a software raid 5 is not the simplest thing to setup. I have gotten it to work in Gentoo but nowhere else. You will most likely need to set up raid and LVM and recovery could be hard, for a software problem like kernel or boot issues, unless you have a live CD with a kernel that supports raid5 LVM and will auto start mdadm and create the dev files for you.

Yoooders method is what I use and just backup my by boot and root partitions via tar to the raid so I can restore them from a live CD.

---

