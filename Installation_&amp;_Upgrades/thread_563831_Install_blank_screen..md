---
title: "Install blank screen."
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by beanie0610 on 2007-09-30
I have a fairly new toshiba satellite a135. I tried to install Ubuntu a couple of weeks ago and got to the install screen, once past that a bunch of text pops up so fast its unreadable. Then it just goes to a blank orange background, not processing anything after that. I tried the text install as well and it worked. But when i log into ubuntu on my computer the same blank orange screen stays on the screen, not letting me do anything but move my mouse. plz help with any advice/instructions.

---

### Post by PmDematagoda on 2007-09-30
Could you post the specs of your computer?

---

### Post by Pumalite on 2007-09-30
[http://ubuntuforums.org/showthread.php?t=421157](http://ubuntuforums.org/showthread.php?t=421157)

---

### Post by PmDematagoda on 2007-09-30
But Pumalite that thread concerns sound, his problem is starting and even installing Ubuntu.

---

### Post by Pumalite on 2007-09-30
[http://ubuntuforums.org/archive/index.php/t-543262.html](http://ubuntuforums.org/archive/index.php/t-543262.html)

---

### Post by PmDematagoda on 2007-09-30
Pumalite that new thread you linked still doesn't solve his problem. I think we could advance better if we knew your laptop specifications beanie0610.

---

### Post by Pumalite on 2007-09-30
Somebody has to keep me straight.

---

### Post by beanie0610 on 2007-09-30
My laptop has the following specs:

120 gb hard drive
500 gb ext. hard drive(not installed with linux yet)
2.0 ghz processor(pentium m)
1 gb ddr2 ram

---

### Post by Pumalite on 2007-09-30
That's great, but you left out the most interesting part: graphics

---

### Post by beanie0610 on 2007-09-30
sorry about that. it just has a standard intel graphics media accelerator 900

---

### Post by Pumalite on 2007-09-30
Well, that means you need the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the green sign 'Start Download'
(You will need to configure your xserver at the end of the installation. Post back)

---

### Post by beanie0610 on 2007-09-30
I installed the alternate cd, and that is what lets me log in to ubuntu. But once i log in, i get the same problem that happened when i tried to install using the live cd. It just stays at a blank orange screen, not allowing me to do anything but move my mouse, and not processing anything either.

---

### Post by Pumalite on 2007-09-30
Try: 
Ctrl+Alt+F1 to get a command line (at the blank screen)
Report back if you get one.

---

### Post by beanie0610 on 2007-09-30
I do get a command line asking for my ubuntu login

---

### Post by h0ax on 2007-09-30
Try logging in with the command line and then run "startx"

---

### Post by Pumalite on 2007-09-30
Login with your username
your password, then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then startx
(Cross your fingers)

---

### Post by beanie0610 on 2007-09-30
in doing this, i get to a point where it asks me for a method for selecting the monitor characteristics. This point is after a long series of configuration questions about my mouse and keyboard etc. Should i be this far?

---

### Post by beanie0610 on 2007-09-30
And what should i do at this point?

---

### Post by Pumalite on 2007-09-30
Let the program select your monitor automatically and accept the default.

---

### Post by beanie0610 on 2007-09-30
When i do that i get to the next question about color/bit configuration. When i try to proceed it gives me a statement at bottom saying "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf20070930121330". it then leaves a space for me to input. Enter won't work, what should i input?

---

### Post by Pumalite on 2007-09-30
If 24 doesn't work, try 16.

---

### Post by beanie0610 on 2007-09-30
No matter which one i choose, it asks for an input at that point.

---

### Post by Pumalite on 2007-09-30
That's something only you can answer. It beats me.

---

### Post by beanie0610 on 2007-09-30
It doesn't let me do anything after that point, it needs some input after i choose 16 or 24.  Is there any significance in it displaying in text below the configuration window 'brandon@ubuntu:~$' then asking for input?

---

### Post by PmDematagoda on 2007-10-01
Okay, new plan, try logging into your account while in CLI(Recovery Mode), I'm not sure of the command you need to use, so could someone please provide that?

---

### Post by beanie0610 on 2007-10-02
Is it Ctrl+Alt+F1?

---

### Post by Pumalite on 2007-10-02
If you have a command line, you can input the command I gave you before.If it says: login:, then input your username and password. Ctrl+Alt+F1 is to get a command line when you do not have one.

---

### Post by beanie0610 on 2007-10-09
All my problems were solved by using the 7.1.04 upgrade disc instead of 7.04. The live cd worked just fine.

---

