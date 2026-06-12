---
title: "A couple questions."
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by ColeTurner on 2011-02-13
I am seriously considering switching from Windows XP SP3 to Ubuntu Linux. I am looking for a more modern operating system. I am also looking at not spending $100+ on said operating system. I also like the idea that Ubuntu is stable and secure. I want to completely abandon Windows in favor of Ubuntu. I am not much interested in a side by side installation.

So, I have a couple questions. One question I have is, what are the differences between 
Ubuntu Desktop Edition and Ubuntu Desktop (GUI) Installation? How would I install Ubuntu Desktop (GUI) Installation instead of Ubuntu Desktop Edition? Is the installation of one more difficult than the other.

I am attracted to the GUI Installation because it only required 512 megabytes of RAM. I have only 1 Gigabyte of RAM and I figure that using an operating system which requires less memory than I have is a good idea. I will be getting an additional 512 megabytes of ram which will give my computer 1.5 gigabytes of RAM.

I also have concerns regarding compatibility. A fairly exhaustive overview of my computer can be found here: [http://temp.net63.net/My%20Computer%20Specs.htm](http://temp.net63.net/My%20Computer%20Specs.htm).
If you see a component in my computer that may not be compatible with Ubuntu, please tell me.
 
Know that I am a complete newb to Linux and Ubuntu. 

Yes, I know, the post is long. I am sorry about that. I only want to be thorough.

---

### Post by mr_luksom on 2011-02-13
I can't access your link, but you will be shocked at how much hardware is supported by linux. I other than my old iPhone, I have never had hardware issues, provided I was using Ubuntu Desktop (some more advanced bistros like xubuntu, lubuntu or puppy linux can be more difficult), it was all installed for me. If you have any issues, there are lots of knowledgeable people here.

As for which install, just use Ubuntu Desktop, you should not need the alternative installer. 1GB ram is heaps, I have installed ubuntu with 256MB without issues.

Take the dive into linux, you may like what you find. None (maybe a small number with a great deal of trouble) of your windows software will work with linux, but there are great open source alternatives, all free. Within a few weeks, you'll never want to use windows again.

---

### Post by eentonig on 2011-02-13
Both of the Desktop versions you mentioned, seem to be the same to me. 

Just download the LiveCD, burn it to a CD and boot your PC from it.

This will run Ubuntu on your computer without making any changes at first. And will give you an idea how well your HW is supported. 

If you don't see too many problems, click on the installer icon on your Desktop and the installation will start (GUI based). If there's any question on the way, note it down and abort or postpone the installation and pop it here, so people can help you.

---

### Post by Hippytaff on 2011-02-13
I'd suggest trying ubuntu from the livecd to check hardware compatability. Bear in mind that it will be slow from cd, but this will not be the case once it is installed. If all the hardware works fine from livecd you will be fine. Most hardware is well supported. There are still some issues sometimes with Nvidia, and broadcom, but they can usually be over-come ;-)

---

### Post by ColeTurner on 2011-02-13
One, I must thank you all for your overwhelming support and help. 
Two, how do I know if I've made the CD correctly. I am using the Live CD to post this message (if that is relevant). God, Ubuntu is beautiful.
Three, does any one know of any good fee file back up sites? If I made the C.D. right and if I can find good file back up and if 1 gigabyte of ram is enough, I am thinking about installing either tonight or tomorow. I am extremely eager to get started with Ubuntu. How easy or difficult is the install? What happens when I right click in Ubuntu? What kind of anti malware is availabe for Ubuntu? Does Ubuntu have a task manager?

---

### Post by Hippytaff on 2011-02-13
wow...lots of questions :-)

If your using the livecd to post then you've done it right. It might be worth trying a few things (like streaming from youtube) to check sound etc.

ubuntu one is a cloud storage site you can use for free (up to a certain amount of space). and I wouldn't worry too much about malware on linux, unless you download a lot of third party software. It remarkably secure. Just use the repositories to download the software you want.

If you type ```
top
``` into a terminal (open a terminal with CTRL+ALT+T) that is like a task manager. Even better - download htop by doing```
 sudo apt-get install htop
``` once it's installed type htop.

[the official documentation ]("https://help.ubuntu.com/")is worth a read and the [ubuntu manual]("http://ubuntu-manual.org/")

Enjoy :-)

Edit -> 1 Gig of RAM is plenty

---

### Post by Moyamo on 2011-02-13
If you wan't anti-malware(which you don't need). Try [avast! anti virus]("http://www.avast.com/index") and for a firewall try [firestarter]("http://www.fs-security.com/"). These all have a GUI but you get some great CLI firewalls and anti virus

---

### Post by TenPlus1 on 2011-02-13
Ubuntu has a few flavours which differ slightly in the Window Manager and programs installed and thankfully each can be run from CD to test and find the one that suits you before installing on your machine...

Kubuntu (uses KDE which is more eye candy than most)
Ubuntu (uses Gnome which is the middle ground but still has 3d effects)
Xubuntu (uses XFCE which is lighter and feels quicker) I use this one
Lubuntu (uses OpenBox which is the lightest and fastest, usually for older systems)

All of the above will run with 512mb without a problem and each have their own internet, office, multimedia software available on cd and in the global repository (all FREE for download)...

---

### Post by gordintoronto on 2011-02-13
After installing Ubuntu, start System/Administration/Synaptic Package Manager, and search (not quick search) for "ubuntu-restricted". Then install the packages! Select them, then click on the "apply" button.

What do you use a computer for?

---

### Post by ColeTurner on 2011-02-13
I use my computer mostly for surfing the web and some image manipulation. I also use my computer for downloading images, audio and video.

---

### Post by grahammechanical on 2011-02-13
If you think that your first post was long, then you should see some of my replies! Can I make a couple of points?

The first time you install you might want to allow the installer to do it all for you. Especially if you do not want to keep the original operating system on it. Then, you might want to try it again now that you are more confident about what is going to happen. 

If so, you can create more than one partition. With just one partition all your data files will be kept in a folder called Home. If you need to re-install and reformat then that folder will be lost. If you create two partitions you can put the operating system in the first partition (20GB should be fine) and give it the mount point of /   and then use the rest of the disc for a second partition which you give a mount point of /home. Then all your data and settings will be save from a re-installation.

I have four partitions. I use the other two to install different versions of Ubuntu for testing and for backing up my data if I need to re-install. I get a menu at startup that lets me choose which operating system I want to try out.

By the way I only have 1GB of memory. It is fine. These are just some things to think about.

Regards.

---

### Post by ColeTurner on 2011-02-13
I am currently installaing Ubuntu. I have gotten to a part which says "Ready when you are". What do I do now? It doesn't seem to be advancing.
I think I figured it out.

---

### Post by Moyamo on 2011-02-14
> **grahammechanical said:**
> If you think that your first post was long, then you should see some of my replies! Can I make a couple of points?

The first time you install you might want to allow the installer to do it all for you. Especially if you do not want to keep the original operating system on it. Then, you might want to try it again now that you are more confident about what is going to happen. 

If so, you can create more than one partition. With just one partition all your data files will be kept in a folder called Home. If you need to re-install and reformat then that folder will be lost. If you create two partitions you can put the operating system in the first partition (20GB should be fine) and give it the mount point of /   and then use the rest of the disc for a second partition which you give a mount point of /home. Then all your data and settings will be save from a re-installation.

I have four partitions. I use the other two to install different versions of Ubuntu for testing and for backing up my data if I need to re-install. I get a menu at startup that lets me choose which operating system I want to try out.

By the way I only have 1GB of memory. It is fine. These are just some things to think about.

Regards.

1GB OMG. That's half the size of my home directory.

---

