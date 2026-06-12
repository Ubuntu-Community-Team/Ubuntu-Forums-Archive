---
title: "Trying to install a plugin"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-17
And it's a binary file. In the error it even says make sure you're not trying to open a binary file. I don't know how to install this otherwise. It's just a single file, no readme. I'm relatively new to Linux and still reading Linux for Dummies. But unfortunately I couldn't find what I was looking for and decided to ask here. Can anybody help?

---

### Post by aysiu on 2006-07-17
Where'd you get the plugin?
What's the name of the plugin?
Do you have a link to the plugin?

---

### Post by Roasted on 2006-07-17
Oh damn I'm sorry I could of sworn I posted it.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I think all of the information you need is there.

In the instructions when it says to put in ./flashplayer-installer, it tells me there's no file or directory. The file is sitting on my desktop and won't open. When I try to open it that's when it says make sure I'm not trying to open a binary file (which it is).

---

### Post by aysiu on 2006-07-18
First of all, the best and easiest thing to do is install from the repositories.

Once you [enable extra repositories](http://www.psychocats.net/ubuntu/sources), you can install a whole host of applications either [graphically with a few clicks](http://www.monkeyblog.org/ubuntu/installing) or [with two commands in the terminal](http://www.psychocats.net/ubuntu/installingsoftware).

In this case, with the proper repositories (see first link): ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by Roasted on 2006-07-18
I could of sworn I did that. I think I used that same exact link and followed the directions. Should I redo it? Maybe I messed up?

---

### Post by aysiu on 2006-07-18
> **Roasted said:**
> I could of sworn I did that. I think I used that same exact link and followed the directions. Should I redo it? Maybe I messed up?
What I'm advising (please do read the links I linked to--they will help you with not only this plugin but with a lot of software installation in general) is installing it from the online repositories.

What you were trying to do was install it from a .tar.gz you downloaded from the Adobe website. If you choose to do it the second way, you would do something like this: ```
username@ubuntu:~$ **cd ~/Desktop**
username@ubuntu:~/Desktop$ **ls**
install_flash_player_7_linux.tar.gz
username@ubuntu:~/Desktop$ **tar -xvzf install_flash_player_7_linux.tar.gz**
install_flash_player_7_linux/
install_flash_player_7_linux/flashplayer.xpt
install_flash_player_7_linux/flashplayer-installer
install_flash_player_7_linux/libflashplayer.so
install_flash_player_7_linux/Readme.htm
install_flash_player_7_linux/Readme.txt
username@ubuntu:~/Desktop$ **cd install_flash_player_7_linux/**
username@ubuntu:~/Desktop/install_flash_player_7_linux$ **ls**
flashplayer-installer  libflashplayer.so  Readme.txt
flashplayer.xpt        Readme.htm
username@ubuntu:~/Desktop/install_flash_player_7_linux$ **sudo ./flashplayer-installer**
``` As you can see, it's a lot easier to use package management to install applications.

*Please* read the links I linked to earlier. You won't regret it.

---

### Post by Roasted on 2006-07-18
When I copied over the first part of that link to open the source list I copied/pasted the following:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

This is what I got:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

BUT the source list still came up. Is this okay? I just wanted to make sure.

---

### Post by aysiu on 2006-07-18
It's perfectly fine. Read more here (especially the bottom bit):
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Roasted on 2006-07-18
I'm sorry... maybe I need to do some more reading or something, but I'm reading the links you sent me and I'm learning a lot but... maybe I'm in over my head or just not clicking with the material, but I just don't see how to install this file I got from shockware. My repositories I updated to what you posted above and everything. I even went back and tried to put the command back in to see if anything helped, and I'm still getting the no directy or file found. ](*,)

---

### Post by aysiu on 2006-07-18
You don't need the file from Adobe. You don't need the .tar.gz.

When you install from the repositories with this command ```
sudo aptitude install flashplugin-nonfree
``` that does **everything**. It downloads the installer file, and it installs Flash for you. Then the plugin is there already and ready to be used.

You're still wanting to use the .tar.gz you downloaded. Throw it in the garbage. You don't need it.

---

### Post by Eric_T on 2006-07-18
When I try to install the flash plugin I get:

Couldn't find any package whose name or description matched "flashplugin-nonfree"

I have all repositories enabled...

---

### Post by aysiu on 2006-07-18
When you say "all the repositories," do you mean all the checkboxes in Synaptic or following the tutorial I linked you to?

Also, after you change your repositories list, you have to let the package manager know you've updated it, so it can get the latest information. In Synaptic, it's clicking the **Reload** button. In the terminal, it's ```
sudo aptitude update
```

Can you post here (copy and paste the text of) these commands? ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
cat /etc/apt/sources.list
```

---

### Post by Roasted on 2006-07-18
I used this command as instructed. I assume I was supposed to use it in the Terminal? I did. 

sudo aptitude install flashplugin-nonfree

And I got:

Couldn't find any package whose name or description matched "flashplugin-nonfree"
The following packages have been kept back:
  linux-image-2.6.15-26-amd64-generic
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

](*,) :(

---

### Post by aysiu on 2006-07-18
There's a command you have to run *before* that, assuming you enabled the proper repositories, that will let Ubuntu know "Hey, I've updated my repositories list. Can you check again to see if Flash is in there?" It's *sudo aptitude update*. So you would really run *two* commands: ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by Roasted on 2006-07-18
Okay, I must of goofed up the repository thing. I did what you said and I'm getting the same error in the terminal. Back to square one to figure out what repositories I need. Any tips before I do this? (eating lunch)

---

### Post by aysiu on 2006-07-18
This link will help you get the right repositories--trust me. I've installed *flashplugin-nonfree* several times before:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Roasted on 2006-07-18
Okay I've got to be doing something wrong.
I went into the sourcelist and changed everything. Already did that twice but I did it again to make sure. Then I updated in terminal, and then pasted the other line you sent me to install the plugin. STILL I get the same thing.

Is this supposed to auto-activate whatever repositories I need or something?

---

### Post by aysiu on 2006-07-18
It's in the Multiverse repositories. I'm sure of it. You can check it out right here:
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

I know you said you've replaced your sources.list twice. Can I just take a look at it, in case something didn't go well? Please post the output of these two commands? ```
sudo aptitude update
cat /etc/apt/sources.list
``` Just highlight everything in the terminal and copy and paste the text into a post.

---

### Post by Roasted on 2006-07-18
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [43.0kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [25.0kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Fetched 119kB in 2s (46.5kB/s)
Reading package lists... Done

---

### Post by aysiu on 2006-07-18
Can you also post the output of ```
cat /etc/apt/sources.list
```?

---

### Post by Roasted on 2006-07-18
Surely.

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

---

### Post by aysiu on 2006-07-18
Yeah, that confuses me. Your sources.list looks good.

So ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
``` says the package can't be found?

If you go to System > Administration > Synaptic Package Manager, click **Reload** and then do a search for *flash*, what do you see?

---

### Post by avtolle on 2006-07-18
This may be totally without merit, but I noticed while scrolling through this thread that one of the packages held back was the kernel for AMD 64. IIRC, there are some issues with Flash and 64 bit processors. This may be the result of faulty memory, or otherwise totally useless, but it is offered FWIW.:)

---

### Post by Roasted on 2006-07-18
I opened it, hit reload, and it looked as if it were downloading something. Then, I got this error.

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-synaptic.png[/IMG]

And what's this talk about the 64 bit processor stuff? For the record, I have an AMD 64 bit 3000+. Perhaps I should get the non-64 bit file and see what happens?

---

### Post by avtolle on 2006-07-18
As I am rapidly reaching the upper limit of my knowledge, I can't answer your question. Perhaps you might search the Forums for any threads dealing with this issue. Sorry I can't be of further assistance.

---

### Post by Roasted on 2006-07-18
I'm still trying to understand something. What are repositories exactly? Are they like preinstalled "packs" of plugins, and it's not so much that you need to DOWNLOAD the plugins, you just need to activate the repository as well as activate the actual plugin - right? Or am I completely off?

And I assume that the one code I put in the terminal was more or less an auto-activator or some sort?

---

### Post by aysiu on 2006-07-18
> **Roasted said:**
> I opened it, hit reload, and it looked as if it were downloading something. Then, I got this error.

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-synaptic.png[/IMG]

And what's this talk about the 64 bit processor stuff? For the record, I have an AMD 64 bit 3000+. Perhaps I should get the non-64 bit file and see what happens?
Oh! That's it. Sorry. I didn't even think to ask you before. 64-bit Flash isn't so easy: [quote=Help Ubuntu]    *

      Flash for AMD64 and PPC
          o

            At present, there is no non-free flash implementation available for 64-bit processors (or Mac) because the manufacturer does not support them. However, there are two free implementations in the works. One is gnash and the other is swfdec. [WWW] Gnash, whilst still under development, aims to be a proper free, open source replacement for all the platforms. There is a repository hosting AMD64 Gnash packages at [WWW] [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)

            If you are determined, install a i386 Ubuntu in a DebootstrapChroot and launch your browser with flash plugin from there.[/quote]

---

### Post by Roasted on 2006-07-18
I'm sorry, I don't want to move too fast or else I'll get caught up and confused.

How about I just install a non 64 bit plugin? I didn't buy my CPU to take advantage of 64 bit capabilities, I just bought it because it was a damned good price and I <3 AMD.

---

### Post by aysiu on 2006-07-18
I'm not sure it's that easy. I think the plugins have to be compiled for your architecture (the one you have installed).

Since you installed 64-bit Ubuntu, I don't know if you can just use a 32-bit package with that.

You can, however, use 32-bit Ubuntu on your 64-bit computer.

Does that make sense? There may be solutions short of reinstalling, though. I don't use 64-bit, so I don't know what those are.

---

### Post by Roasted on 2006-07-18
Wait, how can you tell I am on a 64 bit Ubuntu? What if I wanted to downgrade to 32 bit? Could I do that without a format? 

Basically, it's 1 way compatible between 32/64 bit systems/OS?

---

### Post by aysiu on 2006-07-18
> **Roasted said:**
> Wait, how can you tell I am on a 64 bit Ubuntu? From the error you got in Synaptic and the fact that the *flashplugin-nonfree* package can't be found, despite your having the correct sources.list. > What if I wanted to downgrade to 32 bit? Could I do that without a format? 

Basically, it's 1 way compatible between 32/64 bit systems/OS? Again, not having any experience with 64-bit myself (I don't have a 64-bit computer), I don't know the answer to that.

You may want to post a new thread--something like, "I have 64-bit Ubuntu. How can I downgrade to 32-bit?" Best of luck.

---

### Post by Roasted on 2006-07-18
For the record I greatly appreciate the patience and information you have given me throughout this thread. ;)

---

### Post by aysiu on 2006-07-18
> **Roasted said:**
> For the record I greatly appreciate the patience and information you have given me throughout this thread. ;)
I appreciate your patience. The whole time you were probably thinking, "What does this guy think I am--a moron? I copied and pasted that command. I already followed that tutorial. Why isn't this working? Argh!"

I should have thought of the AMD64 thing sooner.

---

### Post by Roasted on 2006-07-18
Nah. I'm trying to be as level headed as possible when learning this. I've had 9 years of Windows experience so I knew coming over here to Linux would be difficult.

Anyway, going to switch gears here and try to avoid making a new thread (I know most forum mods don't appreciate multiple threads being made). SOOOO...

FOR THOSE OF YOU WHO ARE FAMILIAR WITH 64 BIT SYSTEMS. After reading this thread WHAT can you tell me the problem is? I'm a new Linux user so if I have to repeat any steps I did earlier in this thread I'll do it. Is there anyway to install this 64 bit plugin without trouble? How about the 32 bit one? Can the 32 bit plugin run on a 64 bit processor? I would think it would, but then again I'm a Windows user and know Windows had no trouble... ](*,)

---

### Post by aysiu on 2006-07-18
[This thread](http://www.ubuntuforums.org/showthread.php?t=202537) just got updated, and you may find it helpful.

---

### Post by Roasted on 2006-07-18
I'm seriously on the verge of just going back to Windows. I did what the directions said for Java and I just got an error message. ](*,) ](*,) ](*,) ](*,)

---

### Post by Roasted on 2006-07-18
After downloading this recommended later in the thread:
Flash : [http://www.debian-multimedia.org/poo...0-0.0_i386.deb](http://www.debian-multimedia.org/poo...0-0.0_i386.deb)

I got this error:
[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-PackageInstaller-flashpl.png[/IMG]

---

### Post by aysiu on 2006-07-18
Before you go back to Windows, consider (I know this sounds like a big step) reinstalling and using the 32-bit version of Ubuntu. It works on a 64-bit computer, and you won't be limited in terms of standard software (like Flash).

You're going to hurt yourself trying to get Flash working on AMD64.

My two cents.

---

### Post by Roasted on 2006-07-18
Can you give me a link or something for the 32 bit linux?

Also, my Linux is on a separate hard drive. Is there anyway I can install it RIGHT NOW and just choose to overwrite everything? I was just going to go into Windows, download it to a blank CD, then try to boot from the CD like I did the first time. But can I skip that and just reinstall/reformat in 1 shot? Not sure how Linux works with that... :confused:

---

### Post by aysiu on 2006-07-18
> **Roasted said:**
> Can you give me a link or something for the 32 bit linux? Sure, here's one:
[ftp://mirror.anl.gov/pub/pub/ubuntu-iso/CDs/6.06/ubuntu-6.06-desktop-i386.iso](ftp://mirror.anl.gov/pub/pub/ubuntu-iso/CDs/6.06/ubuntu-6.06-desktop-i386.iso)

> Also, my Linux is on a separate hard drive. Is there anyway I can install it RIGHT NOW and just choose to overwrite everything? I was just going to go into Windows, download it to a blank CD, then try to boot from the CD like I did the first time. But can I skip that and just reinstall/reformat in 1 shot? Not sure how Linux works with that... :confused: You will, in fact, have to download it, burn it to a blank CD, and reboot... but once you do that, you can overwrite the second drive.

If you think that's too much trouble, I would go back to Windows for now. Save Ubuntu for another time when you aren't in the middle of being frustrated.

---

### Post by Roasted on 2006-07-18
Friday night I'm going to the beach for a week. The monday after I come back I'll start school where I'll also be learning about Linux. I'll continue to get my feet wet until I get some more formal training, though. It's fun messing with new stuff, especially when it finally works!

Thanks for everything.

---

### Post by aysiu on 2006-07-18
No problem. I always advise taking it slow.

I think, though, after your 64-bit adventure, you'll find 32-bit to be a piece of cake.

---

### Post by Eric_T on 2006-07-19
I lacked a line in my sources.list... And I checked it several times without noticing... oh well, thanks for the help!

---

### Post by Roasted on 2006-07-21
WHICH repositories are okay to mess with? I updated the very first one in the list as well as the security updates one. I have like 10 repositories here... wasn't sure what was safe and what wasn't safe to mess with.

---

### Post by Roasted on 2006-08-01
Along with my above question, if I install plugins via Automatix, does Automatix take care of clearing up whatever repositories needed?

---

