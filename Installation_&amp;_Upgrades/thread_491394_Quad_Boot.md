---
title: "Quad Boot"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by Lamez on 2007-07-03
I want to setup a quad (4)  boot. I have 4 OS's I would like to install on two hard dirves. 

1.Western Digital 40Gb - Slave
2.Maxtor 300Gb - Master

Here are my OS's

1.Windows XP
2.Windows 98 SE
3.Ubuntu 7.04
4.Mandrake 2007 Spring

I want to know what is the best way to install these. 

I know the first operating system I would install would be XP. Then would I install 98SE? 

Now I am really lost on how I would do the linux OS's.  I love mandrake just because it has a great installer and a graphics based grub. So would I do this one last, so it would overright ubuntu's grub?

Also I would like to have the windows OS's on one harddrive, since 98 does not take up a lot of space.

Please help, thanks guys.

---

### Post by Jacemg on 2007-07-03
It'd be a little tricky I think you'd have to do:
XP
Ubuntu (with grub loader)
98SE
Reinstall grub loader
Mandrake 2007
Reinstall grub loader

---

### Post by dabl on 2007-07-03
Knowing what I know now (versus 6 months ago), I'd do the following:

1. Study up on partitioning here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

2. Download and burn the GParted Live CD ISO from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

3. Use the GParted Live CD to partition my disks according to plan.

4. Install Win XP on the master IDE, in the designated partition.

5. Install Ubuntu in its 3 designated partitions (/, /home, and /{swap}), and allow Grub to go to it's favorite MBR, where XP boots.

6. Install Mandrake in its 3 designated partitions ( " " " " ), and allow it to modify Grub and the boot menu.

7. On one of my Linux systems, install VMWare Player 2.0 and install a Win 98 virtual machine to do whatever you need Win 98 for.  Here's some guidance, probably more oriented to Win XP:

[http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

Two cents' worth ....   :popcorn:

---

### Post by Shazaam on 2007-07-03
Yes Mandriva (or any distro) will overwrite grub if you let it. I would install Ubuntu as your last linux distro. I have found that it sets up grub better during install.

XP first (will hide Win98, do as dabl said and run 98 in a virtual machine on XP) on the 40 gig (unless you have a lot of programs/videos/music to install)
Partition the 300gig with an extended partition first (you can have more than 4 partitions this way), follow dabl's instructions for partitioning but install Mandriva first then Ubuntu. If you do it right you will have TONS of room to install other distros to play with.

---

### Post by Lamez on 2007-07-03
Alright I think I have gotten it down. I want to install mandrake last so it will overright ubuntu's boot loader, I love mandrakes boot loader, and I love the fact that you can cuztomize it.


Would it be eaiser to install 98 first, because xp will detect it, but 98 will just add a new MBR?

Also, when I setup ubuntu, do I just let it take up the whole disk, then let mandrake resize it? 

Do I let them share swap? Do I put them on the same boot partiton? Do I have to make a /home partiton?

---

### Post by Pumalite on 2007-07-03
Have you read the links that dabl gave you?. Are you willing to follow his recommendations?

---

