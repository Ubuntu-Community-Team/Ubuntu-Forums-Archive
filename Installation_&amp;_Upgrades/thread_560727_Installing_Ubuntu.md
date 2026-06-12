---
title: "Installing Ubuntu"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by mlyons16 on 2007-09-26
I'm getting ready to install now. Now I'm going to use the installer included on the Desktop Live cd, but I've come across a website that provides insight on partition planning. I still want my Windows Vista partition but I also want my ubuntu one.

Now, I haven't done anything yet, but can someone advise me on the best partition plan based on the ones available on this website:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Thanks for your support.

---

### Post by Pumalite on 2007-09-26
First of all do your partitioning with the Vista partitioner(somewhere in Administration, hard drives), Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
And create the following partitions in the partition you created before:
10 GB for '/'
500 MB for /swap
The rest for /home
Install with Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below green sign 'Start Download'
And install using the partitions you created earlier.

---

### Post by mlyons16 on 2007-09-26
Okay, we'll thats fine.. so don't use the desktop cd?

Why not, I've been using it fine as my live cd for about 3 weeks now.

---

### Post by Pumalite on 2007-09-26
Alternate CD is easier to install, you have more control, and you avoid possible hardware and graphics problems: That you booted the Live CD is no guaranty that the installation will go well, especially if you want things certain way.

---

### Post by mlyons16 on 2007-09-26
I think I'd be more comfortable using the graphic installer. I mean, I'm not a dumbass with computers, but I'm not super super technical either. I understand the Alternate CD uses a text based installer.

I've been looking at instructions on this site:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Would you agree with these installation instructions. They seem a little more user friendly than:

10 GB for '/'
500 MB for /swap
The rest for /home

No offense, I'm sure that its good information you're providing. I just want to keep things simple though right now. And the first link:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I brought that up because I'm concerned over the file system thing. I want to be able to create and save documents in Ubuntu, and have a file system that will be supported by my windows and ubuntu partitions if im correct

---

### Post by Pumalite on 2007-09-26
You can mount Windows from Ubuntu. You can install ntfs-3g and have read/write. You can also make a different partition formatted Fat32 to share data between OS's

---

### Post by mlyons16 on 2007-09-26
Okay, so by now I've taken on a lot of information. Kind of summarizing everything we've talked about. Can you detail my instructions for installing. And if i install using the graphical installer or the alternate cd text installer.... will I achieve the same end result?

---

### Post by Pumalite on 2007-09-26
Just use my instructions in post # 2 and you'll be fine,

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by mlyons16 on 2007-09-26
I'm just feeling intimidated by the wealth of information. I just kind of find out something on my own or am attracted to using the built in graphical installer, and now I'm being advised to take a more technical approach to the problem.

Not that I don't appreciate you're insight. This is what I want:

I want to have both Windows and Ubuntu on my HP Pavilion a6120n.

I have an Intel Core 2 Duo 2.4 GHz, 2 GB Memory, 320 GB HD, Intel Integrated Graphics card (supported by Ubuntu Desktop Effects and Compiz Fusion as I've experimented in the live cd).

I want to at my desire boot into either Windows or Ubuntu, and when I'm in there, I want to be able to open a word document in open office and type away and save it. I'd like to do the same thing in Windows. If I can access documents I've created/modified in Windows in Ubuntu or vice versa, excellent.

What is the best approach to satisfying that desire?!?!

---

### Post by Pumalite on 2007-09-26
Exactly what I told you. Don't be afraid. You'll have the things you want. But in any installation there is a danger and no warranties. You have to backup everything before you install another OS. That's just good sense. I do it always just as good practice.

---

### Post by rsambuca on 2007-09-26
I understand your hesitation, since I went through the same thing when I first started.  Having said that, there comes a time when you have to get your feet a little wet!

There isn't much to say that hasn't already been covered.  Like already stated, I would:

1.  Use the Vista disk manager to shrink the Vista partition.  This will give you space for Ubuntu to use on the hard drive.
2.  Install Ubuntu using your previously mentioned partition sizes.  They look great to me.  It doesn't really matter whether you use the liveCD or the alternate CD as they end up doing basically the same thing.  Both are easy to follow along.

EDIT:  Backup your data first, just in case!

---

### Post by mlyons16 on 2007-09-27
Alright, We'll I'm backing up everything onto my USB key, CD's etc etc. I realize that's good practice. But.. when it comes to doing the partitions, how do I do that. I found the thing in Vista to do it, but where do I start in the disk management window?

I have my C: drive which also has the native HP Recovery partition on it. Both are NTFS. 289.26 GB is the current capacity of my C drive and the current capacity of my D: Recovery Partition is 8.83 GB. Now, on the primary C: partition, I have 222.02 GB in free space. From that information, where do I go next?

I'm sorry to be asking so many questions, but I really like learning new things and I'm really giving this Ubuntu thing all I've got.

---

### Post by Pumalite on 2007-09-27
In the C: 222.02 GB use Gparted and proceed as I told you.

---

### Post by mlyons16 on 2007-09-27
Then What is that Vista partitioning tool for? Just to determine the capacity of my existing partitions?

---

### Post by Mze on 2007-09-27
Check  this website out. Explains very well what you need to do with images.

Cheers.

[How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by maybeway36 on 2007-09-27
I don't see why you would need GParted if you use Vista.

---

### Post by mlyons16 on 2007-09-27
I'm just going to print and follow the instructions in post 15. Thank you to that user who posted it and thanks again rsambuca!

---

### Post by mlyons16 on 2007-09-27
> **Mze said:**
> Check  this website out. Explains very well what you need to do with images.

Cheers.

[How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

Having read that installation guide, I'm rather relieved. A couple of follow up questions now:

1. Is GRUB automatically installed? GRUB isn't another third party tool I need to get that screen when my PC boots to choose between Vista and Ubuntu right?

2. What about that NTFS-3g project thing. How does this come into play and how do I use that?

3. If I hold off on the installation until 7.10 is finalized, can I expect at least the steps pertaining to the partitioning in Vista to be the same? I'd imagine that the installation steps using the graphical desktop CD installer would be proportionally similar, correct?

4. Once everything is installed, will I have access to my documents, pictures, music, etc. that I have in Vista? I guess this comes into play with the NTFS-3g project, right?

Thanks for everyone's assistance thus far. The support is amazing here.

---

### Post by rsambuca on 2007-09-28
> **mlyons16 said:**
> 1. Is GRUB automatically installed? GRUB isn't another third party tool I need to get that screen when my PC boots to choose between Vista and Ubuntu right?

2. What about that NTFS-3g project thing. How does this come into play and how do I use that?

3. If I hold off on the installation until 7.10 is finalized, can I expect at least the steps pertaining to the partitioning in Vista to be the same? I'd imagine that the installation steps using the graphical desktop CD installer would be proportionally similar, correct?

4. Once everything is installed, will I have access to my documents, pictures, music, etc. that I have in Vista? I guess this comes into play with the NTFS-3g project, right?

Thanks for everyone's assistance thus far. The support is amazing here.
1.  Yes, Grub is the bootloader that gives you the option of which system to boot-up.  It is highly configurable and easy to use.
2.  ntfs-3g allows you to write to your Windows filesystem (reading the Windows drive is enabled by default).  It is stable.
3.  It doesn't matter which version of ubuntu you install, the procedure will be the same.  Honestly, I would just go ahead and do it now.  You can always upgrade to Gutsy when it becomes a stable release.  As an alternative, since it will be a fairly fresh install, you can just do a new re-installation when gutsy comes out and use Feisty as a 'test run'.  Once the partitions are set up, you only have to do that step once.  It takes less than 30min to install, so it isn't a big deal.
4.  See point 2.

---

### Post by mlyons16 on 2007-09-28
I pretty much understand how to partition. I'm going to hold off on installing until Gutsy becomes a stable release in about a month. Okay, so now my focus is the NTFS-3g project. My questions are. if I've created documents, or have multimedia files in my Windows partition, can I access them in Ubuntu.

Vice versa, if I create a document or download a song while using Ubuntu, can I access that file while in Windows?

How do I set up the NTFS-3g?

---

### Post by rsambuca on 2007-09-28
I really don't see what is gained by waiting, but, your choice obviously!

Out-of-the-Box, Ubuntu can read from ntfs drives, but not write to them.  That is where the ntfs-3g driver comes into play.  To install ntfs-3g as well as its GUI configuration utility, you can either use the Synaptic Package Manager, or use the terminal```
sudo apt-get install ntfs-3g ntfs-config
```.  You then just run the ntfs-config utility and it sets everything up for read & write access to your ntfs drives.

Natively, Windows will not even see the ext3 drives, but with the fs-drivers for windows, it gives full read/write access to those drives, and they are seen and show up exactly like another hard drive in explorer.  You just have to pick the drive letter(s) for the ext3 drive(s).

I think you are ready to install.

Do it!

DO IT!  :)

---

### Post by mlyons16 on 2007-09-28
Well I guess I can/should/could/would. lol

I don't REALLY want to wait a whole other month to install. 

So install NTFS-3g from inside ubuntu.

For reading my ext3 drive while in Vista, where and how do i install the solution named, "fs-drivers".

---

### Post by rsambuca on 2007-09-28
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mlyons16 on 2007-09-28
alright cool...

can you now help me with some migratory advice. If I use the ntfs3g thing, then i can get access to my mp3s, jpegs, etc from windows while in ubuntu.

Is it pretty seamless to use my music files from the 2 os's. What program should I use especially for playing music, burning cds, etc..

I plan on using Google's Picasa2 for photos.

---

### Post by Shazaam on 2007-09-28
> **mlyons16 said:**
> alright cool...

can you now help me with some migratory advice. If I use the ntfs3g thing, then i can get access to my mp3s, jpegs, etc from windows while in ubuntu.

Is it pretty seamless to use my music files from the 2 os's. What program should I use especially for playing music, burning cds, etc..

I plan on using Google's Picasa2 for photos.

As stated before Ubuntu (linux) has READ access to Windows filesystems enabled by default. So you can copy from the Windows partition and paste to the Ubuntu partition (desktop, folders, etc) Only install the files for write access to Windows if you really need it. You could also set up a separate shared partition (NTFS, FAT32) for Windows/Ubuntu.
As far as multimedia software there are a bunch and you will get a whole slew of opinions as to which one to use. Try the ones that come preloaded and if you want check Synaptic for other apps.

---

