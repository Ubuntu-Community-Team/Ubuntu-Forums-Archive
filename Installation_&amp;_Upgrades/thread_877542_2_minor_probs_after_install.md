---
title: "2 minor probs after install"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by philipearle on 2008-08-01
Just got done installing 8.04, Ubuntu detected all my hardware and for the most part everything is good.  Two minor annoyances maybe you guys (and gals) could help me with.  First my number lock won't come on after booting.  Second, my wireless light won't come on, usually shows blue when connected, but doesn't light up at all.  It still works, though.  Minor annoyances, but maybe they can be fixed.

My system is a HP laptop...HP Pavilion dv8000 series, (8235 to be exact).  It is a dual core processor running 1.8 GHz, 2GB Ram, GeForce Go 7400 video with 512 MB memory.  Any other info that is needed please let me know and I will provide it.  

Thanks in advance, Philip

---

### Post by K2712 on 2008-08-01
For the numlock issue:

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

As far as the wireless LED goes, I'm sorry but I have no idea.

---

### Post by LeoSolaris on 2008-08-02
What type of wireless do you have?

My Intel Wireless N in my Inspiron did that, and the fix was rather easy...   just snag the backports from the repo. (should be in the Universe repo, and findable with Synaptic rather than the normal Add/Remove) I do not recall all of the steps at the moment, but I am sure you can find the steps on the forums with a quick search. I'm about to hit the hay, otherwise I would search and just drop a link in for you.

Good luck and welcome to the wonderful world of Linux...  the DIY OS.

Leo

---

### Post by philipearle on 2008-08-02
hey again..

tried to edit the file, but it was giving me an error telling me i did not have permission to edit or save file, was logged in as root, so don't know about doing that.

and about the light, i will search the forums for details, 


thanks for the help, both of you

---

### Post by philipearle on 2008-08-02
Got the wireless light working...thanks again

As far as the numberlock key not working at startup...I followed the instructions in the link, and when i try to save the file it comes up with an error telling me that i do not have permission to change this file.  I have logged in as root in a terminal window.  I installed Krusader, which is a file manager that logs you in as root.  In both cases I get the same error message as above.  Any ideas??

Thanks, Philip

---

### Post by xen-uno on 2008-08-02
try ...

```
sudo gedit /etc/gdm/Init/Default
```

in Terminal ... it works here

---

### Post by philipearle on 2008-08-02
OK, I got it working.  Had to go through Nautilus to be able to save the changes.  All is working.  Still trying to learn Ubuntu, but there is a thick Windows fog in my brain.  

Thanks again for all the help, these forums are great.

---

### Post by keheikev on 2008-08-02
Yes I think you have to use the super user do sudo command to make edits to some parts of the file system.:popcorn:

I have been fixing the same thing with the gnome desktop.

---

### Post by Bucky Ball on 2008-08-03
> Yes I think you have to use the super user do sudo command to make edits to some parts of the file system.

If it doesn't work the first time, always try 'sudo' before your last code and go again (in a terminal, press the up arrow on your keyboard and it should paste the last command you typed, then just add sudo at the front). And don't panic phillipearle, the fog will soon lift and you'll start to feel more calm, relaxed, imaginative and part of a community ... have fun (you will!). As long as you remember one important thing: Linux is not Windoze! Go with the flow and keep an open mind. There is plenty of help here if you get in a fix but hey, that is what DIY is all about). :)

---

