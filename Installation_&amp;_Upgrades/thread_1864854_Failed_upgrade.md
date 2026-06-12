---
title: "Failed upgrade"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by littlebird on 2011-10-19
I have to note that the first part of this debacle is entirely my fault, now I just need to figure out what to do...  I was upgrading from 11.04 to 11.10 when I decided to move my laptop to the desk (I have a dead battery), blithely thinking 10 feet would be a short enough distance to not interrupt the process.  Wrong!  I had to restart the system, and was confronted with mass chaos.  I could not boot up the system at all, instead I was greeted with lines of code that I still can't decipher (and can't get the computer to repeat). 


I was eventually able to start the computer in 11.04 safe mode and get a little bit of the repository repaired using FGLRX, but that only got me a very small victory.  Instead of colored lines when I attempted to boot normally, I was given a textual description of what the GUI was supposed to be doing, but only partially.  After it checked the battery state, it just stopped.  Now when I try to use recovery mode, I am dealing with the same colored line problem I have with the live CD. 

I have tried booting from a live CD of 11.04 (which worked when I first installed the system) so I can back up my data and do a fresh install, but am again confronted with the blank screen with colored lines after the splash screen loads.  Oddly, I can hear the start-up music, so everything must (?) be working back there?  I have also tried a USB boot with the same symptoms.  

This is probably relevant before I ask for suggestions.  I had the colored lines problem when I was originally trying to switch from Vista to Ubuntu on the currently dead laptop, but I stumbled across a set of keystrokes in one of the forums that allowed me to access the disk perfectly.  Any ideas on what that might be?  I never had graphics issues until this disaster happened either, so I don't think its a graphics card issue.  Hopefully I didn't fry the hard drive...  

I really need this computer up and running ASAP, so any help would be seriously appreciated.

---

### Post by wnelson on 2011-10-19
Go to terminal and login as root.

First run: apt-get dist-upgrade -f

if that fails 

Run: dpkg --configure -a

either of these will install the cached applications.

Walt

---

### Post by littlebird on 2011-10-19
Hi Walt, 

Thanks for the suggestions.  I went to try them, but am still unable to access the terminal because of the screen issues.  I think that needs to get fixed before anything else so I can actually tell the computer what to do at this point.

---

### Post by owiknowi on 2011-10-19
looks a bit like there's something wrong with your screen(connectors) or video chip or card, which is rather nasty with laptops.
first you could try to remove the battery and run the laptop only ac power, just to see what happens.
broken batteries can cause problems too.

---

### Post by littlebird on 2011-10-19
> **owiknowi said:**
> looks a bit like there's something wrong with your screen(connectors) or video chip or card, which is rather nasty with laptops.
first you could try to remove the battery and run the laptop only ac power, just to see what happens.
broken batteries can cause problems too.

I removed the battery and booted from the USB drive, and still no luck.  What I don't understand is that until yesterday I was having no graphics issues of any kind.  Is there a workaround for this?  I have a 1st gen. Dell Inspirion 1501 with an AMD Sempron processor and PCI-x16 card (don't know what brand, as I cannot access the laptop at the moment).  Hope that helps!  Thanks, 

Andrea

---

### Post by mörgæs on 2011-10-19
Before suspecting the hardware I would begin with a fresh install. There is a link below explaining how - especially the part about boot options is relevant to this problem, I guess.

---

### Post by owiknowi on 2011-10-20
a fresh install or booting from live mdeia shouldn't differ that much in this case, afaik.

since the live medium didn't give any improvement, you could consider installing the os with which the computer was shipped (windos?) originally.
thus you'll know for sure the hardware is ok.

---

### Post by mörgæs on 2011-10-20
> **owiknowi said:**
> a fresh install or booting from live mdeia shouldn't differ that much in this case, afaik.

A life boot is a good beginning, but a real installation gives more options of experimenting with drivers (some of which require a reboot).

---

### Post by littlebird on 2011-10-20
This laptop was a hand-me-down, and I can try getting the original discs from my sister, but I doubt she still has them.  The computer was running Vista before I installed 11.04 five months ago, and had no problems until this distro upgrade disaster.  Booting from a live CD of 11.04, 10.04 or Mint for that matter gives me the same set of problems, and I can't boot from a USB stick either.  The one thing I have been able to run successfully is a memory check, which said the system was running normally.  It seems to be an OS issue.  

Have there been any fixes for live boot problems like this?  I have come across them before in the forums, but no one seems to know what to do with them.   I really need to back up my data (I lost 5+ years of documents when my previous hard drive failed, and I don't want to go through that again...).

Thanks for all of your input.

---

### Post by littlebird on 2011-10-20
> **mörgæs said:**
> A life boot is a good beginning, but a real installation gives more options of experimenting with drivers (some of which require a reboot).

I have checked this forum, and I will need to give it a more in  depth look, but it doesn't really address the boot issues I'm having.

---

### Post by jimbo99 on 2011-10-20
Try alt+ctl+f1 to see if you can get a terminal login prompt.  Then try the commands recommended in the responses.

---

### Post by owiknowi on 2011-10-21
if nothing else works, and **you don't have any personal file stored on it**, you should consider to wipe the hard drive and starting from there.

you can read, for example, [here](http://www.owiknowi.org/indexmorebits.html), how to go about.

---

### Post by littlebird on 2011-10-21
> **jimbo99 said:**
> Try alt+ctl+f1 to see if you can get a terminal login prompt.  Then try the commands recommended in the responses.

Ok, this worked, I was able to access the login prompt.  The first set of commands that Walt gave me to update the broken upgrade failed - "no such kernel exists".  Then I was automatically sent into normal mode again.   At least I could input something this time, that's progress!  I wonder if I should boot from the hard drive instead of a live CD and run the same commands, perhaps I will get better results.

I'll get back with my findings.  Hopefully this will help my solve this, otherwise I'm back to square one again.

Thank you everyone for your input, I really appreciate it.

Andrea

---

### Post by littlebird on 2011-10-21
> **wnelson said:**
> Go to terminal and login as root.

First run: apt-get dist-upgrade -f

if that fails 

Run: dpkg --configure -a

either of these will install the cached applications.

Walt

Ok, so I have been able to upgrade to 11.10 using alt-ctrl-f1 to access the terminal and run dist-upgrade -f (yay!) but when I try to boot normally I am still running into the problem I had before.  No more colored lines (unless I try booting from a CD), but I still don't have a GUI.  I tried running dpkg --configure -a hoping that would fix the problem, but I get an error message: "unable to access dpkg status area: Read-only file system".  

I'm closer to a functional computer now, so that's a plus.  I noticed that flash didn't install, and I was getting some really weird code as it was installing about (not kidding at all, I took photos) Wells Fargo, the Japanese Government, Equifax, and Trans Union.:confused:  I think there might be something more seriously wrong than a simple interface issue.

---

