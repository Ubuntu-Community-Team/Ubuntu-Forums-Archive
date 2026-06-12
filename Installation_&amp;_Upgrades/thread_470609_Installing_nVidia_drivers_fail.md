---
title: "Installing nVidia drivers fail"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by notbitmonk on 2007-06-11
First, I'm new to this.  I just installed Ubuntu for the first time this weekend.  Everything went good, I really like what I see.  I have an nVidia GeForce 6600 256 MB AGP card which I want to use.  I checked the forums for some help installing the drives and found a very good guide on what to do.  The procedure failed because of an error that read that I do not have libc.  That computer is not connected to the internet (I do not have internet in my house) so I'm not able to download anything or try any of your suggestions until I go back to my house this afternoon.  I also tried following the instructions on the nVidia page (getting in to terminal an typing sh driver name) but then I got an error that it can only be run as root.  Can you provide some help?

---

### Post by LollYouSuckZor on 2007-06-11
Mabey.. You can copy the drivers you downloaded from Nvidias website on a CD? or MP3 player?  and manually install them from a console? CHMod the files, etc.  Not fun, but doo-able? Most of what you were trying wont work, because Nvidia drivers are hosted online, as you do not have an internet connection you cannot reach them.  Your only chance to get the drivers, though you can survive without them, you have to download them and copy them onto a portable memory, 'device' and place it on your computer... Other than that I suggest you get an internet connection. :D

How to become a root:

In the console/terminal, whatever your using, their both the same.  Type, 
```

sudo su

```

It will then ask for your password, Enter it, and you'll be a root user.

---

### Post by notbitmonk on 2007-06-11
Thanks for the reply.  I do have the drivers copied on my second hard disk.  My main hard disk contains the operating systems (XP and Ubuntu) and my second hard disk contains my work files, music, etc.  The path to the locations of the nvidia package is something like /media/Data Drive/Data/Applications/Nvidia.  When I get in the terminal I type cd "/media/Data Drive/Data/Applications/Nvidia" to change to the location of the package and then I type sh Nvidia-Linux-x86-1.0-9755-pck1-run (or something very close to it, I'm typing from memory).  That's when it says that it has to be run as root.

---

### Post by LollYouSuckZor on 2007-06-11
So login as root, and try it out, tell me how it goes.. :)

:
Oh sorry, I forgot, Try it when your at home. Lol, Sorry.

---

### Post by notbitmonk on 2007-06-11
That's the problem.  I do not know how to log in as root, I'm a newborn in the Ubuntu world.  I do not know what the heck is that I'm doing (what does sudo, sh, etc. mean?).  The post that I followed for installing the nVidia drivers is very good, I did everything the author said.  At the point when I was asked to to hit Ctrl-Alt-F1 I knew I was going away from the GUI but I didn't knew that there wasn't an easy way out (like exit or quit in DOS), luckily at the end of the post were the instructions to get back in to the GUI.  However I had restarted the machine because I couldn't see the GUI were the instructions were located.  I know I have to get back to the author and tell him the he should edit his post so that new users actually print the instructions or view them from a different machine (besides, the person also needs to know the location of the package and that the path is different from Windows).  This is one of the things I like about Ubuntu, the forums where everyone can get help and the fact that if something goes really wrong, I can reinstall in 15 minutes (I love that the systems loads very fast, it takes me longer to type the username and password that for the system to load).

---

### Post by akshayas1986 on 2007-06-11
A suggestion

Try to avoid chaging permanently into root by typing > sudo su because when you acquire root previliges you can do practically anything to the OS and any mistake can cause some damage to your OS.

If any command needs super user i.e. root's access, prefix the command with sudo. For example, apt requires root access to install file so type > sudo apt-get install <file_name>

About libc, libc is a very important library. And it is required to be updated quite often. You might have an plder version of libc. And with Ubuntu, nothing works without net connection..:(

---

### Post by notbitmonk on 2007-06-11
Thing about libc is that as I was going through the different areas of the desktop, I found a list of libraries and libc was there.  About the internet connection there is not much I can do.  I had to drop my dial-up service because the telephone lines are so bad that I wasn't able to get any data across (now I'm also dropping the telephone service because no calls go through).

To follow what you are suggesting, if I follow nvidia's intructions, I need to type sudo sh Nvidia...  Is this assumption correct?

---

### Post by akshayas1986 on 2007-06-11
Ya thats right.. But I doubt if its the Nvidia driver problem.. My knowledge is not great about libc and Ubuntu but if I am right, Ubuntu does not always give the latest version of libc. I faced some problems when I tried in install some softwares,and I am still not able to fix it.Example-Limewire :(

---

