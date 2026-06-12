---
title: "New User Here, How Do I Install Ubuntu?"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by mlyons16 on 2007-08-29
Hello,

I'm currently using Vista, it's nice but I want to explore an alternative OS.

What is the easiest, least invasive way for me to go about using Ubuntu?

Also, I would like an easy option of switching back to Vista, either permanently if I don't like Ubuntu, or occasionally (for instance, if I like Ubuntu, but wan't to dabble in both OSs)

I appreciate the anticipated assistance and I thank you in advance.

---

### Post by merlinus on 2007-08-29
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

-merlin

---

### Post by Pumalite on 2007-08-29
Download a Live CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), do md5sum on iso, burn at 4x, and boot from it. It should allow you to experience Ubuntu without an installation. If you like it, then you can install. Come back for instructions if you decide to install.

---

### Post by siralphred on 2007-08-29
You can try out the live cd but that has its limitations, such as you cannot save anything as it will be gone after you remove the cd so i will suggest you dual boot and play with it for a  while and then make up your mind, if you are using vista  go to run and type: dskmgmt.msc  then create a partition for ubuntu by shrinking the vista partition, then restart with ubuntu in the cd tray and remember to choose : Install on largest continuous free space....that will install on the partition u created and you will be done dont worry ubuntu will recognize the vista....good luck

---

### Post by Pumalite on 2007-08-29
If you decide to install, make sure you use the Vista partitioner; otherwise Vista won't let run anything in your computer.

---

### Post by glotz on 2007-08-29
One thing I've heard people compliment is wubi. It will install Ubuntu inside Windows for you to try. [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by mlyons16 on 2007-08-29
alright, Well I've heard of the live cd concept before... So, just download from where it says Download Ubuntu... I remember coming accross a help article, where can i find this?

---

### Post by Pumalite on 2007-08-29
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by Bakon Jarser on 2007-08-30
> **merlinus said:**
> [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

-merlin

Excellent link merlinus.  It helped me out a lot.

---

### Post by merlinus on 2007-08-30
Glad it was useful..  There is a wealth of information at that site, and also this one:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I have learned lots and lots from both.

-merlin

---

### Post by mlyons16 on 2007-08-31
Hello,

We'll I really liked that site that you provided... The one at:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I think those instructions were nicely laid out

Let's say I use the live cd, then install, etc etc... and then I don't want any trace of Ubuntu left on my computer. I only want the Vista partition, no more Ubuntu..

How do I go about doing this. I haven't installed Ubuntu yet, as I'm looking to explore my options out before I get myself in.

---

### Post by rharriso on 2007-08-31
If you have trouble getting the ISO to work. Just order it from osdisc.com. They sell different distros for a dollar, about 5 with s and h

---

### Post by mlyons16 on 2007-08-31
burning the iso isn't my concern, It's say after ive burned and installed it... and then i want to wash my hands of it, how do i do that?

---

### Post by glotz on 2007-08-31
You can run it off the LiveCD. That way there's nothing to uninstall.

Or if you do install it, then just repartition and remove the partition you had Ubuntu on.

---

### Post by mlyons16 on 2007-08-31
Okay, and how do I go about repartitioning and such?

---

### Post by ubuntu27 on 2007-08-31
> **mlyons16 said:**
> Okay, and how do I go about repartitioning and such?

When you install Ubuntu, you will partition the drive ("make room" in your hard disk). So when you want to delete Ubuntu, you got to do the same thing. Only instead of creating a new partitions, you delete it.

---

### Post by 2manydrugsago on 2007-08-31
Another new user here. I have a server and  i have installed Kubuntu and  need help. What are the exact command line instructions to install/unpack/whatever on Ubuntu 2.6.15-26-server? or am I missing something?

---

### Post by Pumalite on 2007-08-31
If you have downloaded Kubuntu Server; this is an iso. An iso you burn to a CD as 'Image' and then boot from it.

---

### Post by glotz on 2007-08-31
2manydrugsago, see [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

---

### Post by 2manydrugsago on 2007-08-31
I am a new Kubuntu User with very limited Linux / Unix Experience.  I just Installed the ISO of Kubuntu 6.06.1 LTS Dapper Drake - Kernel 2.6.15-26-Server.

I installed the ISO and rebooted the System.

What now?  I can find no instructions detialing the exact command line prompt commands to enter to install and activate any GUI Interface, KDE, Gnome, X11Rxx etc????

Help!!!!

---

### Post by Pumalite on 2007-08-31
A Server is command line only, but if you want a GUI, you can do this: sudo apt-get install gnome-desktop

---

### Post by 2manydrugsago on 2007-08-31
I just installed the newest Ubuntu Desktop version on a DELL PowerEdge 4400 Server  ...everything went fine....the GUI started and worked fine. When the system was shutdown and restarted it just displayed a Linux Command Prompt....NO GUI....

What do I do to get the GUI to always restart?`

---

### Post by Pumalite on 2007-08-31
Try startx first. If not, then: sudo dpkg-reconfigure xserver-xorg. Accept most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by mlyons16 on 2007-09-03
Hello again...

I'm posting from Firefox in Ubuntu! 

Thanks for all the help... actually the most helpful resource was:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It's great... now that I've done this once, I could easily do it again, and now I have my very own LiveCD!

Linux is awesome. I have to say... yes, It's a little intimidating on how to install it, but hey... I love learning new things and all I needed were clear resources, and I've found them! Thanks again everyone for all of your help.

Only problem I had was getting my Wireless Card to get on my network properly... It's fine now as I'm obviously posting, but it did take some playing around with. This interface reminds me a lot of Mac OS X, but it somehow feels far superior. It's like a mix of Mac and Windows... what a glorious happy medium.

---

### Post by glotz on 2007-09-04
Welcome to the land of the penguin dude! :D

---

