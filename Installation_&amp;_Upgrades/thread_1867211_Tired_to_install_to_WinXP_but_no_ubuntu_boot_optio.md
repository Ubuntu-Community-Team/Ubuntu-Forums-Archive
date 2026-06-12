---
title: "Tired to install to WinXP but no ubuntu boot option on restart"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by castlefox on 2011-10-22
I've downloaded ubuntu-11.10-desktop-i386 torrent two times and I keep getting the same problem on every install.

After completing the download I mounted the ISO and installed ubuntu 11.10 through wubi.  I gave it 9gigs to use up.  I have a 40gb HDD but 14 are free to use.  Defraging the drive has not made any effect.  

After the wubi install process a window does not poop to where I can choose to boot into windows xp or ubuntu 11.10.  So I have not been able to completely install ubuntu or try out 11.10 on this hardware yet.

Any ideas ?

---

### Post by scania_gti on 2011-10-22
Wubi - not good idea. Just make partition for Ubuntu, and install. Less pain, more pleasure :)

---

### Post by castlefox on 2011-10-22
Well im trying to figure out of this is a bug I should file or if Im doing something wrong.


I also dont have enough space on my external HDD to back up everything like I should if Im gonna dual boot and all that.

---

### Post by bcbc on 2011-10-22
Right click on My Computer, Properties, Advanced tab, Startup & Recovery settings. 

Check the 'Time to display Operating systems' is not zero, if it is set it to 10.

If that's not the issue make sure there is an Ubuntu entry in the "Default OS" drop-down box (don't set it to Ubuntu). If it's missing, then post the contents of you C:\boot.ini

---

### Post by subhadip_sky on 2011-10-23
I faced problems with the installation file downloaded from torrent. Use the official Ubuntu download page to download the ISO. Might help.

---

### Post by castlefox on 2011-10-25
bcbc- I did the firs thing you suggested and it worked like a charm.

+10,000 pats on your back.     You are awesome.


subhadip_sky - I always grab the torrent from the office webpage but I will keep that in mind

---

### Post by Rubi1200 on 2011-10-26
If the problem is resolved, please mark this thread Solved using the Thread Tools near the top of the page.

---

