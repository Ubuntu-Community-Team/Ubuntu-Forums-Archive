---
title: "Reformat and partition"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Palu on 2008-04-19
I'd like to try a few distributions while waiting for Hardy. Each time I'd like to completely reformat and maybe delete entire partitions and make new ones of different sizes / for different uses. In this way I'm hoping to get more familiar with this sort of thing. My computer currently has Vista--though I might be doing these things on an XP computer too.

**Please point out things that I won't necessarily need to know because they're covered by the GUI based setup.** (Though I know I eventually should learn as much in the terminal as possible.)

My final goal will be Hardy Heron with the following partitions:
[LIST=1]
[*]4 GB as a swap partition (I hear it's more efficient than a swap file)
[*]The main partition (I think there will be 110ish GB in that). I might mean home partition (see next item).
[*]Should the root have a tiny partition separate from the home partition? (I'm more repeating roughly what I heard someone say and I'm not entirely sure what I mean)
[/LIST]

[LIST=1]
[*]How do I reformat across ALL partitions? I want it to delete my partition definitions too. It will make me feel more distanced from my Windows days in a symbolic sort of way.
[*]Once I make separate partitions, how does the kernel know which I wanted to be my swap, which my home, etc, etc?
[*]If I have a home partition, can I wipe the root partition, install a different distro, and have it use that home partition?
[*]If I install other distros without deleting Ubuntu, can I generally add them to my root partition and boot manager and have them use (hopefully through a GUI installation dialog) ?
[/LIST]

I have found the following functions and think they might be involved in the things I want to do:
[LIST=1]
[*]mkfs: Does this just format within a partition, leaving the partition information intact?
[*]fdisk: Does this display something like /dev/hda to represent each of my devices? Or is it a way to format FAT32 only? Or is it both information (using -l as a parameter?) AND a tool (to do the actual reformatting)? I'm confused. :)
[*]cfdisk
[/LIST]

Should all my partitions be NFS (the Linux default(?))? I don't need a swap with windows because other people on my network will have a fileshare server (once I set one up) where I'm hoping to have a FAT32 partition (20 GB probably) and also a music server on the main part (woot!). I think I'll use Ubuntu Server Edition for all that, but that might be out of the scope of my current questions unless you have a thought or two that might relate to other parts of this.

What's a really good Ubuntu (or general) terminal command reference like the man pages but a little more user friendly for people who are decently new? :popcorn: I especially have trouble figuring out how parameters work when looking at man pages. I understand parameters as a concept and from when I use commands in a DOS setting (when I worked with DOS I just learned from my father and memorized) or windows setting using the "Run" dialog, but not from reading Linux MAN pages. :(

**Important Edit: By NFS, I meant ext3. I knew what NTFS was. Not sure how I confused ext3 with the letters NFS. Thanks!**

---

### Post by fsmithred on 2008-04-20
1. That's an awful lot of swap. Unless you have a notebook that needs 4G to hibernate, I can't think of a reason for that much. 512MG - 1G is plenty for most people.

2,3 - 8-10G for / is comfortable. Use the big space for /home.


1. When you get to the partitioning part in the installer, go to manual partitoning, and you can select which partitions to delete, and then start over again. Be advised that if you delete ALL your partitions, your distance from windows will be more than symbolic. Say goodbye to Vista.

2. Information about where partitions get mounted is in /etc/fstab. You shouldn't have to touch that file.

3. Yes, you can keep your /home partition across installs, as long as you remember not to let the installer format that partition. 

4. If you're going to have multiple installations, I'd recommend giving each of the additional ones their own partition for everything except swap, which can be shared. Different distros might want to do different things with some of the hidden files and directories in your home. That could mess with your settings. 

The installer will make entries in the grub/menu.lst for all the operating systems on your computer, so you'll still be able to boot into them. 


1 - mkfs makes a filesystem inside a partition. 

2, 3 - fdisk is for making, deleting, or listing the partitions on a drive. cfdisk is friendlier, but does the same thing.

You shouldn't have to use  these if you're doing a basic install from cd.


NFS is a service for sharing files between computers. You probably want to go with ext3 for your partitions. Why do you want a FAT32 partition on your server? You don't need that to share files with windows on other computers. Your server software will do that.


[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://linux-newbie.sunsite.dk/](http://linux-newbie.sunsite.dk/)
[http://tldp.org/](http://tldp.org/)

---

### Post by Palu on 2008-04-20
I guess all the times I said NFS I meant ext3. :)

My computer is a desktop and I could actually live without ever hibernating at all. I thought the swap was like a Windows pagefile (which I might not understand fully either, I suppose) and is the virtual memory created when you run out of system memory. I had thought people recommended 150% to 200% the size of your RAM being reserved on your hard drive for virtual memory. My machine has 2 GB of system memory and I tend to open a billion windows of everything over time while I work...

Thanks for the server comment. I think learning how to set that up will be beyond the scope of this thread. I'm sure I have a lot to learn about networking in Linux before I poke at that.

From my original post.
> Once I make separate partitions, how does the kernel know which I wanted to be my swap, which my home, etc, etc?
Sorry if I missed that, but I think I still don't know this. Will this be part of the installer? Sorry. I guess I could just do this, but you're really helping me be more comfortable with the unknown by explaining all this ahead of time. :popcorn:

---

### Post by tommcd on 2008-04-20
You only need 1 swap partition. All distros can share the swap.
You only need 1 /home. All distros can share /home. One caveat: Make each distro's user name slightly different. Otherwise, the hidden .config files that are stored in home might confilict if they all have the same user name. I create a separate /data partition for my stuff to avoid that. Each distro's  /home, and all it's .config files, are stored in each distro's root partition. To do this just create a /data (or call it whatever you want) partition instead of /home, but that is up to you.
Vista has it's own partitioning tool. It may be good to use that to shrink Vista to make room for linux:
[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)
You can then use Ubuntu to reformat the newly created free space to ext3 for Ubuntu.
10GB for each linux root partition is plenty.
EDIT: For basic terminal commands, this is what got me started:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
Practice, don't just read, the stuff they discuss there.

---

### Post by fsmithred on 2008-04-20
The rule that you should have twice as much swap as ram makes sense if you only have a small amount of memory. You're right that swap gets used when memory gets full, but with the large amounts of memory in new computers, swap doesn't get used much, and some people run without any swap partition..

Once again, the kernel looks at /etc/fstab to mount your partitions in the right places. You might want to manually edit this after you have a couple of distros installed, but you really don't need to worry about that now. This file will be created during the installation, based on what you tell the installer about how you want the drive partitioned.

If you're going to install linux on the same drive as windows, then keep reading before you install linux, so you don't screw up your windows. If you have a spare computer that can be linux-only, then make that your safe playground, and dive right in.

---

