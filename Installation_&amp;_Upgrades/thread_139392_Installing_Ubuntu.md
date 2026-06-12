---
title: "Installing Ubuntu"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by NeoGreen on 2006-03-03
I have a real problem, I downloaded Ubuntu to my computer (I am have a Dell L700cx with an intel celeron processor at 700Mhz and 27 gigs)which is running Red Hat Linux and I don't know were to go from here.  How do I install it?  I saved it in a file on my desktop and cant get it to run.  I am doing this right?  I am new to Ubuntu and Linux (I know a little about Red Hat).  Please help.

---

### Post by pestilence4hr on 2006-03-04
If you downloaded an .iso, you need to burn it to a cd and then reboot onto that cd.  Do you know how to burn a cd image?

---

### Post by NeoGreen on 2006-03-04
No, I don't can you tell me.

---

### Post by pestilence4hr on 2006-03-04
Your most user-friendly option is to see if k3b is installed and then go to tools->burn cd image, and point it to the iso.  Another option is to use the command line utility cdrecord..."cdrecord dev=x,y,z ubuntu*.iso", where x,y,z is determined from the output of "cdrecord -scanbus" or "cdrecord dev=ATAPI -scanbus".  But if you are new to linux, try k3b first ;)

---

### Post by Sherlock Holmboy on 2006-03-04
if you already have a cd burning program there will probly be an option to burn an "image" which is what an .iso file is

---

### Post by NeoGreen on 2006-03-04
Thanks for the input guys, I'll try it.  So after I burn the CD and reboot my computer with the CD in it, is should automatically start to install Ubuntu?  Oh, another thing, will it effect Linux Red Hat when I install Ubuntu?  What I mean to say is, if all goes well and I do get to install Ubuntu, what will happen to Linux Red Hat.

---

### Post by roachk71 on 2006-03-04
Hmmm... An excellent question.

Many distributions have a partition re-sizer, though I haven't encountered the option for this in the Ubuntu installer. If there is, it all depends on the free space of your ext2/ext3, reiserfs, whatever partitions, except NTFS and swap.

Be careful, though: be sure to leave yourself some free space on the old partitions, even if you won't be using them much (the system logs will still use space, along with configuration file updates, etc.) :KS

Ah! And in case there isn't a resizer, Knoppix can be downloaded and burned, which does have one!
You can find it here:
[http://www.knopper.net/knoppix]("http://www.knopper.net/knoppix")

...And open the the QTPartEd utility from its menu.

---

### Post by NeoGreen on 2006-03-04
Awesome, thanks for the input.:D  Oh, yeah will I have to install Knoppix first before installing Ubuntu?

---

### Post by pestilence4hr on 2006-03-04
Knoppix runs entirely from cd (i.e. there is nothing to install).  But you don't need to use knoppix to re-size partitions, when you install ubuntu and get to the "partitioning" stage, you can resize the partitions there.  Just select the partition you want to resize, and change its size.

But if you feel more comfortable using graphical interfaces, by all means use knoppix.

---

### Post by NeoGreen on 2006-03-05
I would like to thank all that have helped me on my problem.  I finally got Ubuntu up and running.  Thank You for your help and to tell you the truth this is the first website that I have encountered that has actually helped me.  Thank You my friends, I have finally found a home.  Now I can celebrate drinking up that bottle of Brandy that has been waiting for me.   I told myself I would get Ubuntu installed before the end of my weekend.  Now I can have a couple of drinks with old Mr Presidente. Again Thank You my Friends.   Ubuntu to you all.

---

