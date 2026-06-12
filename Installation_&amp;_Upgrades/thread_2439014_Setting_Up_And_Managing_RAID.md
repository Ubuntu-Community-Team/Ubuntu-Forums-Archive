---
title: "Setting Up And Managing RAID"
date: 2020-03-21
forum: Installation &amp; Upgrades
---

### Post by racerxsixtynine on 2020-03-21
In addition to the system drive, the machine I recently built has four 4 terabyte drives in it that I plan to use as a RAID array, for backup of my photos and music. Is it a realistic expectation that I can set up the RAID and manage it with the Ubuntu Desktop OS?

Or do I need to use Ubuntu Server?

If I should be using Ubuntu Server, should I install that on a separate partition on the system drive?

Will I be able to access the RAID created by Ubuntu with my Windows machines connected to my peer to peer network?


Looking through past threads regarding this, I see that the process should be install Ubuntu Server first, then Ubuntu Desktop. Looks like I have started off on the wrong foot.

Also, none mention the network compatibility with Windows machines.

So many questions . . . . . .

---

### Post by rsteinmetz70112 on 2020-03-21
Ubuntu Server and Desktop are the same OS, with somewhat different packages. You can certainly set up RAID on Ubuntu Desktop I've done it, you may need to add some packages to get the features you want. Exactly how you set it up depends on your preferences. I typically use software raid with mdadm and lvm2 mostly because I started doing it that way. There are other methods. Others here have more experience and expertise. 

If you want help or advice please post some more detail about what you're trying to do.

---

### Post by racerxsixtynine on 2020-03-21
> **rsteinmetz70112 said:**
> 
If you want help or advice please post some more detail about what you're trying to do.

I would like to create a RAID using the four 4 terrabyte drives, that can be accessible on my peer to peer network by all of my other machines, i.e. several laptops, and several desktop PC's, all running various versions of Windows, such as Windows 2000, Windows NT, Windows XP Pro and Windows 7 Pro.

The RAID will be used for storing and accessing my photos, music, and documents.

So essentially this Ubuntu machine will function as a NAS.

---

### Post by racerxsixtynine on 2020-03-21
> **rsteinmetz70112 said:**
>  I typically use software raid with mdadm and lvm2 mostly because I started doing it that way. 

So mdadm and lvm2 are packages?

> **rsteinmetz70112 said:**
>   There are  other methods. 

I suppose so. Like Windows, there is always more than one way to get things done, eh?

> **rsteinmetz70112 said:**
>   Others here have more experience and expertise. 

Again, I suppose so. I'm counting on it too. This forum is filled with knowledgeable and helpful people.

---

### Post by racerxsixtynine on 2020-03-25
Maybe I didn't ask the question right or something. How about I try again.

I'm looking for guidance on how to proceed creating and managing a RAID on a machine I recently built and installed Ubuntu on. I've searched and read, and read and searched. One member here, @rsteinmetz70112 replied, and dropped a couple clues which have been helpful, but chasing down the info has only left me more unsure about the methods and processes I need to follow.

He mentioned there are others here with more experience and expertise, so perhaps some of them might pop in and help me find my way.

The system has a 1 terabyte system drive, and four 4 terabyte NAS rated drives where I would like to set up the RAID. I know I will need to get more fluent in using the terminal for installing whatever package(s) that are required, and then using it to create and manage the RAID. 

Also, I wish to set this up so it is accessible by my Windows machines that are connected to the peer to peer network I have here, and, hopefully allow my televisions and stereo system access the video and music I will be storing on it.

Mr. Steinmetz mentioned mdadm, and lvm2, but I haven't been able to find out if I should use one, the other, or both. Perhaps someone experienced in this stuff can chime in here. The last thing I want to do is dive in head first, and, not being fluent in Linux, dig a hole that can only be fixed by filling it in and starting over.

System details are:

ASUS Prime Z370-AII motherboard
Intel Core i5-8400 6 Core Processor
64 gigs RAM
(1) 1 Terabyte WD Blue Hard Drive
(4) 4 terabyte WD Red NAS hard drives
Ubuntu 18.04 OS

Thanks to anyone, and everyone who is able to help.

---

### Post by aljames2 on 2020-03-25
Complex things you want to accomplish, and it all is possible.  However, being new to Linux means you will need a lot of self-study in Linux concepts starting with the command line, even using a Desktop environment, command line use is essential.  Then there is learning how to install, maintain the OS.  There are many packages & tools available to help achieve your goals depending on what they are specifically, such as NextCloud, Plex, NFS, SSH, Putty, CIFS, WinSCP, SFTP (don't use FTP), VPNs, Backup tools, Software RAID arrays (mdadm)...including which RAID convention, how many drives needed, and understanding the consequences of a crapped out drive and it's effect on the entire pool (other drives), & many other issues / options to consider depending on your needs.

But first....before beginning any of this, I think you should understand your current network architecture and what may be needed to accomplish your goals in as secure a way as possible.  There are things to learn with routing, firewalls, switches, managing network traffic, subnetting, internet involvement, dealing with wireless access points, and more.  The network architecture needs to be set up correctly (with your goals in mind) before setting up computers and installing software packages.  Why I bring up the network stuff is everything matters...who your users are, where they are, how far away they are, how they will connect, what are their technical abilities, what OS's are they running, what are their needs, and others.  Then there is having a backup & restore plan (RAID is not a backup system).

To make it simpler for my household, I ditched all the Windows machines.  My wife uses Ubuntu Desktop now and she probably don't realize it, as long as her functionality is there.  I do run 1 Windows (strictly gaming) PC for FPS games, that's it.  Everything else is Linux.

I'm not trying to dodge your question.  But it is not one that has an answer you may be looking for (step-by-step).  Too many possibilities and unknowns.  I recommend you not give up, stay inspired, just plan to hunker down and do some Linux learning.

[http://www.linuxcommand.org/tlcl.php](http://www.linuxcommand.org/tlcl.php)  (free Linux Command Line e-book)
[https://help.ubuntu.com/](https://help.ubuntu.com/)  (Official Ubuntu documentation)

Google searches are ok, just don't start copying/pasting commands you don't understand.  Enjoy the journey :)

---

### Post by lvm on 2020-03-26
Concise md RAID guide is available here: [https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Cookbook](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Cookbook)
Setting up samba (windows networking) standalone configuration is described here: [https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Standalone_Server](https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Standalone_Server)

---

