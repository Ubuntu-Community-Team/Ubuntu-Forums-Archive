---
title: "Login and Everything After is Dog Slow"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by sivacrom on 2006-07-14
Hello everyone!

I am new to Ubuntu and have just installed it on my;

iMac DV
600 MHz G3
512 MB RAM

And I am right off the bat having a problem where everything works nice and fast until I log in.  Right after entering my password (this is in the GUI, BTW) the machine slows to a crawl, taking five minutes or longer to finish logging in with my mouse pointer hanging in spurts where it will sit unresponsive for about 90 seconds, then move to where it was positioned when I let go of the mouse last, then it waits there for 90 seconds or so, etc.  At some point, I can actually move the mouse about, but certain menu items just hang and god forbid I try to open an application lest it never finish opening.

Odd thing is, this happened about three months ago when I installed Fedora Core.  I gave up and installed Yellow Dog that time, but I'd rather get this solved.  Any ideas?

By the way, logging in at the command line in the BASH shell work just fine.

Thanks in advance.

---

### Post by jayemef on 2006-07-14
Did you try monitoring with top and seeing what's going on?

Log into your first virtual terminal (Ctrl+Alt+F1 and login) and start top (just type 'top' without quotes), and then jump back to X (Alt+F7) and try logging in. If you go back to your virtual term (Ctrl+Alt+F1 again), the most demanding items CPU-wise should be at the top of top.

---

### Post by sivacrom on 2006-07-15
Another thing to note - if I log in a the bash shell prompt (ctrl alt F1) and then activate the "startx" binary, a window session begins that is about what I'd expect in terms of responsiveness - windows open quick, applications launch, the mouse responds nicely.  I wonder if there's something about the login window that is causing this...

I have not tried "top" idea yet (great troubleshooting idea, though) - too anxious to use Ubuntu now that I have a work around!  But I will and thank you for the pointer regarding the toggle back to GUI with alt F7!  You have been very helpful!

---

### Post by linear on 2006-07-15
On the iMac G3, you need to disable dri in xorg.conf:

1. **Ctrl-option-F1** to drop to a terminal.
2. **sudo nano /etc/X11/xorg.conf**
3. Find the line that reads "load dri", and comment it out (put a **#** in front of it).
4. Save (**Ctrl-O**) and exit (**Ctrl-X**).
5. Restart Gnome (**sudo /etc/init.d/gdm restart**)

---

### Post by sivacrom on 2006-07-16
Linear - I thought you might be on to something.  But I have done this (albeit with vi, not nano), and now I get a very responsive mouse pointer against a black background.  I'm not seeing anything.

Jayemef - BEFORE I tried Linear's suggestion, with top I found that Xorg was hogging over 90% of the CPU.  (Now that I commented out the "Load dri" it's gotten under control, but as you can see, this hasn't solved the problem quite yet.)  I did some research online and found that a lot of people are experiencing similar response with NVIDIA graphics cards which I THINK I have in my G3...

---

### Post by sivacrom on 2006-07-16
No, I have an ATI Rage 128 Ultra (AGP 2x).  Scatch the Nvidia possibility...

My work-around from my second posting in this thread is also no longer working.

---

### Post by linear on 2006-07-16
Forgot to ask: what are HorizSync and VertRefresh settings in xorg.conf?

Try setting HorizSync to 60-60 and VertRefresh to 75-117.

---

### Post by sivacrom on 2006-07-17
Linear - Thanks for checking up on my progress.  The two settings you mentioned were (by default) already set up just as you suggested (HoriSync 60-60 and VertRefresh 75-117.  

I found some paragraphs on input devices having to do with a wacom tablet, which I most CERTAINLY do not have.  I commented out the paragraphs, then commented out reference to them towards the bottom of the xorg.cof file in a section whose name is escaping me (it's late).  I also commented out the entire section at the very bottom of the xorg.conf file pertaining to DRI, figuring it was useless because I commented out "Load 'dri'" earlier...

Whenever I try to startx, it's a grey screen.  If I just log in at the GUI, it's a black screen.  I always have my mouse pointer.  Sometimes, when starting up the machine or executing startx, I see the screen horizontally cut off at about one-third of the way down, but it always comes back to fullscreen.

Now, when I switch back to the CLI, I see the following messages...

(WW) ****INVALID IO ALLOCATION**** b:0xf0000400 e:0xf00004ff correcting
(EE) end of block range 0xefffffff < begin 0xf0000000
(EE) R128(0): No DFP detected

I googled the last error you see there and I can't find anything useful about it.  I'm hoping you have another toy in your bag of tricks...

---

### Post by linear on 2006-07-17
[LEFT]My bag of tricks is running low...
 
Hmm. The [Date Bug]("https://help.ubuntu.com/community/UbuntuDateBug"), perhaps?
 
Or - some other problem in xorg.conf. Can you post the contents,  or maybe try starting over:
 
**sudo dpkg-reconfigure xserver-xorg**
 
 [/LEFT]

---

### Post by sivacrom on 2006-07-17
The date is correct.  I did the reconfigure via CLI as you recommended and the problem remains.  I'm not going to play anymore.  Ubuntu rocks... if it will let you log in.  I'm on to a different distro to see if I can get a version of Linux working for me in the most basic way so I can learn the ins and outs of Linux.  Take care and thanks for your help!

---

### Post by defunktional on 2006-09-02
Hi,

I had the same problem on the same iMac. Only with 768Mb ram.
I tried linear's "comment out load dri" approach, and it works now.

Thanks!

---

