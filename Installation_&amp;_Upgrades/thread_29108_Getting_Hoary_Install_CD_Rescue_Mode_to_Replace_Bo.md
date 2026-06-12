---
title: "Getting Hoary Install CD Rescue Mode to Replace Boot Partition"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by Levander on 2005-04-23
In the hoary release notes, it says that the [Hoary Installation CD](http://www.ubuntulinux.org/support/ReleaseNotes504/) now supports a rescue mode.  To find it on that page, search down for "rescue mode", it's down a ways. I've been booting and looking for this rescue mode.

So, first question: How do I get into this rescue mode?

I'm having to resize my boot partition (where the kernels are stored) to make it bigger using parted.  The reason I'm trying to secure a rescue disc is in case I hose the partition during resizing.  

If I do mess the partition up, I see in the hoary install cd set-up process, one of the options is "partition disks" and another is "install grub".  Can I skip all the other steps in the installation process and just do these two to try to get back my boot kernel?

So, that's a second question, how good a plan is that to recreate the boot kernel if I mess it up?

---

### Post by nad on 2005-04-23
The /boot partition is just a filesystem. Copy it elswhere for safekeeping. ' cp -dpR /boot/* /mnt/someplace/boot/. '

What you do need to copy is your master boot record as your current partition table is here. ' dd bs=512 count=1 if=/dev/hda of=hda.mbr '. This command will copy the first 512 bytes of your first hard drive to the file hda.mbr. You should also have a copy of your partition table. ' parted /dev/hda print > parted.txt ' This is the Holy Grail of restoring your previous settings.

To restore your mbr, reverse the input file (if=) and the output file (of=) of the dd command. This is always a nerve wracking procedure as you never know if 512 bytes is going to overwrite something. Double check your command string before issuing. If you are dual booting with another os, be forewarned YMMV.

Don't forget that GRUB can be your friend. You may need to modify your menu.lst and review your settings in /etc/fstab.

Dan M

---

### Post by Levander on 2005-04-23
Okay, great, that's exactly what I needed to know.

Now, how do I get to the rescue mode of the hoary installation CD in case I've got to use that to boot the system?

I'm just assuming that's the best rescue disk to use because I've got one anyway since I installed hoary from it, and it would be the most compatible theoretically with the rest of my system because it was made by the same people.

---

### Post by nad on 2005-04-23
All linux live cds or floppys for that matter that I know of will supply a terminal interface and the programs mentioned to issue the commands that were referenced. It is simply a matter of knowing your way around. Play around, with caution.
I find it the best way to learn.

I haven't used the hoary install cd this way, but, I imagine that there is a boot parameter to enter single user mode which will give you a single terminal console. Personally I use a knoppix cd, the UBCD (Ultimate Boot CD), damnsmall on a usb pen drive and still occasionally a tom's rtbt floppy for diagnostics and repairs to linux and other operating systems.

Dan M

---

### Post by Levander on 2005-04-23
Ummm, I don't quite need the level of emergency relief you got with all those emergency disks.  In fact, in a few years of using Linux, this is really the first time I've thought I've needed one in case something I do messes up.

Am hoping to just stick with an Ubuntu branded solution - thinking things will be easier that way.  If, I could just figure out how to damn get into the rescue mode.

But, I do appreciate your help.  Especially with how to restore the boot partition.

---

### Post by nad on 2005-04-23
You may need to get the latest download as the hoary install preview disk that I made does not have this feature.
Using the F1 key at the boot prompt brings up a menu of options, Not here, but at the begining of the install one of the first menus gives an option to open a ash shell. Particularly unfriendly and apparently not completed as of this release.

Let me know what you find out.

Dan M

---

### Post by Levander on 2005-04-23
Okay, I do have the fully released, not preview release version of the hoary install CD.  But, if the rescue mode's not complete, would using the Hoary Live CD be a better rescue system?  Maybe I can use that and stay inside the Ubuntu scope of things?

Also, back on this resizing the boot partition, the parted manual says that if I resize a partition, I must reinstall grub's stage2 file:

[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC44](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC44)

Am having an awful time figuring out how to do this.  Anybody gotta a link with instructions?  Or know how to do this?

I'm using ext3, which doesn't have a stage1.5 file, so I assume I do need to reinstall grub's stage2 file.

Been looking through the grub manual now.

---

### Post by nad on 2005-04-23
I'm sorry if I was unclear. The point I was trying to make is that it doesn't matter what distro, or for that matter what operating system, you are using to repair your files and hard drive. As long as these utilities are available and can access your filesystem and hardware you are fine. Your operating system is not running when you do this. And yes, using any live cd will give you more resources to work with.

You will need to update grub as I mentioned in my first post. See this link for an easier to read grub howto with examples:

[http://www.freeos.com/](http://www.freeos.com/)

Search for the Howto link and then the grub howto.

If you would post your new parted configuration, I will try to give you your grub command line.

Dan M

---

### Post by Levander on 2005-04-23
No, I got that.  I realize that there are a variety of rescue disks out there I can use.  But, not only am I just trying to figure out how to get done what I need done this time, I'd like to have some kind of starting point if I ever need to do something similar in the future.  That's why I'd like to use an Ubuntu product.  I'm very happy with the distribution, and just figure if I use something from then, since I'm using a lot of their stuff anyway, it may come in handy again a year or two down the road, since I've already got a little experience using their live CD if I use that, or the hoary installation CD rescue mode if I use that, etc.

I'm looking at the freeos link you sent now to figure out what the hell I gotta do with grub.  I may split that question out into a separate thread since it's not really what I started asking in the title of this thread.  But, I'm going to try to figure it out on that freeos link you sent me.

Thanks a lot for the help!

---

### Post by Levander on 2005-04-23
[QUOTE=nad]
If you would post your new parted configuration, I will try to give you your grub command line.
[/QUOTE]

Okay, I missed this first time I read your post.  Am really kind of hesitant to run parted, without some kind of documentation telling me what I'm supposed to do with grub after I resize.  I'm wondering if what parted's manual is calling "reinstall grub's Stage2 file" is really part of some larger process some people do.  Like just re-installing grub altogether?

I know there's an option in the hoary installation CD to "install grub".  If I can skip all the other steps in the installation process, maybe I could just get the install CD to install it for me?

This is really kind of surprising that it's this hard to find.  I know parted is a common tool, and it seems like most people have to do this with grub after running it.  Just seems like it would be easier to find.

---

### Post by nad on 2005-04-23
You know, I just went back to reread your original post. Why not just delete the older kernels and their associated map and init files. This will free up ~5M each. I think that synaptic will automatically delete these files when you remove the older kernel packages. How often do you boot to an older version? If not, go in and remove them manually.

Dan M

---

### Post by Levander on 2005-04-23
Dan, that would be great!  However, for some odd reason, I decided it was a good idea to only make a 15M /boot partition when I installed Warty.

Under Warty, I updated from ubuntu's 386 kernel to the 686-smp kernel.  Before I upgraded to hoary, I had to figure out how to remove a kernel package, which is a little more complicated than removing a regular package.  There's just a different command with a couple of more command line options.  

So, then when I upgraded to hoary, it installed another kernel.  Which is what I was afraid it was going to do, and is why I figured out how to remove the old kernel.  I have two kernels on my system now and like 507 1-K blocks that aren't used and 0 blocks free according to "df /boot"'s output.  I know the math doesn't add up.  But, "du /boot" says "!K-blocks: 15022, Used: 14515, Available: 0, Use %: 100".  

If I want to use "apt-get update" and "apt-get upgrade", I figure I need to make that /boot partition bigger.  Because, apparently, when they install a new kernel, they don't remove the old one.  This must be in case there's problems installing the new one.  If I don't make this partition bigger, and the next kernel is a little bigger than the last one, I'm screwed somehow.  Notice that this is even if I remove one of the two kernels I have out there now.

---

### Post by Levander on 2005-04-23
Well, due to unforeseen developments during the parted re-partitioning process, I am now the proud owner of a Hoary system with a 1GB /boot partition!  I know, entirely to large, but it works.

I ended up having to copy the old boot partition into another place on the hard drive.  And, what is wierd is that before I had a chance to re-install grub, and after I had modified /etc/fstab to point /boot to the new partition, the system booted fine!  So, I was booted off the old /boot partition, but had the new /boot partition mounted.

The only reason I believe I am currently running the new kernel is because when I boot, I get the grub menu, and on the option that is my normal boot, I hit 'e'.  In the commands listed for that menu option, it says (hd0,1), and my new boot partition is /dev/hda2.

The reason I didn't get a chance to re-install grub when I thought I could is because grub is available neither on the Live-CD nor the half-assed "rescue-mode" of the hoary installation CD.  Although, I'm not convinced I found the rescue mode.  I didn't see anything about opening an ash shell.  What I did see, is that if you choose "Go Back" during any step of the installation process, you get to a menu that lists all the installation steps.  Towards the bottom there is an option to "Execute a shell".

Don't know why they don't have grub on the Live-CD, I've seen people talk about using that as a rescue disk several times in my searching today.

Also, I used that "Go Back" feature of the installation CD to install grub.  Was going to do it the manual way, but I've killed enough time on this project.  And, when I went into the grub command line that you can get from just booting your regular ubuntu system, I couldn't get the setup command to work.  It would look like your running, but when you rebooted, everything was the same as it was before.  My guess is that you can't use grub to change the configuration of the disk you're running it from, or that you've booted grub from.  Something like that.

To re-install grub, I used the procedure basically documented here:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by nad on 2005-04-23
LOL

It's great that everything worked out okay. Good catch on that ubuntu grub howto.

Grub is a little hard to get your head around. Especially if you've never used it before. It happens to be a shell of its' own with arcane commands. It can be run from any location if you know the syntax. (hd0,1) Is the correct address for your /boot partition. I'm glad you learned how to edit the boot parameters also. You are on your way wizardness.

Dan M

---

### Post by Levander on 2005-04-23
[QUOTE=nad]You are on your way wizardness.[/QUOTE]

God I hope not, that was nerve-wracking.

But, really, maybe I'm just spoiled by this whole Ubuntu thing. Used to have adventures in Linux like that all the time...

---

