---
title: "Feisty &quot;black screen&quot; at startup, Help!"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by kealan on 2007-05-01
Just upgraded from edgy to Feisty, it worked fine after the initial system restart initiated by the installer.  Now it will go to an unresponsive black screen after the ubuntu logo and before the login screen.  ctrl+alt+backspace and ctrl+alt+f1 have no effect.  I can start up in recovery mode and use the exit command to open gnome and it works fine.  I tried: sudo dpkg-reconfigure xserver-xorg.  It restarted into gnome once and then reverted to the black screen with the next restart.  

I have an HP with 2.53 GHz P4 and integrated graphics 845 GL chipset

---

### Post by kealan on 2007-05-02
No one has any Ideas?!

---

### Post by blazercist on 2007-05-02
delete "splash quiet" from the boot line.

---

### Post by kealan on 2007-05-02
I saw no "splash quiet" in the boot line, so I deleted every instance of "quiet splash".  It seems to have worked.  I don't understand why it worked, but thanks for the help.

---

### Post by blazercist on 2007-05-02
splash quiet/quiet splash same thing, usplash has been known to cause this issue on many systems including my ATI x800 Pro.

---

### Post by Fr33d0m on 2007-05-02
What boot line?

---

### Post by slink on 2007-05-04
Hi, 

I just ran into same trouble 

[http://ubuntuforums.org/showthread.php?t=432556](http://ubuntuforums.org/showthread.php?t=432556)

Do I need to:

- Boot-up computer
- If GRUB menu is hidden, press Esc to enter the GRUB menu
- Select Ubuntu, kernel 2.6.12-8-386 (recovery mode)
- press e
- delete every instance of "quiet splash"
- press b to boot

?

Or do I need to read more info about editing Grub, before?

---

### Post by brion@cbkidder.com on 2007-05-06
This did not work for me on my Dell Inspiron 1100. After upgrading from Edgy to Feisty the laptop screen goes black.

---

### Post by slink on 2007-05-07
I'd like to clarify if my problem is the same as yours since I did not upgrade but installed. 

My "symptom" is a black screen with the spinning wheel after the startup progress bar and total unresponsiveness to keyboard (no ctrl-alt-F2). Is that the same as you both kealan and [email]brion@cbkidder.com[/email] ?

I edited my 'Login Window' prefs before the trouble began. Could that be related?

---

### Post by brion@cbkidder.com on 2007-05-07
Yes, slink that is the same problem I had. I was running 6.10 with no troubles at all, and when I let the update manager install 7.04, the laptop booted once normally but from the next time on I got the black screen. The only way I could successfully boot is to the command line from the oldest selection in GRUB.

I looked at the xorg.conf file but it looked the same as before, so I don't know why Feisty/7.04 made it impossible for X to launch. I needed to use my laptop so I eventually did a fresh reinstall of 6.10, which is a major pain because then there's the updates, install the printers, beg and plead the wireless networking to work, and so on.

From reading the forums, it appears that you and I are by no means alone with this problem, which makes me wonder how this didn't get addressed in Feisty during beta; perhaps the Feisty release was premature.

---

### Post by slink on 2007-05-07
I was given the advice to restore any backuped xorg.conf ( [http://ubuntuforums.org/showthread.php?t=432556](http://ubuntuforums.org/showthread.php?t=432556) ) but there were no previous /etc/xorg.conf.bak1 files, and I did not manage to edit Grub, so I decided to fresh install too. 

Now I'm afraid that could happen again. 

I edited my 'Login Window' (accessibility tab and login theme) prefs before trouble so I suspect the problem is related to that.

---

### Post by Heratiki on 2007-05-09
Same here... Inspiron 1100 after a fresh install of 7.04 (Alternative CD) it went through the install fine but when it came to it's first boot it went to a black screen after the Ubuntu Boot screen and before the Login Window.   The keyboard doesn't work and it seems as though the machine is locked up.  I can't quite remember how to kill the Ubuntu Boot screen so that I can see what's going on so if anyone wants to help me there it would be great...  Also has anyone been able to get it to boot into recovery mode with this problem, I haven't tried but just thought since I'm reinstalling now I would give it a go...

---

### Post by slink on 2007-05-10
Do you Heratiki and [email]brion@cbkidder.com[/email] recall what configurations did you change before that first reboot+trouble?

Did you edit the 'Login Window' prefs?

---

### Post by localetc on 2007-05-10
I am getting the black screen too but during the installation!  I can't even begin the installation.  The sound and video initiate, then the mouse locks up and the screen goes black.  This is on an inspiron 1000.

---

### Post by chuckygobyebye on 2007-05-10
I have the same problem on installation.  Deleted quiet-spash and got the verbose install steps.  Seemed to all get on the HDD and started to boot.  Got one step after starting Gnome and then went all black.

However,

I'm using an older CRT monitor and after it blanks out the montior's OSD brings up a frequency out of range message, which suggests that the black screen is being caused by Gnome switching to a video mode that isn't supported by the hardware, which is pretty lame really.

---

### Post by Dan Hammond on 2007-05-13
This blacklogin with a spining cursor isexactly my problem too is there anyone out there who can help before i do a fresh install???
Please...?

---

### Post by bbskeelz on 2007-05-23
i tried installing xubuntu and ubuntu on the 1100, both cases, on a fresh boot, will hit the blank screen, but if i go into shell first then startx, it's fine.  any advice?

---

