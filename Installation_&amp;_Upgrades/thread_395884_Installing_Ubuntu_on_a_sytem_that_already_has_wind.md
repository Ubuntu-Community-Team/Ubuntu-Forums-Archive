---
title: "Installing Ubuntu on a sytem that already has windows"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Doughy on 2007-03-28
What do I need to do before I attempt to install Ubuntu as a dual boot?

I would like to keep my existing windows OS installed, but just install Ubuntu as a dual boot.  Currently, my hard drive only has one partition which uses all the space.  Will the ubuntu installer allow me to repartition without losing my windows data?  Do I need to repartition before attempting the ubuntu install?

Any help is appreciated.

---

### Post by mac.ryan on 2007-03-28
You can find here the ubuntu how-to:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It is not difficult and it is mostly done automatically by the LiveCD. Enjoy! :)

**[COLOR=Red]EDIT:[/COLOR]** just to be clear, the answers to your questions are: yes (shrinking the partition without loosing data), no (the installer will do partitioning for you during the installation process). Anyhow it is **never** a bad idea to backup your data before manipulating partitions...

---

### Post by az on 2007-03-28
> **Doughy said:**
> What do I need to do before I attempt to install Ubuntu as a dual boot?

Nothing.  Just be sure that you pick the option to resize an existing partition and not the USE ENTIRE DISK option.  The former will do all the work for you.  The latter will wipe your drive and start from scratch.

By default, the first option *should* be the one you are offered.


> **Doughy said:**
> 
I would like to keep my existing windows OS installed, but just install Ubuntu as a dual boot.  Currently, my hard drive only has one partition which uses all the space.  Will the ubuntu installer allow me to repartition without losing my windows data?  Do I need to repartition before attempting the ubuntu install?


You do not need to partition.  The installer will do it for you.  Just sit back and relax.

Back up your important data - the partitionner is safe (it's even a little chicken) but nothing is foolproof.  AFAIK, the linux partitioning tools are just as safe, if not more safe than the ones you would use/buy with windows.

If the Ubuntu installer cannot partition the drive, it will not offer you the option.  If this is the case, maybe try to defragment your windows filesystem and try again.  Also, you need to have enough free space on your windows partition so that it can shrink it...

You need an absolute minimum of 2 to 3 gigs of hard drive space to install Ubuntu.  More (depedning on your needs) is better.

---

### Post by confused57 on 2007-03-28
Here's an excellent howto with screenshots:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
As az mentioned, defragging your Window's partition is probably a good idea before you try to install Ubuntu.

---

### Post by Doughy on 2007-03-29
Thanks everyone, I installed Ubuntu last night without a hitch.  The installer worked extremely well and was very easy.  I was really impressed.

Is this ease of installation specific to ubuntu or does it come from debian/other distros?

---

### Post by mac.ryan on 2007-03-29
> **Doughy said:**
> Is this ease of installation specific to ubuntu or does it come from debian/other distros?

Hello Doughy, first of all: WELCOME! I am rather sure you will soon come to love ubuntu, and enjoy tweaking it according to your needs...

as for the installer, my last debian installation dates back 1,5 years ago. It was also quite easy (not as easy as ubuntu, though). Anyhow, ubuntu explicitly aims to become (but really, it is already!) the easiest and more user-friendly distribution of GNU/Linux...

Have fun with ubuntu! :)

---

### Post by cplewis on 2007-03-29
Hi, I'm in the same bag here...I have burned CD's for Ubuntu and LiveCD and am ready to take the leap.

I have XP Pro, SP2, 80GB HD w/ 52GB Free....How much space should I allocate to what?

Very green here...It shows,lol.

Any assistance will be helpful...just don't want to mess up.

Thanks.

C.P.:guitar:

---

### Post by Doughy on 2007-03-29
> **cplewis said:**
> Hi, I'm in the same bag here...I have burned CD's for Ubuntu and LiveCD and am ready to take the leap.

I have XP Pro, SP2, 80GB HD w/ 52GB Free....How much space should I allocate to what?

Very green here...It shows,lol.

Any assistance will be helpful...just don't want to mess up.

Thanks.

C.P.:guitar:

CP,  since I am a newbie too, this document that was already posted was really helpful:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It suggests allocating about 500MB for swap space (virtual memory).  Other than that, as long as you give a few gigs of space for Ubuntu, it is really up to you.  If you plan on working and installing a lot of programs on Ubuntu, give yourself more space.

One thing that I did was create a separate partition as FAT32.  This makes it so that I can write to that partition whether I am in windows or ubuntu.  Then, you can store all your personal documents in this partition of the drive and access them from either OS.  The reason for this is that windows uses the NTFS file system and ubuntu generally runs ext3.  However, both OSs can read/write FAT32, so it's common ground.  ubuntu can't write to NTFS safely from what I understand.  Windows definitely won't write ext3.

---

### Post by rillip on 2007-03-29
Not to try and turn anyone off, but just as a warning to those who have just installed;  I was really happy with Ubuntu (still am!) when I first got it, but I mostly toyed with it, still was doing most of my stuff in Windows, so I didn't really pay attention to the ammount of free space on the partition.

Well as I started using it more and more, and Windows less, I started eating up the space.  One night I left KTorrent running.  I came back the next day and had to boot into Windows for a particular app. When I went back to Linux... very bad things had happened.  It booted fine, gave me the login, but I could never get pas there.  I spent about two weeks troubleshooting it (not solid, it just took me that long to devout a decent ammount of time) with the help of people like on this forum to figure out what had gone wrong.  I had filled my drive to the point that it couldn't do anything; I couldn't start the gui interface (xserver-xorg) because it has to create files and there was no space. This is NOT an immediately obvious problem; I only figured it out when I couldn't get one of the suggested commands to work, and tried to do "man [command]" (don't remember which it was) and was rudely informed there was not enough space free to do so. Additionally, when my drive has been full I get very poor stability; some apps like Opera will just exit for no reason, and it only occurs when full.

So the moral of the story is alot more space than you think you'll need, and pay attention if you're on a small drive.  If you're going to use the KDE, I highly recommend KDirStat.  I'm sure there's a Gnome equivalent, but I found Boabab was not what I was looking for.  I don't see why you couldn't run KDirStat in Gnome but you'd likely have to have the KDE installed, which could be a little silly.  There's also command line ways to do this ("man du" and "man df" for more info) but I doubt you're goign to want to use the command line, being relatively new.

Still, at some point you're almost certainly going to have to, so it might not be a bad idea to get something like KDirStat, get the information you need, and then try using du or df to try and find out the same informaiton.

---

### Post by cplewis on 2007-03-29
Thanks so much guys!....I'm "Off to see the Wizard"

Will keep you posted...not to make a pun!

---

### Post by Feenix3k on 2007-04-01
Besure to defrag the disc first  to give you the max size for Ubuntu, or the W$ part maybe damaged

---

