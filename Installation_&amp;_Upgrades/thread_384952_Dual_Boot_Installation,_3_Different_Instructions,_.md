---
title: "Dual Boot Installation, 3 Different Instructions, Which is Correct?"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by w1llywonka on 2007-03-15
Dual Boot Installation, 3 Different Instructions, Which is Correct?

I am going to setup my PC to dual boot Windows XP and Ubuntu, Windows XP is already installed.  According to various websites I have found after installing Ubuntu 3 possibles things will happen:

1. Ubuntu will automatically recognize my Windows installation, I will be given a choice of which OS to boot immediately and all will be fine: [http://doc.ubuntu.com/ubuntu/switching/C/dualboot-procedure.html](http://doc.ubuntu.com/ubuntu/switching/C/dualboot-procedure.html)
2. Ubuntu will load up but will not recognize my Windows XP installation and I will have to go into Ubuntu and edit GRUB: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
3. Nothing  will load up and I will get an error message saying no operating system detected and I will need the system restore cd to fix it: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Which one of these is correct?  I really don't want any surprises.

Keeping in mind that I already have an installation of Windows XP on my PC, and will be using Partition Magic to create a separate partition beforehand on which to put Ubuntu which of these scenarios can I expect?  Also I have taken the usual precautions of backing up files etc, but still rely on Windows quite a bit.

---

### Post by chewearn on 2007-03-15
> **w1llywonka said:**
> Keeping in mind that I already have an installation of Windows XP on my PC, and will be using Partition Magic to create a separate partition beforehand on which to put Ubuntu which of these scenarios can I expect?  Also I have taken the usual precautions of backing up files etc, but still rely on Windows quite a bit.

Since you have Partition Magic, use it to resize your WinXP to make room for ubuntu; but do not put anything in the freed space.  This space should be unallocated (no partition in it, and unformatted).  Then, during ubuntu setup, you can use the option where the installer automatically create ext3 and swap on the freed space (option with something like "largest continuous free space").

---

### Post by w1llywonka on 2007-03-15
Right... Yes that is what I intend to do, but my question is more what will happen next.  Will GRUB automatically recognize both Windows and Ubuntu in such a scenario?  Or will I need to tweak things before I can boot into both Ubuntu and Windows.

---

### Post by chewearn on 2007-03-15
The installer should should automatically recognize windows and ubuntu.  I have not done many dual boot installation, but the few times I did, it was smooth sailing (no tweaking needed).

If you are worried because of the people coming into this forum with problems; then you should realized you are only seeing people with problems.  Others who have similar dual boot installation will probably not be posting here to say they are successful.

Of course, there is the 0.1% chance... don't sue me if you failed :mrgreen:

---

### Post by Herman on 2007-03-15
I agree with AstalaVista,
> If you are worried because of the people coming into this forum with problems; then you should realized you are only seeing people with problems. Others who have similar dual boot installation will probably not be posting here to say they are successful. Lately an average of over 700 per day have been joining Ubuntu Web Forums, according to my records from the forum counter at the bottom of the front page. Even if that number of people only install one copy of Ubuntu each, that's a lot of installing going on. For that number of installations, I don't think the number of problems per day is very high at all.
Remember, certain other operating systems have tech support too, and I am sure that those people are far busier than we are here.  

If you are really worried about bootloader problems get yourself a [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").

I think aysiu's website is the best for most people to use nowadays, I recommend [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php"). (by aysiu).

I do not recommend Partition Magic though, you should do your disk partitioning with the Ubuntu installer's partitioner, GParted.

Regards, Herman :)

---

### Post by w1llywonka on 2007-03-15
Thanks for the advice.  One more question.  If you don't reccomend to use partition magic, since I have 250gb drive it is already partitioned into 4.  My Windows partition is 20gb and I don't want to shrink it.  Will GParted, allow me to take space from my 3rd and 4th partitions and combine these into a 5th partition for Ubuntu?

The reason I would prefer to use Partition Magic is that it remaps drive letter references.  If GParted creates a new parition it could potentially move all my other partitions up a drive letter and then kill all my program links etc.

---

### Post by Herman on 2007-03-16
Hello w1llywonka,
You asked,> since I have 250gb drive it is already partitioned into 4. My Windows partition is 20gb and I don't want to shrink it. Will GParted, allow me to take space from my 3rd and 4th partitions and combine these into a 5th partition for Ubuntu?
What are your partition numbers? Have you got four primary partitions already, (numbers 1,2,3 and 4?). If that's what you mean then you can't create any more partitions unless you delete one first and create an 'extended' partition first. 
I'm not sure what you mean. I can give better help if I can have the output from sudo fdisk -lu, (from a Live CD), ```
sudo fdisk -lu
```I don't know about your 'partition letters'. GParted will normally retain our partition numbers unless we force it change them that by doing something like copying a primary partition and pasting it inside and extended partition or the like. Then it would have no choice. 

Regards, Herman :)

---

### Post by ravis_31 on 2007-03-16
Hi my scenario is something similar.My Acer laptop has windows xp installed on c: (45G,primary),I had repartitioned my other drive D: (45G,logical) into two drives (D:35G,logical and F: 10G,primary)i tried installing ubuntu 6.10 with the alternate cd(due to ati x700 issues)on F:.When i get to the partitioning part,i use F as the ext3 drive and the rest of the 1G becomes unusable.
I'd used Partition magic to repartition D:.
I have the following options

1)Merge F: into D: as it was previously (logical) and try installing,will i be able to install on a logical drive
2)Delete the D: (logical) merge it into C: then while installing use 20 GB for 2 ext3 drives and 1GB for swap space
3)If there's an easier way please let me know

thanx
travis

---

### Post by chewearn on 2007-03-16
> **ravis_31 said:**
> 1)Merge F: into D: as it was previously (logical) and try installing,will i be able to install on a logical drive
2)Delete the D: (logical) merge it into C: then while installing use 20 GB for 2 ext3 drives and 1GB for swap space
3)If there's an easier way please let me know

Either way looks the same.  Only difference is that in option 1, you get a smaller C: For option 1, if you delete D, then resize F, you will not end up with a extended partition (though, I think ubuntu is still ok installed in extended).

---

### Post by ravis_31 on 2007-03-16
is it possible to install in the existing logical D:.If yes then i don't need to go through the steps.

travis

---

### Post by Herman on 2007-03-16
Hello ravis_31,
I can tell you that Linux is able to be installed just as happily in logical partitions as primary. It makes no difference at all.

Regards, Herman :)

---

### Post by ravis_31 on 2007-03-16
thanx man,i've successfully installed ubuntu YAY!!!!
now i have to deal with the ati configurations.After the orange progress bar the screen goes blank.How do i go into the command prompt?

travis

---

### Post by ravis_31 on 2007-03-16
i got into the command prompt edited the xorg.conf to vesa and it returned some error.i changed it to radeon and i could hear the startup music but still the screen in blank.
how do i solve this now?

travis

---

### Post by w1llywonka on 2007-03-16
All solved and installed.  Basically I forgot about the whole only 4 primary partition thing, so I put all data from 4 onto 3, deleted 4, then tried to merge 2&3 but got errors, so I converted 3 from primary to logical and was all set to go.  

Ubuntu installed painlessly and Grub automatically recognized my Windows installation.

Now I am trying to get Beryl running, but I am getting an API mismatch error after installing Nvidia drivers.  But I suppose that is another post....

---

### Post by Herman on 2007-03-17
> i got into the command prompt edited the xorg.conf to vesa and it returned some error.i changed it to radeon and i could hear the startup music but still the screen in blank.
how do i solve this now?Hello ravis_31,
I would probably not bother to try to edit my xorg.conf file by hand but let it be done automatically for me with '[sudo dpkg-reconfigure xerver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")' and  I find that works for me every time. I hope it will work as well for you. I have two machines here that each have ATI Radeon 9200 video cards, and they work well enough for me in Ubuntu. I haven't really tried to tweak them to their maximum, I'm content with the defaults.
That link should be enough to get you started, I hope.

Regards, Herman :)

---

### Post by Herman on 2007-03-17
Hello w1llywonka,
Thanks for the feedback, I wonder if the same link, '[sudo dpkg-reconfigure xerver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")' would be any help to you as well? 
I recommend making a backup of your /etc/X11/xorg.conf file first.
That web page was written mainly for ordinary users, it's possible that you are doing something quite advanced, so I'm not sure if I'm really being helpful here or not. I guess you'll see for yourself and make up your own mind what is best for you.

Regards, Herman :)

---

