---
title: "Migrating from Windows XP - Specific software"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by DWk102 on 2007-07-28
Hi all,

I've decided I'm going to give ubuntu a try without using the LiveCD. My questions before migrating are software specific.

[LIST=1][*]When I set up WinXP under VMWare, can this installation of WinXP access the rest of the hard drives?[*]I have Remote Desktop set up in WinXP right now and access it from work. If I set up Remote Desktop in the VMWare installation of WinXP, will I still be able to run it?[*]I see there's a Remote Desktop for ubuntu. Do I need ubuntu in order to access it? If I do, what's the easiest solution in a WinXP-only office environment?[*]If I plug in a USB, will this version of WinXP inside VMWare be able to recognize and read the USB?[*]I use Opera as my main browser. How can I migrate my settings from WinXP to ubuntu's Opera?[*]From what I have read, there's no installation for Flash in Opera. Is there a workaround for this?[*]I have an Nvidia video card. Will I need to install some specific drivers in ubuntu?[*]I have a TV Tuner (LifeView TV) currently. Will it work correctly being ran inside VMWare?[*]I use remote control tools inside WinXP (VNC and Radmin). Will I still be able to access other computers using the software installed in the VMWare installation of WinXP?[*]I use NOD32 and Sygate to protect my WinXP installation. Will I need some sort of security software inside the VMWare version of WinXP?[*]I also use powerful (or usually referred as memory hogs) software like Adobe Photoshop, Adobe Audition, Adobe Captivate, and Guitar Pro. Any feedback on running this software through VMWare?[*]Will PowerDVD work correctly through VMWare's WinXP?[*]Will CD/DVD burning software, like Nero, run & burn correctly?[*]Last but not least, I hardly do any gaming. However, I do enjoy a weekend poker play. Any alternatives?
[/LIST]

Numbers 1-8 are the most important ones and if I become comfortable that they can be resolved, I'd definitely be moving.

I'm not thinking of having these solutions forever though. I do know of alternatives. However, I'd like to do the migration smoothly. Eventually, I might stop using them overall. For now, I'd like babysteps :)

Thanks for any help you might provide - and please include as many links as you can :)

---

### Post by jmaryinchina on 2007-07-28
1. Your vmware machine and your hosting machine will see each other through a virtual network interface. Therefore, if you use samba services on Ubuntu you'll be able to dedicate a folder to be shared between your windows in VMWARE and Ubuntu. Also Ubuntu will be able to see and write in your shared folder in your virtual windows.
     Samba usually doesn't work out of the box, it's like this because you must always adapt it to the particularities of your network and this can't still be detected at install.

2. Yes, and you can also run RDesktop directly from Ubuntu. It's called Terminal Server Client.

3. The remote Desktop Server of Ubuntu is VNC. So you need to use a VNC client. It will work from any platform.

4. Can't answer, I haven't tried yet. What I know is that you shouldn't care because Ubuntu will usually recongnize what you have plugged and will make it easy to use. It seems you want to use windows as before but inside linux. If you have solutions in Ubuntu, why to use the windows ones ?

5. The answer to this must exist on opera forums.

6. There is. It is documented on opera web site.

7. Yes, with your nvidia graphic you can install the nvidia drivers which are restricted. Anyway, your graphic will work out of the box. The nvidia proprietary drivers can be installed after.

8. Your TV tuner might run with Ubuntu directly.

9. You can do that from Ubuntu directly.

10. Keep your antivirus. For firewall and Co, your Linux box can act as firewall protecting your vmware install.

11. Those soft will run fine in vmware (I'm not sure for Guitar Pro) if you have enough memory. I suggest to have 2Gb at all for your computer.

12. Try and give us your feed back.

13.I usually use Gnomebaker, and it's perfect.

14. ?????

---

### Post by DWk102 on 2007-07-28
Awesome reply, I really appreciate it :D

Just a few more questions on the answers you provided:

1. By any chance do you have a link for this? I'm very interested in it
2 & 3. I guess I'd be just running the VNC client externally and I'd be able to see VMWare as well, right?
4. Awesome, I figured that would be the same, just needed confirmation
5 & 6. Will search - thanks.
7. What do you mean by restricted?
8. Would this be running generically? I read [http://www.tomshardware.com/forum/230282-50-tuner-ubuntu](http://www.tomshardware.com/forum/230282-50-tuner-ubuntu) and found out about MythTV ([http://mythtv.org/index.php](http://mythtv.org/index.php)). Would this be the type of solution I'd be looking at?
9 & 10. Great, thanks
11. I have 1GB - I don't run them that often, but I'm sure I'll be able to find good alternatives (Well, I already have used GIMP in Windows, so that's one down)
12. I certainly will
13. I'll try it
14. Heh, poker software would be the explanation for that

Thanks again

---

### Post by DWk102 on 2007-07-28
For # 5, how do I migrate the opera.ini config file?

Thanks again

---

### Post by kalekseishaken on 2007-07-28
There are 2 ways to use VMWare under Linux, 1) create a virtual hard disk that resides on your Linux partition or 2) use an existing WindowsXP installation. I use option 2 you can find the instructions for using a 'native' install of Windows at (Note: because of activation issues, this will only work with a 'retail' version of WindowsXP);

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)


I chose to do this since I needed to Windows to be able to access both physical hard disk of my computer an all partitions on each hard disk.

VMWare does handle my USB ports with no problem. I have been able to run my USB printer through VMPlayer with no problem.

The big problem for me had been creating the second VMDK file for my second hard disk and getting VMTools to install. To be honest I never got the complete VMTools to install, but since all I needed from VMTools was the SVGA driver and the mouse it worked fine.

Under Ubuntu, I ran NTFS-3g to access all of my NTFS partitions and added the 2 FAT32 partitions to the 'fuse' group. The only caveat to this approach is that you should never access the actual Windows OS partition from Ubuntu while the VM is running. You can access all of the other partitions no problem at all.

Ciao . . . C.Joseph

   "A promise is nothing more than an attempt
    to respond to an unreasonable demand."

[http://blog.tlerma.com/](http://blog.tlerma.com/)

A Windows professional's view of entering the World of Linux

---

### Post by DWk102 on 2007-07-28
Heh, no turning back!!! (well yes, there's a turning point, but don't want it)

Right now I'm installing ubuntu :)

I guess the real questions will come in later... in some mins :)

---

### Post by DWk102 on 2007-07-28
Ok, installing Flash in Opera is being a problem. I've searched and tried many different options. Is there a specific procedure I need to follow for it?

---

### Post by Patrick-Ruff on 2007-07-30
I had some trouble with guitar pro when I tried it.  if you use the huge sound libraries that aren't midi apparently they don't play . . . but the program will run in wine.  

though, last time I tried it the fonts were all messed up . . .

---

### Post by wthanna on 2007-07-30
As a native linux alternative to Guitar Pro, try Tux Guitar [http://www.tuxguitar.com.ar/](http://www.tuxguitar.com.ar/)  it works real well and reads your guitar pro files

---

### Post by DWk102 on 2007-08-04
Awesome. Before anything, thank you all for your responses. Having support in difficult times is always gratifying :)

Almost all issues have been either solved or are unnecessary to solve. If you could help me with the following, it'll be greatly appreciated.

1. Even though I have migrated Opera completely, the only thing I'm still lacking is Flash. I've gone over quite a few ways to install Flash (e.g. installing the Firefox plugin into it), but without any good result. Any help in this would be greatly appreciated.
2. I have enabled Remote Desktop and have tried it successfuly. However, is it possible to block the computer when it's being accessed through Remote Desktop?
3. I need to install no-ip.org's DUC (Dynamic Update Client). However, it's not a .deb or .rpm and it has been a while since I installed something manually. Any help to install this I'd thank a lot.
4. I have a Logitech MX500 mouse. I've searched for ways on how to use its 5 buttons, but haven't tried something that works. Is there a special driver somewhere for this?

Again, thanks for all the help. And for the software you have recommended, I'm in the process of testing it.


Instead of using VMWare, I'm using Innotek Virtualbox - it's certainly easier to use than VMWare, and runs fast enough.

---

### Post by Bakon Jarser on 2007-08-26
Just switching to Ubuntu myself and was wondering how you did with powerDVD.  I need a dvd player that does surround sound.

As far as poker software goes, Pokerstars works in Wine.  I haven't messed with it too much but it got a gold star rating.

---

### Post by DWk102 on 2007-08-29
For DVD playing, I was using Kaffeine. It certainly works like a charm for that purpose. I can't comment on the surround sound, since I don't have any yet.

Pokerstars did work well, except when the window tried to get focus (it doesn't work as it does in WinXP).

---

