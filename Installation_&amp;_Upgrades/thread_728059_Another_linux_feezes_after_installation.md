---
title: "Another linux feezes after installation"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by zo8890 on 2008-03-18
I wanted to ask if anyone has any idea what this error message is before my ubunbtu 7.10 OS loads.  I did an alternate CD install on a Pentium IV 2.6, 1gb RAM, 60GB Hard drive, not sure what the mother board is, but i have a ATI Radeon 9250 PCI.

I keep getting an error message right before the ubuntu loading screen comes up, which the OS seems to bypass just fine, but after the loading is complete it just stays on a blank screen, not receptive to ctrl+alt+f1 or anything, so I couldn't bring up a command line.

Error looks something like this  :

Cannot allocate resource region 0 of device 0000:00:002

On top of that when i try to do a memtest86, it freezes at the 3rd test...I had it running all last night. 

I think I've looked at just about every post on the load up freezes and nothing has seemed to work yet.  Was wondering if a brave Samaritan could help a new Ubuntu seeker!

---

### Post by rillip on 2008-03-18
Can you boot from the live CD?  That might let us look at the error logs and better figure out what is happening.

Eidt: Actually, you must be able to boot from the alternate, which should do fine too.  Try looking in /var/log/boot.log if you have one, dmesg, and the xorg files, see if any errors jump out there.

---

### Post by zo8890 on 2008-03-18
How do I check to see what error messages I am getting?  How do I get to the /var/log/boot.log to see?

---

### Post by zo8890 on 2008-03-18
I just ran the LiveCD with safe graphics mode, and entered startx at the command prompt.  This is the error I received:

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

---

### Post by Furiattl on 2008-03-18
Check the Bios.
Is you Radeon AGP or PCI? If it's AGP check the bus: *2, *4 or *8
Check the aperture size (set it to 64 or 128Mb)
If you can manage to run the *sudo dpkg-reconfigure xserver-xorg* try selecting the visa driver and some resolution that you are sure of (800x600)?.
Is it a CRT screen or an LCD one?
Good luck.
I have a Radeon 9250, it runs ok with Ubuntu but can't make the TV out working.
For what I can see so far the graphics drivers are one of the weakest parts of the system.

---

### Post by zo8890 on 2008-03-18
It's a PCI card and I run this system on a CRT, a gateway.  I'm not sure where to put in the command that you suggested, should I put it in after I get safe-graphics mode started, or before one of the lines at startup?

---

### Post by Furiattl on 2008-03-18
Did you check the Bios settings?
Windows seems to be more tolerant.

I don't know man. Try running the command in the low-graphics mode then, then ctrl+alt+backspace.
I've been playing with my gfx drivers a lot latelly and found out that the visa is quite safe bet.
For what I experienced do not try the fglrx driver.

---

### Post by zo8890 on 2008-03-18
I'll give a try when I get my next chance ( should be about 3 hrs)  and I'll get back on to let you know what happened.  But what you're saying is to run it in safe-graphics mode and then when I get a command prompt to put in...

?

---

### Post by Furiattl on 2008-03-18
type it in the terminal 

applications- accesories- terminal

---

### Post by zo8890 on 2008-03-18
Oh, I might misunderstand, but I don't have a working copy of any OS on my comp anymore.  I've installed Ubuntu on the hard drive and wiped out windows.  Now I can't get anything working.  Very frustrating :( 

I was understanding that the applications- accesories-terminal was the path to the terminal in Ubuntu correct?  If that's the case...I can't get to it ><

---

### Post by Furiattl on 2008-03-18
Have you got the Ubuntu install CD?
It's less then half an hour to install it.
Does it not start from the CD?
I though you mentioned that it starts in low-graphics mode.

---

### Post by zo8890 on 2008-03-18
> Have you got the Ubuntu install CD?
It's less then half an hour to install it.
Does it not start from the CD?
I though you mentioned that it starts in low-graphics mode.


I have the Ubuntu 7.10 install CD
I have already installed it on the computer using the alternate CD, because the Live CD would not run.
Ubuntu does not start from the Live CD, nor does it start from the hard disk
The alternate (Text Based) CD allowed me to install, but when I attempt to restart my system it freezes.

---

### Post by zo8890 on 2008-03-18
As I said before, I haven't encountered an error of this specificity on the forums and I was wondering if anyone could lend their assistance.

---

