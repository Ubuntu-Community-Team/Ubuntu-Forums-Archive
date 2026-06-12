---
title: "no gnome on USB stick"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by bogaerbr on 2008-05-19
Hallo,

I have Ubuntu 8.04 installed on my desktop computer. No problem over there (except that I still don't have flash playing in firefox 3)
Then I decided to install Ubuntu 8.04 on a USB stick , to be used on my laptop (compaq nc 6000)
When I start the Live CD, everything works fine. I do get Ubuntu 8.04 as on my desktop.
Then I decide to install it on my USB stick, reboot the computer.. at this stage I get as far as a login and I do get the desktop background for Ubuntu 8.04 (the Hardy Heron), but no pannels, nothing.. just the heron. 
No mouse clicks result in any action, neither...
So..
I installed Xubuntu 8.04 on the same USB stick. No problem ! I do get a fully functional Xubuntu booting from the USB stick. I install KDE, and again no problem : I do get Ubuntu started with  KDE, all right.
After I installed gnome on Xubuntu, I  get exactly the same as when I installed Ubuntu from the Live CD.
So It seems the 'gnome' environment does not want to be installed on my USB stick. Not yet.
Again : Ubuntu 8.04 (with the Ubuntu-desktop) gnome environment works OK from the Live CD.. so I do not think something is broken within gnome.. It just doesn't work if I try to install it on a USB stick.

Has anyone experienced the same problem ?
Has anyone some suggestion to make Ubuntu-desktop operational when I start from a USB stick ?

Bruno

---

### Post by DominicF on 2008-05-19
Hi, 

I've had the same problem and has been reported before.  The workaround was to press cntrl-Alt-F2 when you get to the blank screen and login in text mode.

$ cd /tmp/

and remove the .X0-lock file i.e. 

$ sudo rm .X0-lock

then startx

$ startx

When you get back to the Desktop yo'll need to enable automatic login

'System'-->'Administration'-->'login window', open the security tab, and enable automatic login  
(note this takes a long time for the screen to pop-up a few minutes)

Good luck.

---

### Post by bogaerbr on 2008-05-19
Hi !

Thanks a lot for your answer.
I did try it out, and ...
IT WORKS.

Only : each time I start up, I need to use the command line "startx"
It does not seem to remember the state of the computer with which I stopped.

Oh well ! Now at least I have got the Ubuntu Desktop.

Bruno

---

### Post by DominicF on 2008-05-19
Hi Bruno,

I don't remember the details behind this problem.  But to get past this issue of removing the lock file at each bootup you'll need to enable automatic login.

So, to recap:

Bootup remove the lock file, startx to bring up the Desktop, from the Desktop 'System'-->'Administration'-->'login window', open the security tab, and enable automatic login at this point  the fix is made permanent.  Next time when you bootup it should bypass the login screen and go straight to the desktop.

---

### Post by bogaerbr on 2008-05-19
Hallo DominicF.

I guess I was just a little too impatient..
Indeed ! Everything went as you told me in your first answer.
Now the laptop boots with  Ubuntu 8.04 (Ubuntu-Desktop) from my USB stick.

Really glad that you were there to help.
Thanks a lot !

Bruno

---

### Post by billbear on 2008-06-08
I also encountered this. My solution:
Boot into XP from my internal disk.  Open VMware and create a virtual machine using the whole usb stick as its hard disk. The usb stick boots successfully in VMware because it is recognized as a HD rather than a usb stick in the virtual environment. Then update ubuntu. The bug's fixed by updating and the usb stick can boot a real machine now.

---

