---
title: "replacing pclos2007 that's dual booted with vista"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by BryantArms on 2008-09-12
Hello.

I want to install Ubuntu Hardy LTS in place of PCLinuxOS 2007 that I now have installed.  It is dual booted with Windows Vista.  I don't want to repartition my disk.  And I don't want to lose files already in pclos that may be useful for ubuntu.  Let me explain what I have done in case that helps me get better advise.

Last year I bought a barely used Acer 9410-4441 from a co-worker for next to nothing.  But it has Vista installed.  When I figured out that I needed to re-learn how to use the operating system I decided to learn about linux instead.

After some research and trying out a lot of live CD's, I decided to install PCLinuxOS2007 onto my computer.  It seemed to need the least amount of adjustments to work reasonably well.  But I didn't want to remove Vista... just in case it was needed for some tasks.

So I figured out how to dual boot pclos with vista with grub by using a program called EasyBCD.  I don't remember all of the details of how I managed to do it.  My disk is partitioned so that vista stayed on the primary partition.  I shrunk its volume as much as I could using vista.  Then I created a partition formatted with FAT32 to use as a shared partition between pclos and vista.  The rest of the HD was left unallocated so that the PCLinuxOS Live installation CD could install automatically while dividing and formatting the unallocated space to suit itself.  Two of the linux partitions are formatted with ext3 and the other linux partition is for linux-swap.  Now when I boot Grub pops up and lets me choose to boot either into vista or pclos with a few other choices.  If I don't make a choice within a limited amount of time, then Grub defaults into pclos.  This has all worked very well.

Yet PCLinuxOS 2007 has its faults.  It has given me about the same number of annoyances as Vista. And it turns out that keeping vista has been very convenient for some situations.  I am tired of trying to figure out how to configure pclos to suit my needs.  And I don't want to feel like I need vista as a backup for some situations.  (Besides that, vista is hogging a lot of disk space.)  Ubuntu Hardy seems to be closer than pclos now to having an easy intuitive interface that just works for most of the common things I do.

I am just a typical user.  I'm not a programmer.  I need the easy symbolic forms of GUI's.  Hopefully all I need to do is use the Live CD to install ubuntu on top of pclos.  If there is a better partition format that ubuntu now uses, then I am open to reformatting the three linux partitions.  I put all of my documents and personal files in the FAT32 partition so I can also get to them with vista.  So the only files in the ext3 partitions are the ones pslinuxos put there.  That is my situation.  Can I simply install over pclinuxos and still have grub work the way it does and not lose my access to vista?

Thanks in advance for any consideration you give to my solicitation for advice.

Bryant

---

### Post by BryantArms on 2008-09-13
I am supposing by the lack of response that maybe the gurus here expect that I will be disappointed with ubuntu too... even with the new release.

Anyway, one of the programs that I have become hooked on is digicam's photo management program.  Its powerful; but if I could I would simplify some of its functions.  I was concerned that installing ubuntu would erase all of the tags and other meta data I have attached to my photo collection even though that collection is not saved on a linux partition.  Fortunately, it turns out that data is part of the jpg file.  This is an example of the kind of data I am concerned about saving before I wipe out pclinuxos with ubuntu.  Can anyone think of other common programs that have data, besides my bookmarks, worth backing up to my storage partition?

The other information I am specifically looking for is a how-to or sneak peak of what the installation will be like for existing partitions.  And maybe someone would like to recommend specific partition sizes for the ubuntu installation instead of the allocation I currently have for pclinuxos.  By the way, my /home partition is 10G, the / partition (root partition?) is 18G, and the swap is 1.5G.  The FAT32 partition for sharing files between linux and vista is 52G.  The rest of my drive, around 80G, is hogged up by vista.  Comments?

---

### Post by caljohnsmith on 2008-09-13
I think your plan sounds just fine. Those partition sizes you have all ready should work perfectly with Ubuntu. Just install Ubuntu over PCLinuxOS like you plan to. But about saving pertinent files from PCLinuxOS, first of all, were there any system configuration files you had to tweak to get PCLinuxOS working smoothly? For instance, like things in /etc/X11/xorg.conf, or did you have to add any special kernel options in your Grub's /boot/grub/menu.lst? If not, then you would probably have to tell us what programs you like using in PClinuxOS for us to help you determine if there are any other program configuration files worth saving. 

You mentioned you used EasyBCD to configure Vista's boot menu, but on start up, do you get first a Vista boot menu or do you get a Grub menu? That's important, because if you are using the Vista boot menu and want to keep it that way, you would have to make sure that you install Grub a little differently then a normal install when you install Ubuntu.

---

### Post by BryantArms on 2008-09-14
First of all, thank-you very much for giving me any attention.  It helps to give me confidence in the general impression I have gotten about the ubuntu community.  (By the way, pclos community has been good.)

You asked about how I boot up with Grub.  Well, I think I go strait into Grub during the boot.  That is because I don't see any Windows style graphics when Grub comes up.  What happens is a after the bios is done doing its thing, a Grub screeen comes up that gives me a list of operating systems.  I choose one or I leave it on the one highlighted at the top of the list, (Linux), and it loads the selected OS.  It has occurred to me that maybe I'm not using EasyBCD at all since I spotted a bunch of Grub files in the / partition while rooting around for files I may want to back up.

Am I using EasyBCD or not?

---

### Post by caljohnsmith on 2008-09-14
> **BryantArms said:**
> First of all, thank-you very much for giving me any attention.  It helps to give me confidence in the general impression I have gotten about the ubuntu community.  (By the way, pclos community has been good.)

You asked about how I boot up with Grub.  Well, I think I go strait into Grub during the boot.  That is because I don't see any Windows style graphics when Grub comes up.  What happens is a after the bios is done doing its thing, a Grub screeen comes up that gives me a list of operating systems.  I choose one or I leave it on the one highlighted at the top of the list, (Linux), and it loads the selected OS.  It has occurred to me that maybe I'm not using EasyBCD at all since I spotted a bunch of Grub files in the / partition while rooting around for files I may want to back up.

Am I using EasyBCD or not?
Yes, it sounds like you definitely have Grub installed to the master boot record (MBR) of your HDD. That means it should be really easy to install Ubuntu and get things working, at least as far as Grub is concerned. Just do the standard Ubuntu install, and you shouldn't need to do anything special to install Grub to the MBR.

Just as a side note, I should also mention though that if you ever plan on doing any repartitioning at all, I would highly recommend you use Vista's Disk Management rather than anything else; it's not that Vista's Disk Management is so great, it is just that the geniuses at Microsoft designed Vista so that Vista maintains its own partition table outside of the HDD's main partition table in the MBR. So in practicality that means if you use anything other than Vista's Disk Management to do your partition changes, it can break Vista and cause Vista to not boot at all. :roll:

Anyway, good luck, and let us know if you run into any problems or have any more questions. :)

---

### Post by zvacet on 2008-09-14
>  By the way, my /home partition is 10G, the / partition (root partition?) is 18G, and the swap is 1.5G. The FAT32 partition for sharing files between linux and vista is 52G. The rest of my drive, around 80G, is hogged up by vista.

If it is possible shrink your Vista more if you can ( I never used it so I don´t know if you can do that).Add that unallocated space to your share partition.For linux partition I will give 10 to root and 18 to home.

---

### Post by louieb on 2008-09-14
> **BryantArms said:**
> ...I currently have for pclinuxos.  By the way, my /home partition is 10G, the / partition (root partition?) is 18G, and the swap is 1.5G...
This should be an easy one.  
1st copy off anything in  PCLinuxOS you want to keep.
Just tell the Ubuntu installer to use the PCLinuxOS partitions. To do that choose the manual partitioning option. 
right click on the 10GB partition and choose edit. Make its mount point / (root). and check the format box.

do the same thing for the 18BG partition only make its mount point /home. 

The Ubuntu installer should see the swap partition and use it without you doing anything.  

Just let the install continue and you should be dual booting Windows and Ubuntu with GRUB an the boot manager.

BTW: Even if you are using EasyBCD  you still have GRUB. What happens is EasyBCD  loads GRUB then GRUB load Linux. 
Good Luck.

---

### Post by BryantArms on 2008-09-16
OK!

I feel encouraged.  Thanks.

There are just a few more things I want to know before I plunge in.  I can figure them out by myself but maybe I can save some time by bringing them up here.

One of the last bits of information I am trying to put together is whether or not I should install the 64bit version of ubuntu or the 32bit version.  I am only just beginning to wonder about that since I ordered some ram for this machine.  It turns out that it is capable of handling 4G of ram.  And I am under the impression that windows normally can only recognize 2G unless it is the 64bit version of vista.  Since my machine is supposedly designed for vista, Aspire 9410-4441, I am wondering if it is a 64bit machine.  Crucial.com's scan said that the machine can handle 4G, but that vista may only be able to use 3or3.5G unless it is the 64bit version of vista.  Then it can see it all.

Can ubuntu see all 4G of RAM when I install it?  If so, would that be true even if I don't use the 64bit version of ubuntu?  (I have read that the 64bit version is very buggy.)

Please forgive me if I'm heading off on a tangent for this topic.  I am still focused on installing ubuntu in place of pclos while maintaining my dual boot with vista.  I want to set aside at least two hours to focus on the installation and adjustments.  So maybe tomorrow I will finally do it.

Thanks again for the encouragement and advice.  Please don't hold back if you have more.

Bryant

---

### Post by louieb on 2008-09-17
> **BryantArms said:**
> OK...
Can ubuntu see all 4G of RAM when I install it?  If so, would that be true even if I don't use the 64bit version of ubuntu?...

You will need a 64 bit OS to use more than 2GB ram. The 2+GB limit is just math.
 A 32 bit base 2 number uses 31 bits for the number and 1 bit for the sign.  2^31 = a little over 2G.

---

### Post by caljohnsmith on 2008-09-17
> **louieb said:**
> You will need a 64 bit OS to use more than 2GB ram. The 2+GB limit is just math.
 A 32 bit base 2 number uses 31 bits for the number and 1 bit for the sign.  2^31 = a little over 2G.
Are you maybe forgetting the effect of the sign bit? With 1 bit for the sign, the range is then -2GB through +2GB, or ~4GB. 32 bit OSes can access up to 4 GB of RAM, not 2 GB I believe. For instance, see the [Wikipedia article on 32-bit computer architectures]("http://en.wikipedia.org/wiki/32-bit").

---

### Post by BryantArms on 2008-09-20
I have decided to wait until I got the new RAM before I do the install.  And now I have the RAM.  Two two-gig sticks have replaced two half-gig sticks.  You can imagine how eager I have been to see the effect on performance of my software.

The result has been surprising.  Vista sees the 4 gigs but only uses a little more than three of them.  Otherwise it is working much better than before... and now without crashing.

But here is the part that surprises me:  Linux won't work anymore!  When I tried to boot into pclos I ended up at a black screen and the computer eventually settled down as if waiting for something.

So I thought "Oh well.  Now I will install Ubuntu.  But first let me see how the live CD version works with this extra ram."  When I tried that ubuntu seemed to start off normally.  Then some very distorted graphics appeared when I would normally expect the home screen.

None of the live CDs I have laying work either.  I tried pclos 2008 gnome and Knoppix 2007.  The optical drive seems to be working since it still plays movies.

What is going on?  Is Linux not compatible with 4-gigs of RAM?:confused:

---

