---
title: "Installing on 256mb ram"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by raja.aydina on 2007-11-30
I have an old pc, 
Centrino 1.5 GHz; 256mb ram, and 60 gb hdd,
I tried installing gutsy, the live cd will load up, but when I do install, it would freeze up. I know the ram is minimum, but is there any way to install it without loading the live desktop, so it wouldn't freeze up. 
please help.
thanks

---

### Post by PmDematagoda on 2007-11-30
On 256Mb of RAM even if you install Ubuntu using the Alternate CD you will still face problems with the installed Ubuntu OS as it may not be able to work to it's full potential using only 256Mb of RAM.

I suggest that you install [Xubuntu]("http://www.xubuntu.org/get") which will work better than Ubuntu on your PC.

---

### Post by mellowd on 2007-11-30
Or fluxbuntu.

If you really want ubuntu then get the alternate cd

---

### Post by cyberbuff on 2007-11-30
Does your installation freezes when it comes to "Scanning mirrors"? If so, do disable the netrwork. [Some ppl are having probs with it]. 
I think the minimum requirement of RAM is 256Mibs. So it *should* work. As mellowd said give AltCD a try. that may help you...

---

### Post by Herman on 2007-12-01
It will help a lot if you use a [GParted -- LiveCD]("http://gparted.sourceforge.net/") to do your partitioning first and most importantly make a Linux swap area somewhere on your hard disk, about 1 GB should be more than enough.

Next time you boot the Live CD, it will find your swap area on the hard disk automatically and use it for a 'slow lane' for the RAM. Slower moving items from the memory will be sent to the swap area temporarily, freeing your real RAM for all the hard working, faster jobs.
You will notice a huge performance boost and your Live CD should be able to complete the installation at a normal speed.

Regards, Herman :)

---

### Post by raja.aydina on 2007-12-01
What happens, is that it takes a long time for the live CD to load the desktop and the mouse freezes. Does gutsy work well on 256mb? How to I get the alternate cd, I will try the alternate CD, otherwise I'll put xubuntu. Thanks for the help

---

### Post by raja.aydina on 2007-12-01
nvm, i found the alternate CD

---

### Post by wolfen69 on 2007-12-01
i recommend the xubuntu alternate cd.

---

### Post by Herman on 2007-12-01
Well I have a computer here running Gutsy okay with only 127 MB of RAM. 

When I installed, I only had 64 MB of RAM, I used the 'Alternate' CD.
I added another RAM card since then.
The 'Alternate' CD can perform a minimal install in low memory mode with as little as 32 MB of RAM, according to what I have read.

Ubuntu Gutsy will work for me with 127 MB, but it's really slow. it will run some applications okay, but others it chokes on, for example, Gnome Partition Editor is a little too much for it, and slows it down to a snails pace.

I have XFCE desktop (Xubuntu), and that works a lot better, and I also have IceWm desktop installed and Fluxbox.
IceWM is a little quicker than XFCE so I use that quite often and I like them both.

I want to get some more RAM for this machine and I can install up to 512 MB if I can get the right memory modules. Then it will run Ubuntu reasonably well.

Even 256 MB of RAM is a lot of RAM compared with 128 MB, and should run Ubuntu Gutsy okay. (Maybe not fast, but okay).
A lot depends on other things about your computer too, like CPU cache memory and things like that. Some computers will still work when they don't have very much RAM a little better than others can.

Regards, Herman :)

---

### Post by RedSquirrel on 2007-12-01
If you don't get the speed you were looking for with Ubuntu (GNOME) or Xubuntu, you could try a minimal installation with a light window manager such as Fluxbox, IceWm, or Openbox...

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Herman on 2007-12-01
I agree with RedSquirrel in the post above, actually, it was those two links that I used as my install guides when I installed Ubuntu in this particular computer.

I changed one of my 'Alternate CD' installation pages to illustrate the installation part of the process, to make it easier for people to understand how to use the 'Alternate' CD.
So if anyone wants to see how I did mine, they can take a look here, [Windows98SE+Ubuntu Gutsy Gibbon]("http://users.bigpond.net.au/hermanzone/p2.htm")

Regards, Herman  :)

---

