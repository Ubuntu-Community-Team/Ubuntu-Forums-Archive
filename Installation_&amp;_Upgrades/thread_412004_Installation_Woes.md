---
title: "Installation Woes"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by bagadonitz on 2007-04-17
I'm trying to install ubuntu on an AMD dual core system (4600+ AM2).

I will be going onto, to start the only drive in the system.  This drive currently has Windows XP 64 bit on it.  I have tried to erase this using Seagate SeaTools and I don't know if that was successful or not.  Doesn't matter much as it was exibiting the same behaviour before and after I did that.  <update>  I just checked and the XP installation is still in place and bootable.  I will try to trounce it entirely to see if that helps </update>

I have the CD burned and it seems fine.  Everything loads up from the CD and when I get onto the desktop and click the install button, I get through all the dialogs up until you select where it is to be installed.  It finds the disk, moves the slider to suggest a partition and then it either freezes or completely reboots.

Any idea what could be going on here?  Trying to install the 6.10 that the download page suggested for my 64 bit system.

---

### Post by ajgreeny on 2007-04-17
I'm assuming you want to get rid of windows XP completely, and if that is so you could do the following:-
Try running the live CD, and then instead of installing, run gparted and delete the windows partition(s) at that point, and then install ubuntu using the whole disk.  If you haven't tried using the whole disk already in your install procedure, as opposed to the free space option, it may be worth trying that before you delete windows, just in case that works.

---

### Post by bagadonitz on 2007-04-17
I was hoping to dual boot but I gave up on that.

Using the 7.04 Fiesty installer I blew away the XP altogether.  The installer went fine and I'm able to get into the Ubuntu desktop and do things. 

HOWEVER, random reboots and lockups abound.  I'm getting pretty frustrated with this.  I don't even know where to look to see what is going wrong to ask for help.  The logs screen locks up the system and or causes a reboot every time I touch it.

---

### Post by bagadonitz on 2007-04-17
Well I'm just about done with this.

I have memtested my memory (it is fine) run the long diagnostic test on my hard drive (it is fine).  All my temps are well below worry zone.  All my cards are seated.

I'm guess this is a video card driver that is locking up as it always happens when the screen is rendering.  I'll try and find an update to that but it looks like I'll have to dish out for Vista tomorrow which absolutely guts me.

Thanks for the help.

---

### Post by bagadonitz on 2007-04-17
Anyone have any ideas on this?  Very frustrating for my first foray into Linux.

---

### Post by bagadonitz on 2007-04-18
Not the type to give up, I kept trying.

After 12 or so coasters, I was able to get a clean burn of the non 64 bit version of the desktop Feisty Fawn release.  It installed perfectly and I've been exploring ever since.  I've been able to set up my old Brother laser printer on it without issue and I have it shared and can use it to print from my windows box.

So far I love the interface.

Next, set up some shares.  I'm a Java developer that works from home, 6000 km from the office.  I VPN into the windows network at work.  The hope is I can get my intellij IDEA installed in ubuntu, find an oracle tool, and set up shares.  From my windows box I'll use tortoise to pull our svn repository into the share on my ubuntu box and developer from there.  The cube interface is fantastic and will come in very handy for development.  Is there some way I can get it to let me access the top and bottom faces of the cube so to speak?

Thanks

---

