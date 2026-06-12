---
title: "Black Screen Of Death Of Boot &amp; Shutdown!"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by myke on 2008-01-09
After facing and attempting various suggestions to fix the black screen of death of Kubuntu shutdown or restart, it was suggested I reinstall Grub which was easy to do thru Synaptic (way better than Adept even for KDE).    But now when I restart it, it comes up to the partition choice listing (between linux and winxp) and has something knew at the top "grub 2".  If it counts down in to that it launches into black screen of death immediately.  If I choose the first linux kernel as normal, the regular kubuntu splash loading screen goes thru the motions but once the horizontal loading screen is full, instead of going on to load the desktop, it defaults back to the black screen of death with a blinking cursor at the top left hand corner of the screen.  It will boot into recovery mode with a command prompt but I don't know what the hell to do with that.

Clearly now not only can I not shutdown or restart without freezing but I can't boot fully to begin with.   I'm having to get on the forums from my XP side.    I SHUDDER at the thought of a fresh install yet again for a minor problem (what should be) so is there anyone I could boot from the live cd and copy any necessary files to my portable hard drive and then boot into XP and put them into my Linux partition as I can read and write from my XP side to my Linux side and vice versa??    IF so, what do I copy from the live cd and when I boot back into XP, where do I put it in my Linux partition?  

I'm assuming I need to find all of the original Grub files?   Perhaps the shutdown files as well and maybe I could fix that too??

Any body know how this might be possibly fixed???   I'd sure appreciate the help.   I'm forced to work in Windoze in the mean time.

---

### Post by dabl on 2008-01-09
Short answer -- video driver problem.  To prove it, when you've got the black screen with the blinking "_" in the top left corner, press Ctrl-Alt-F1 and observe the login prompt awaiting you.  Sometimes it's just Alt-F1.

Longer answer -- you don't need to reinstall the OS, but you do need to set up your X server with a correct video driver for your graphics card.  Search this forum with the make and model of your graphics card, and that should get you started down the path to a fix.  :)

---

### Post by myke on 2008-01-09
OK -- I looked in my device manager under XP and the video driver is listed as "Intel(r) 82852/82855 GM/GME Graphics Controller". 

I searched the forums about that but nothing.   Any ideas how to get the driver and how would I install it since I can't get into the system?

---

### Post by dabl on 2008-01-09
A search of the forum turned up this -- it would appear the solution is in the next to last post:

[http://ubuntuforums.org/showthread.php?t=651131](http://ubuntuforums.org/showthread.php?t=651131)

:)

---

### Post by myke on 2008-01-09
Also ... if it's the video driver ... why was it working before and is now only doing this after a reinstall of Grub?   and what is the Grub 2 that is appearing in the partition list at boot up?  If I choose that, instant dos type prompt.  If I choose the main Linux kernel like I normally would, it boots up thru the boot up screen at least prior to the black screen of death.   Grub 2 shouldn't even appear in the partition list!   It should have the linux boot up and linux safe boot up along with windows xp.  Now this 'grub 2' is at the top of the list and does nothing anyway.

OK ... I read the thread above and here's my question?   How do I get to all of that info when I can't get to a terminal?  Do I log in to the linux kernal recovery mode?   Will those instructions work from there?

---

### Post by dabl on 2008-01-09
> **myke said:**
> Also ... if it's the video driver ... why was it working before and is now only doing this after a reinstall of Grub?  

dunno -- perhaps there was something more than just a Grub reinstallation?  What problem prompted the Grub reinstallation?

> 

 and what is the Grub 2 that is appearing in the partition list at boot up? 



I have no idea -- not only have I not personally seen that, I don't recall seeing any forum posts mentioning a "Grub 2" on the boot menu!

> 

 If I choose the main Linux kernel like I normally would, it boots up thru the boot up screen at least prior to the black screen of death. 

What you are describing here is a normal boot, with broken X server.  So, fixing the video driver should result in this boot option producing your graphical login prompt, and then your desktop.

:)

---

### Post by myke on 2008-01-09
ok ... so i'll try that based on the other thread .... but where do i get it where i can use "sudo gedit" to pull up the text editor and fix the driver as described in the other thread?   Again, I'm not command line saavy but was ok using it with a terminal after the desktop was loaded.   I just don't know how to fix this without the desktop being there at all.   Do I boot into recovery mode?   Try it from the prompt on the black screen of death?

---

### Post by dabl on 2008-01-09
The command line is definitely intimidating.  You can do basic text editing with "nano", which is slightly easier than "vi".  So, log in at the Command Line Interface (CLI), aka "DOS-like prompt", and then enter ```
sudo nano /etc/X11/xorg.conf
```

at the bottom of the nano screen are all the commands there are.  Scroll down to the "Device" section, change the driver name, and do Ctrl-O to save your edits and Ctrl-X to exit the editor.  The little "^" mark means "Ctrl".  You'll need to restart the system for your changes to be effective (gurus will note this is not literally true, but we're going for quick results here).  To restart your system from the CLI, enter ```
sudo shutdown now -r
```

:)

---

### Post by myke on 2008-01-09
> **dabl said:**
> The command line is definitely intimidating.  You can do basic text editing with "nano", which is slightly easier than "vi".  So, log in at the Command Line Interface (CLI), aka "DOS-like prompt", and then enter ```
sudo nano /etc/X11/xorg.conf
```

at the bottom of the nano screen are all the commands there are.  Scroll down to the "Device" section, change the driver name, and do Ctrl-O to save your edits and Ctrl-X to exit the editor.  The little "^" mark means "Ctrl".  You'll need to restart the system for your changes to be effective (gurus will note this is not literally true, but we're going for quick results here).  To restart your system from the CLI, enter ```
sudo shutdown now -r
```

:)

Ok, dabl ... I went for it and followed your instructions.   I got to CLI and then got to the nano screen to pull up the /etc/x11/xorg.conf file as you said.  I think I may have found the problem.  That file was easily able to be pulled up the way you explained and all of the commands were at the bottom of the nano screen as you said.

Here's the problem ... the xorg.conf file was BLANK!!!   there was nothing on it to edit.  I don't know how it got erased but some thing surely caused it to.   How to I get the entire file filled back in???

Also, to answer the question as to why I reinstalled Grub ... I did so following one of the threads suggestions (of many) that stated that a user was able to fix the restart/shutdown freeze problem that started this whole process by reinstalling grub.   So I did.   I also did some research and found out Grub 2 is a developmental version of Grub that is not yet the standard.   I uninstalled and reinstalled the exact version that I already had so I don't know how it got in there and I don't know what file to edit to get rid of it off of the partition chooser screen at start up.

---

### Post by sdb2028 on 2008-01-09
Just checked into this thread, am having a simular problem. When you typed "sudo nano /etc/X11/xorg.conf" into the command line, did you inadvertantly type "x11" lower case? the folder is case sensitive, you must type "X11" exactly.

---

### Post by myke on 2008-01-10
I did type it lower case at first and realized that was likely an issue so I tried it again and was able to pull up the file.  Unfortunately for me, this solution wouldn't work as it already had the correct driver listed.

I really believe I have a major problem with Grub.   It got worse after this last night and I'm having to post from my work computer as I can't access either my K/Ubuntu or my WinXP partitions.  Nothing.  Nada.

See this thread where I described the current state of my poor laptop:  

[http://ubuntuforums.org/showthread.php?p=4108485#post4108485](http://ubuntuforums.org/showthread.php?p=4108485#post4108485)

---

