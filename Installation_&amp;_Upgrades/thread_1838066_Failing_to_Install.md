---
title: "Failing to Install"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by Xemnas2010 on 2011-09-02
When I tried to install ubuntu-10.10 I got to the the second window making sure I had internet connection, memory space, and ac power. when i click to install it just keeps loading, or looks like that anyway, it doesn't do anything after that.  I'm trying to install on an acer-aspire-one-netbook. installing ubuntu-10.10 netbook or desktop from thumb drive. Anybody know what my problem is or have a solution?

---

### Post by Stolgrove on 2011-09-02
Random comment, but I just replaced my busted harddrive in the same system. And am having the issue of it not installing all the way. Goodluck to you
Installing 11.04 as a standalone os
I will watch your post maybe we will end up with similar issues

---

### Post by mörgæs on 2011-09-03
Have you tried installing the alternate ISO?

---

### Post by Xemnas2010 on 2011-09-03
> **mörgæs said:**
> Have you tried installing the alternate ISO?

the first one i tried to install was 10.10-alternate from a friend, but in the end all I got was (cd drive not detected).

---

### Post by mörgæs on 2011-09-04
There is some advice here: 
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Especially boot options are important.

---

### Post by Xemnas2010 on 2011-09-09
field trip. Alright I went over these various boot options about the only thing I understood was that I might have a problem installing drivers for my video card during installation and to try "nomodeset" (sorry. ADHD does that to me). However when I install, my display doesn't match the pics in the pages. I get the ubuntu logo with a loading bar then it takes me to the desktop with a window asking for a language. I click forward going to a window telling me I need internet, power plugged in, and atleast 2gb of space. When I click to install the arrow turns into its little loading icon. The system doesn't freeze, it just doesn't go anywhere else. I've had it sit like that for a whole day and nothing. But the point is I have no idea how to enable "nomodeset".
If you could offer clear cut step by step instructions it'll help me alot. Lol. I'm sorry, I appreciate it though.

---

### Post by Hakunka-Matata on 2011-09-09
What system are you using now, to participate in this forum?  Ubuntu, or Windows?, or something else.

Have you tried the Ubuntu Release you're installing?  As in "Try Ubuntu without installing to hard drive"?

---

### Post by mörgæs on 2011-09-09
I have not found any help better than the ones I am linking to. Please read them carefully, and if something fails, please post again and describe the exact step where it goes wrong.

---

### Post by Xemnas2010 on 2011-09-23
N/A  Sorry, don't know how to delete a post.

---

### Post by Xemnas2010 on 2011-09-23
> **Hakunka-Matata said:**
> What system are you using now, to participate in this forum?  Ubuntu, or Windows?, or something else.

Have you tried the Ubuntu Release you're installing?  As in "Try Ubuntu without installing to hard drive"?

I'm working off of win-xp and no I haven't "tried" it. Could that be a problem? Oh, and Morgaes, this link is basically what I come up with to start. The desktop icons and quick launch icons are the exception. From here I click forward and the pointer changes to its loading icon, but nothing else happens. Now from this point of view how would I implement your other suggestions?

[http://www.google.com/imgres?imgurl=http://3.bp.blogspot.com/_JBHfzEovWs8/TMWkNAnJJ5I/AAAAAAAAAw0/tiwlLM6GjdE/s1600/3ubuntu10.10install-preparingtoinstallubuntu.png&imgrefurl=http://netgator.blogspot.com/2010/10/ubuntu-1010-installation-guide-and.html&h=768&w=1024&sz=378&tbnid=1ibCuAQLLQg8nM:&tbnh=91&tbnw=121&prev=/search%3Fq%3Dubuntu-10.10%2Binstallation%2Bpics%26tbm%3Disch%26tbo%3Du&zoom=1&q=ubuntu-10.10+installation+pics&docid=VIAoURBpwsKveM&hl=en&sa=X&ei=H4Z8TvbINoLosQKcttxC&ved=0CB8Q9QEwAA](http://www.google.com/imgres?imgurl=http://3.bp.blogspot.com/_JBHfzEovWs8/TMWkNAnJJ5I/AAAAAAAAAw0/tiwlLM6GjdE/s1600/3ubuntu10.10install-preparingtoinstallubuntu.png&imgrefurl=http://netgator.blogspot.com/2010/10/ubuntu-1010-installation-guide-and.html&h=768&w=1024&sz=378&tbnid=1ibCuAQLLQg8nM:&tbnh=91&tbnw=121&prev=/search%3Fq%3Dubuntu-10.10%2Binstallation%2Bpics%26tbm%3Disch%26tbo%3Du&zoom=1&q=ubuntu-10.10+installation+pics&docid=VIAoURBpwsKveM&hl=en&sa=X&ei=H4Z8TvbINoLosQKcttxC&ved=0CB8Q9QEwAA)

---

### Post by mörgæs on 2011-09-25
Let's first focus on getting it run from a live boot. Does this work, if needed with boot options?

Please also give a complete hardware description.

---

### Post by Xemnas2010 on 2011-10-07
Okay, I tried to install again and I noticed a little crash button I hadn't noticed before. It said PARTED_SERVER crashed. 
My hardware:
-ACPI Multiprocessor PC
-Hitachi HTS543216l9SA00
-2 Mobile Intel(R) 945 Express Chipset family
-Atheros AR5007EG Wireless Network Adapter
 -Atheros AR8132 PCI-E Fast Ethernet Controller
-2 Intel9R) Atom(TM) CPU N270 @ 1.60GHz

You also mention live boot. Are you talking about booting the desktop from my thumb drive? Cause I can get there, the problem is installing to my partitioned harddrive. Could I use C:/ prompt from there to get around this?

P.S. Sorry if I'm giving you a run-aruond. lol.

---

### Post by Xemnas2010 on 2011-10-10
I haven't been on in a few weeks, so I think my original thread is dead. I had some problems installing ubuntu-10.10 onto my Acer Aspire One Netbook. I've been getting help from the forums and a friend. Ultimately I'm where I'm at now. Apparently my installation is failing due to the program 'PARTED_SERVER' unexpectedly closing. I'm using a 4gb Kingston flashdrive with fat32 format, and trying to install on one half of my harddrive. I've read this is a common bug when installing from a flashdrive, and the answers I found were conflicting and not that easy for me to understand. One said to delete the partition from the drive, but I can't get rid of my windows xp either. Another said that it was a particular file that needed to be that wasn't working right. Other than that I'm clueless. I have access to the desktop and the terminal. Is there a way to get around this without losing windows? My friend suggested trying 'linuxmint' saying it was 'ubuntu' just better. But I'm gonna keep tryin til I run out of options. Please give me more options.

---

### Post by lisati on 2011-10-10
Threads merged

---

