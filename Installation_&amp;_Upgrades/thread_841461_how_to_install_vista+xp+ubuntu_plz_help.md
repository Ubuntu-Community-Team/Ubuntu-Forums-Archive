---
title: "how to install vista+xp+ubuntu plz help"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by rob89ert on 2008-06-26
hello guys I'm quite  new to linux but i know xp and vista well. i would like to know if you can install vista, xp and ubuntu on the same computer, and be able chose what one to boot from. at the moment i have a 500gb hard drive and ubuntu install on all of it. thanks for any replies!

---

### Post by niyonk on 2008-06-26
Hi..take a look at [this]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

From my own experience, i did install xp first then vista then Ubuntu.
Hope it helps.
Let us know how it goes :popcorn:

::Forgot to mention that i am using the default vista bootloader, and I use a program called Easybcd to add xp and Ubuntu. Cheers!!:: :biggrin:

---

### Post by Nopposan on 2008-06-26
Well, it looks like it's possible to do with grub.  Is there an OS already installed on your machine?  What is it?  Do you have the install disks for both Windows versions that you want to install?

Here's a link to a site that purportedly teaches us how to install four popular operating systems on one x86 machine.
[http://mrvnposts.blogspot.com/2007/02/quad-booting-osx86-xp-vista-linux-on.html]("http://mrvnposts.blogspot.com/2007/02/quad-booting-osx86-xp-vista-linux-on.html")

Wow, now that's really something; I've never done this though.  I have just Linux and Windows XP installed on this box.  And although I have a dual boot system, I prefer virtualization to run windows in a little X-window only when I absolutely have to.

What kind of processor are you using?  How big is your hard drive?

'Looking forward to helping you if I can.

Cheers.

---

### Post by Nopposan on 2008-06-26
P.S.  Usually, if you have the complete install disks for the OS that's already installed, then I'd recommend a complete erasure of the hard drive as a second step.  The first step is to back up your important data to an external source, of course.

To accomplish these things, I can offer advice right away.

---

### Post by rob89ert on 2008-06-26
thanks for replies, I have all the OS CD's/Dvds. i think i am going to try niyonk way of doing install xp, vista and then unbuntu. the question is how do i remove ubuntu to start doing it

---

### Post by Euphorion on 2008-06-26
Hallo

I have done the same recently. I started with a newly purchased Laptop with Vista, spread over drive C: with a Recovery Partition. This is how I installed Ubuntu.

I first of all made a GParted live CD. Google Gparted and download the Live CD image and burn a CD with a burner of your choice e.g. Nero.

Then check to see if your Bios is set to boot from CD/DVD if not change accordingly. Boot from the GParted CD.  When GParted comes up (after selecting language and key board) for US Englisch and Keyboard just hit enter. This Partition manager is better than the one in Vista for it can compress fragmented NTFS Drives better than vista, allows for a greater reduction.

In Gparted reduce your Windows Partitition to make Space for Ubuntu, select the space you require, I reserved 51 GB.

After this has been done succesfully, reboot with the Ubuntu installation CD. Answer all Questions up until partitioning. Then select Manual Partition. Select the free space created above and create an EXT3 partition. When allocating the space, dont forget to leave some space for the swap partition (in my case 1 GB). Then create the swap partition using the rest of the free space. The Partitioning can commence, when asked where to place the boot loader Grub, do not select the MBR of the windows partition, put it in the Ubuntu partition. This is a somewhat hidden option during the Ubuntu install proceedure. See the links below for an illustrated guide. (References to XP but also valid for Vista).

Then carry out the Ubuntu install. After the install, we now need to configure the Vista bootmanager. In vista download EasyBCD and install it. Run EasyBCD and use setup to add the Ubunut Grub BootLoader and save the configuration. When restarting the system the Vista Bootmanager will appear with Vista and Ubuntu.

Naturally you can use the same proceedure to partition your Disk for a multitude of OS's.

Also see the following links:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

In the above links you will find further links to all aspects of installing Ubuntu with and without Windows. Is very educational reading.

Good Luck

---

### Post by niyonk on 2008-06-26
> **rob89ert said:**
> thanks for replies, I have all the OS CD's/Dvds. i think i am going to try niyonk way of doing install xp, vista and then unbuntu. the question is how do i remove ubuntu to start doing it

You might just need to free up some space using gparted (from add/remove programs)
If you have no idea of how it works, then dont stress it :) (putting ubuntu back is just 25 minutes away lol)
Open up XP installation and delete the partition, you will have unallocated space.
Then create a new partition like 100GB for XP. Leave the rest intact (you will do it later after XP installation in disk management) :biggrin:

Good luck!

---

### Post by rob89ert on 2008-06-26
thanks alot of all the replies trying it now!

---

### Post by Perkins on 2008-06-26
Probably what you really want is 7 partitions.  One for each operating system, one for each OS's swap space, and one for storing the data you want to be able to read from any one of them.  You might be able to combine the swap partitions for XP and Vista, but I've never tested that, so I can't say for sure.  I know you don't *need* to have a separate swap partition with windows, but it seriously reduces file fragmentation, and guarantees that your swap file won't be one of the fragmented ones, which can dramatically improve system performance.  Of course, twice nothing is still nothing, so don't expect miracles.

I haven't tried it with XP and Vista, but previous versions like XP and 2000 or 2000 and 95 have been pretty good about living with each other if you install them into separate partitions.  (95, 98, 3.1 and 3.11 can actually all be installed onto the same partition and switched between without rebooting.  Not that any of you care. ;) )  They should even detect each other automatically and configure the bootloader appropriately.

Ubuntu's installer has never given me any trouble about detecting windows and incorporating its bootloader entries into grub.  So as long as you install it last it should just work.  Gparted is probably the best program for partitioning your disk if you're new to this, though there is no reason why you couldn't just use the partitioner on the XP or Vista install CDs.  It's more than capable if you read carefully, just don't bother formatting the partitions for Ubuntu since they need to be EXT3 and linux swap, and the windows partitioner won't do that, so you'd have to reformat them anyway when you install Ubuntu.  If I recall correctly from the last time I did this, XP requires about 2.5GB of space for its system files, and Vista takes something like 6, depending on which version.  Personally I like to put the OS on a small partition and have a larger one for storing my user data.  Again, it reduces fragmentation and makes data recovery in the case of a crash or drive failure considerably easier.  Also, lots of Windows viruses are written by script-kiddies with not real programming skill, so putting your files in a non-standard place prevents some of them from messing with your system quite so much.

---

### Post by Nopposan on 2008-06-26
Once I had some problems reinstalling Ubuntu from the same live installer CD.      I tried twice and both times wound up with problems related to the first install being somehow misconfigured.  Erasing the hard drive solved the problem.  'Wish I could remember the details to tell you, but since then I've developed the habit of completely erasing my hard drive before a new installation from CD.

It takes a while for the process to complete, but it's so easy and I think it's fun too; It gives me a kick 'cause I keep hearing stories on TV and radio about how difficult it is to truly erase a hard drive.  It's just so easy . . .
```
# Shred -v /dev/sda
```

That's /dev/hd0, I think, if you have an IDE drive.

You can add an option to only wipe the disk once or twice and that will take less time.  I think that option is just ```
Shred -v -n 2 /dev/sda
```

If you use the default it will overwrite your hard drive 25 times with random data, then just zeroes, then random, then just one's.  It seems to me that even people with very expensive forensics tools would have a hard time recovering any data from a drive that was wiped this way.

Have fun.

---

### Post by flytripper on 2008-06-26
why not install your fave most used os as a base and virtualise the rest? it saves a lot of messing about if you ask me.
I am using Ubuntu as my main (host ) and booting xp in virtualbox to convert my vid files for my xbox.. works well too!!

---

### Post by Nopposan on 2008-06-27
I'm going to try virtualbox.  'Trouble is that it shows modules for linux-image-2.6.22-14-generic when I just upgraded to linux-image-2.6.22-15.  I wonder what will work and what won't.

---

