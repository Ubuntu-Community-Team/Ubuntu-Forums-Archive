---
title: "Blank screen after ugrade restart"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by tangofoxtrot on 2011-01-22
[FONT=Times New Roman][SIZE=3]I had a working ubuntu 8.04.x system. I ran the update manager to upgrade to 10.04.1 LTS. Everything seemed to run fine up to the point where it needed a restart. Upon restart, it spews out a stream of log messages, changes the font of the log messages already displayed, and then the screen goes blank and the system does not respond to keyboard or mouse. It appears as if the system is trying to set up the monitor and messes up.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]If I ESC into grub after BIOS boot, I have the option of booting two different kernels: 2.6.32-27-generic and 2.6.24-28-generic. The original ubuntu 8.04 kernel was 2.6.24-24-generic(though I did do some updates – might that be the 24-28 kernel?). [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Booting the 32-27 kernel results in the behavior described above. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Booting the 24-28 kernel produces a stream of log messages that scroll past to fast to read and drops into ash. One of the last messages is: !ALERT /dev/disk/by-uuid/ xxxxxx does not exist -which is true because there is very little in the /dev directory.[/SIZE][/FONT]

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums :)

what graphics card do you have installed?

you can try reconfiguring the graphics from safe graphics mode or recovery mode and see if that helps (as this sounds like a graphics issue):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tangofoxtrot on 2011-01-23
[FONT=Times New Roman][SIZE=3]Hi, and thanks for responding. My system has a Nvidia GeForce4 MX420 graphics card.[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I’m not sure how to do what you suggest. When I boot the [COLOR=black]2.6.32-27-generic kernel out of grub, I get the blank screen non-responsive system behavior. It does not leave me in a responsive shell. I’ve tried various combinations of kernel args like: single, init 3, init 1, debug, initcall_debug to bring the system up in a Vanilla text mode and get a better handle on where things are getting funny. All give me the same end behavior - nada. Is there another way to get into a safe graphics mode?[/COLOR][/FONT][/SIZE]
 
[COLOR=black][SIZE=3][FONT=Times New Roman]I can bring the system up with the old 8.04 Live CD, but I don’t think it gives me access to the files on the HD. So, I don’t see how to do mv and dpkg-reconfigure without a working shell. Perhaps my original post was confusing on that point. The other kernel dropped me into a shell, but in a system where there wasn’t even a /dev/disk directory.[/FONT][/SIZE][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3][COLOR=black]I’m assuming that things are going wrong around the time the X-windows starts up. But, the boot up messages go by so fast, I really can’t tell what’s going on. I sort of get the impression that the boot up is more-or-less ok up to the point where the graphics go west.[/COLOR]
[/SIZE][/FONT][/COLOR]

---

### Post by Rubi1200 on 2011-01-23
Do you have a menu entry for Recovery Mode for the kernel in question?

If yes, select it and drop to a command prompt and try the commands from there.

If no, when the normal entry is highlighted press "e" to edit.

Find the line that ends with quiet splash (navigate using arrow keys) and remove it typing nomodeset instead, then "Ctrl" + "x" to boot.

---

### Post by tangofoxtrot on 2011-01-25
[FONT=Times New Roman][SIZE=3]Hi Rubi1200, sorry I took so long to respond &#8211; I&#8217;ve been coming up to speed on the kernel boot process.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I tried the recovery boot as you suggested, but I end up with the same blank screen behavior. With quiet and splash removed and initcall_debug added, the last lines I see before the screen goes blank are:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]BEGIN RUNNING SCRIPTS local_bottom[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]DONE[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]DONE[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]BEGIN RUNNING SCRIPTS init_bottom[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]DONE[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]These lines remain visible for 5 or so seconds, then the font changes and after another 4 seconds blanks. The problem clearly happens after init starts the scripts. I can break into the system and get a shell if I include init=/bin/sh as a kernel parameter. However, this defeats the init process so I&#8217;m not seeing the same environment that exists when I boot without the intervention. But, there is probably stuff around that would show what does work. Can you suggest anything to look at that might be helpful?[/SIZE][/FONT]

---

