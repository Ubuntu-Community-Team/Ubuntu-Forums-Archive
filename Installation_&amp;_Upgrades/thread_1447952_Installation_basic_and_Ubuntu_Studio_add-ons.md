---
title: "Installation basic and Ubuntu Studio add-ons"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by w_tanoto on 2010-04-06
Hi. I am new to ubuntu. Plan to install ubuntu (version 9.10) with Windows 7 side by side. How do I get the add-on to make it ubuntu studio, and how do I install it? The feature it has seems too good to be true, so I decided to try it. I haven't installed ubuntu properly yet, so you have to excuse me if I don't understand anything. (I have tested it in a virtual machine, but haven't got that far). My experience with ubuntu was only tweaking the boot menu by looking at some guides. It might be better if you can explain how the installation works in linux (such as: in windows you use exe, etc). I am not sure, but is "jar" the equivalent of "exe" in windows?

many thanks in advance

---

### Post by cchhrriiss121212 on 2010-04-06
There is a lot of information to cover here, so I'll explain in brief. Firstly you should know that the LTS version of Ubuntu comes out in a few weeks, which I would recommend installing fresh (as opposed to upgrading from 9.10) when it comes out. I'd also recommend you partition your drive manually with a separate /home folder to make future OS installs easier.

About Studio: Once you have 9.10 installed, open synaptic package manager from the system menu and search for studio, install the meta-package (this is a package that contains a new kernel and programs) and the OS will be upgraded. What is the feature you find too good to be true?

There is not a direct equivalent of .exe in Ubuntu, but .deb is similar. You won't be installing anything by downloading from websites, but from synaptic, a gui program which handles the installing and shows you the latest versions of software. It does this by looking through online repositories which you can add to and remove.

---

### Post by w_tanoto on 2010-04-06
okay, I have to admit. I have difficulty in understanding some of these. I heard of "Home folder", but not sure what it meant. All I know is that I am going to make a partition for Windows, Linux and Documents.

What is unbelievable to be true? A lot of things that I can't obtained free of charge on Windows. Out of them all, I have only experienced GIMP.

I am actually planning to upgrade from Karmic Koala to Lucid Lynx at the end of the month, but I have updated all of my Windows installation files, and ready to go. Waiting means that an update will come and come again, and I have to re-do the job (I want to start clean-slate). But if you recommend that, then I'll install Windows 7 alone first, then add Linux after 10.04 release - or just install karmic koala, and overwrite it with lucid lynx.

sorry, but it seems that I need a lot of advice. I am pretty new at this thing, but I think I have to try linux someday, and this is the day to put it to separate HDD instead of just virtual.

---

### Post by cchhrriiss121212 on 2010-04-06
I explained things in brief so that you could reply with more specific questions when you are installing, as some users will want to know everything in detail and others will not. I'd recommend that you install 9.10 now even though 10.04 is coming out soon. This way you will have a practice install and be prepared for the LTS version when it comes. 

> okay, I have to admit. I have difficulty in understanding some of these. I heard of "Home folder", but not sure what it meant. All I know is that I am going to make a partition for Windows, Linux and Documents.
Thats right, but you need to know the difference if you are going to set up a manual partition. Windows should be first on the partition as it does not cooperate well with any other systems, it's up to you how much you allocate to windows and how much to ubuntu. When you get to installing ubuntu you can follow this simple model:
/ - This is root where the OS and programs will be stored - 10GB is enough space
swap - This is used by linux systems when allocating memory - use half the size of your RAM for this
/home - This is your documents and settings - use all the remaining space

When you want to install a new linux OS (10.04 for example), you can overwrite the previous root partition and keep the same home folder with all your files and settings. When setting up a new install, select the home partition to be used as /home but do not format it. 

> What is unbelievable to be true? A lot of things that I can't obtained free of charge on Windows. Out of them all, I have only experienced GIMP.
It is true that there are many great programs available for free, but they will not be exactly the same as the Windows counterparts.
Are you planning to use studio for graphical work? There are 3 metapackages for studio: audio, video and graphics. I use the audio stuff and I prefer the open source programs to what is available for purchase on Windows.

> sorry, but it seems that I need a lot of advice. I am pretty new at this thing, but I think I have to try linux someday, and this is the day to put it to separate HDD instead of just virtual.
Take your time with it and ask a question if you get stuck. The more you use it, the better you will be able to achieve what you want.

---

### Post by w_tanoto on 2010-04-06
so, let me get this right.
Here are the partitions that I plan to create:

HDD1:
Windows 7 (maybe around 100GB)
Ubuntu (maybe around 50GB)
The rest of it for Documents

HDD2:
all of them goes to documents.

as far as I know, Windows only allows 4 partitions to be created in a HDD. So, Linux will only be counted as one partition by Windows, and windows won't be able to see it, but within linux, you can see three partitions (or folder?) that you mentioned above (it was automatically created when I attempted a virtual installation without my interference).

I am planning to use audio feature the most. I like tweaking my mp3s. But GIMP was really good too.

Seems that this will lead to a few more questions:
I don't want to use GRUB2 as my default bootloader. I had a terrible experience with this. In GRUB2, I attempted to change the default OS into Windows 7 (not in my own computer). It was successful, but Linux has two entries. I followed a guide (which is complicated and rare) when I did this.
So, here it what I plan to do: create partition using windows 7 DVD, leaving the space for linux unallocated. Install linux first, then Windows, then install EasyBCD 2 beta to ressurect linux by calling GRUB2 via windows bootloader.
Is this going to work?

I understand that linux can read NTFS, but can't modify it (correct me if I am wrong). I will have all of my documents in two NTFS partition as I work mostly in Windows. It would be great if Windows and Linux can read, modify, etc in each others' partitions. Any programmes for this? - can linux recognise those two NTFS documents partitions as its home partition?

Seems that is all I can ask. I will probably have a lot of questions in less than a week time when I start the installation. Let's hope it's going smoothly.

Thank you for all of your answers. It's been really helpful

---

### Post by cchhrriiss121212 on 2010-04-06
> HDD1:
Windows 7 (maybe around 100GB)
Ubuntu (maybe around 50GB)
The rest of it for Documents

HDD2:
all of them goes to documents.
That is overkill for a root partition of Ubuntu, a typical root partition only needs to be 10GB and mine only uses up 3GB of that space.

> as far as I know, Windows only allows 4 partitions to be created in a HDD. So, Linux will only be counted as one partition by Windows, and windows won't be able to see it, but within linux, you can see three partitions (or folder?) that you mentioned above (it was automatically created when I attempted a virtual installation without my interference).
You can have as many partitions as you like inside an extended partition, as Windows cannot control what you do with your own drive. Windows will not be able to see the different filesystem that linux uses (ext4).

> I am planning to use audio feature the most. I like tweaking my mp3s. But GIMP was really good too.
If this is all you want to do then you do not need studio, as it is made for low latency audio production with DAWs, plugin effects and software synthesizers. Just download Audactiy from synaptic and you should be sorted.

> I don't want to use GRUB2 as my default bootloader. I had a terrible experience with this. In GRUB2, I attempted to change the default OS into Windows 7 (not in my own computer). It was successful, but Linux has two entries. I followed a guide (which is complicated and rare) when I did this.
I'm not quite sure what you think went wrong here, but there is no reason to switch from using grub, as it can easily handle what you want it to do. Look up an Ubuntu program called startup manager to switch the default OS when you boot.

> 
Install linux first, then Windows
This is not a good idea for many reasons (try googling it for some idea). When installing a new dual boot system always install windows first, then linux as it is so much easier.

> I understand that linux can read NTFS, but can't modify it (correct me if I am wrong). I will have all of my documents in two NTFS partition as I work mostly in Windows. It would be great if Windows and Linux can read, modify, etc in each others' partitions. Any programmes for this? - can linux recognise those two NTFS documents partitions as its home partition?
Linux can read and modify NTFS (including files in a windows partition), but you can't have two partitions as one home folder. I would recommend that you have the smaller HD just for windows and ubuntu root, and another for shared files.

---

### Post by w_tanoto on 2010-04-09
hi. thanks for all of the tips and answers. Just want to let you know, I am on verge of wiping up my laptop. I will experiment first with the installation. I'll keep your tips in mind. Will let you know in two or three days how it goes.

(Thanks for reminding me of extended partition - I completely forgot about it since the day XP replaces windows 9x)

however:
I can't seem to find startup manager when I tried it on someone else's laptop. So I tried using command that use "sudo" etc, and modify it manually. Most of the guides were for GRUB1, and I was stuck with GRUB2. So I was a bit confused. I will be experimenting with ubuntu after this, and will let you know if I can find startup manager there (maybe my eyes were not sharp enough when I tried to find it some time ago).

---

### Post by w_tanoto on 2010-04-09
installation was successful, BUT.... it does not boot. It loaded GRUB, but then after I chose one from the menu, it hanged indefinitely. Seems that I have to stick to my netbook to install linux. My main laptop has history of rejecting linux. I tried darwin, and it ruined my BIOS. though it runs windows fine, it seems to dislike linux. I will install it to my netbook and back to virtual machine under windows 7

---

### Post by cchhrriiss121212 on 2010-04-12
This could be an error from the install disk, did you check it for errors before installing? Did you burn the cd on the slowest possible speed?

You have to download startup manager from synaptic.

---

