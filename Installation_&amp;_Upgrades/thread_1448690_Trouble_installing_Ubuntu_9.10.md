---
title: "Trouble installing Ubuntu 9.10"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by clskinny on 2010-04-06
I decided to give Ubuntu a try but I am having problems with the install.  I am new to this venue but I am somewhat tech savy.

The problem computer
MB  DFI nf3 250
HD Maxtor 300gb SATA
CPU Athlon 64 clawhammer 3200
Ram 2gb(2x1gb) DDR 400
Video card Nvidia 6800gt

The install hangs at i386_start_kernel 

When this happens the caps lock and scroll lock button flash on and off in tandem.

I tried installing both the i386 and AMD version via CD, DVD and USB boot and I get the same problem every time.  I confirmed accurate burns by installing Ubunut inside of other functions OSs.  The box will still boot up to the existing XP install that is already on the HD.  I also tried to install on a IDE HD and I hit the same problem.  I tried removing both sticks of ram with no luck.  I can't remove the GPU as the MB doesn't have a onboard output.


Any input would be helpful.

---

### Post by rcaca0 on 2010-04-06
I'm new to this also so I may not be too much help but have you tried to see if the Live cd works with your computer?

---

### Post by clskinny on 2010-04-06
Giving that a whirl right now also downloading the an older version 8.4 I think.

---

### Post by rcaca0 on 2010-04-07
Also just in case you run into this, when I installed Ubuntu 9.10 on my main computer I had to load it with the safe video mode then install the drivers for Nvidia.  
 
One other thing, are you trying to make a dual boot system?

---

### Post by clskinny on 2010-04-07
I want to do a clean install and wipe everything off the drive.  Also The only option I have is normal mode.

---

### Post by clskinny on 2010-04-07
I tried installing 9.10 on a different box and the installation was successful when I install that hard drive into the problem box I get the same error.  It hangs on start and the last line is i386_start_kernel

---

### Post by rcaca0 on 2010-04-07
When installing it you should have see some keys at the bottom F1-F6 if I remember right.  There you should see the safe video driver mode and other options.  

Did you try the live cd?  Just in case you didn't find it is in the menu, I think it reads,"run Ubuntu without installation", something like that.

---

### Post by rcaca0 on 2010-04-07
Also I am assuming that when you are talking about moving the hard drive from one box to another you are talking about two different computers.  I am also going to assume that you are not trying to run the same OS from one computer to another without reloading it.

---

### Post by clskinny on 2010-04-10
I got everything installed apparently it didn't like 2 cd rom drives on the same IDE channel.  Everything is up and operation and now I am doing file migration.  I have hit another road block though.  Based on the advise of a co worker I formatted the drive to ext 4.  The problem I encountered is that I can't copy the files from my external drive to the newly formatted ext4 drives.  I can access everything on the external but it doesn't allow me to paste them over.

---

### Post by rcaca0 on 2010-04-11
I don't know how much help I can be but I'll try.  Is the external HD on ethernet, usb, or something else?  Does it see the HD in the OS and just can't move files into it?

---

### Post by ubun2warrior on 2010-04-11
Why don't you try logging in as root and then try to copy and paste wherever you want.
Logging in as root:
Open the terminal> type sudo passwd> enter your password> enter a new password to login as root> then log out> type root in the user name> type in the new password that you created.

---

