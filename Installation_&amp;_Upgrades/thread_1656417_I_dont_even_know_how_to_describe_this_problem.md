---
title: "I dont even know how to describe this problem"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by yakove on 2010-12-30
I am trying to install Ubuntu Maverick 10.10 on a computer. Instead of waisting time trying to describe what is going on... Im simply going to show you what is happening. This is at the first boot and happens no matter what I do. I can not get into any of the Init's or command prompts. It happens every time I try to install Ubuntu with this computer. I have the same or similar result with Xubuntu, regular ubuntu, and Kubuntu. It also does not matter whether I'm using an alternate disk, regular install disk, or a minimal install disk and it also does not matter what CD/DVD burning drive I choose to burn the disk with. In fact its not the CDs/DVDs because I have been able to upgrade two other computers with the set I am using.



As you can see above It is the login screen for a standard installation of Ubuntu 10.10. Except it does not have any text on the login screen, and shows no mouse. instead of a mouse it has a black box which moves around where the mouse should be and can operate in a limited capacity as a mouse.


I was able to once do a blind login. this is the result above. I know its a little dark but it is the same as the login screen. The mouse is a black box. Also the where there should be text, there is none. not on the menus or in them, and when I attempt to go to Init 1 through 5 it throws me back to the login screen. I also am unable to access the command prompt... 

Anyway I can get a better definition as to what is wrong here? The computer was running 7.04 before I tried to load 10.10 and while Running 7.04 it had no issues. All the hardware also appears to be sound and in working order RAM/HDD/CPU... the only thing I can think of is to try a different CD/DVD reader...

---

### Post by yakove on 2010-12-30
apparently my images did not come through. lets try this again

The first image of the login screen is here

the second image of the desktop is here

If this doesn't Work Ill just put them in the attachments...

---

### Post by Sef on 2010-12-30
I am thinking that you had a bad install. Boot into the Live CD, instead of going into Ubuntu, go down to 'Check Disk for Errors' (or something similar) and see if the disk has any errors on it.  If that is ok, run the live CD and see if you still have the same problem, but I suspect that it is hardware related due to your trying other versions of ubuntu and coming up with the same problem.

---

### Post by grahammechanical on 2010-12-30
How are you trying to install? Are you using an upgrade or are you trying a fresh install from a CD? Have you chosen to format the root partition? Sometimes leftover configuration files cause conflicts. Have you tried using a Live CD?

regards.

---

### Post by yakove on 2010-12-30
I allways do a backup with a fresh install... call me a quaint but I just think its cleaner. well at least most of the time.

---

### Post by yakove on 2010-12-30
Ok I finally found something meaningful. While attempting to run Xubuntu in a Live CD, I got this error.

(preocess:383) GLib-Warning **: getpwuid_r(): failed due to unknown user id (0)

it then stands there for about 5 minutes and then attempts to get into the X session, It then freezes indefinitely...

Since at this stage the information could only have come from the optical drive... Im going to try to swap optical drives, see if that makes a difference...

---

### Post by yakove on 2010-12-30
optical drives did not seem to make a difference while loading the live version of the CD. same process error on load. It was different in that it did give me the same mouse and text issues as if I actually installed Ubuntu. Im going to go find a copy of UBCD and see if it is the dang HDD I allready tested this, but it wouldnt kill me to do it again from the other optical drive)...

---

### Post by yakove on 2010-12-31
OK, HDD is working just fine... I used UBCD/Drive Fitness Test to confirm that... also Ive wiped the entire drive using a hard drive scrubber... also UBCD... Im going to attempt removing the graphics card and running from the internal graphics of the MOBO... if anyone is still reading this thread, and has any other options, Im all ears... and Seriously, Im personally out of Ideas...

---

### Post by yakove on 2010-12-31
ok so I cant get into a LiveCD with the other graphics card... to sum it up

RAM = good
HDD = good and clean
Processor = cant imagine that be the problem considering it ran all these tests without issues.
Graphics card = Works on another computer, on top of that, multiple different GCs give the same or similar result...
Image = nothing wrong with the CD image
optical drive = same issue over multiple optical drives, all of which work well on other systems and have installed ubuntu 10.10 on those systems...

at this point im about to say its the MOBO, Im hesitant though, as it has performed flawlessly through the testing process... Does anyone else have any other ideas as to why this is not working for me?

---

### Post by yakove on 2010-12-31
after visually examining the mother board and video card I have discovered blown capacitors on both... I have placed two pictures of the blown caps...

---

