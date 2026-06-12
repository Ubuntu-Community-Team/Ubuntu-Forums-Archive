---
title: "No Wizard"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by hijoe99 on 2008-09-11
Hi, I'm having trouble installing Ubuntu 8.04 on my Sony Vaio notebook.  What happens is after I start the installation of Ubuntu, I get no wizard to help me along.  Instead I get a command prompt screen.  A lot of text is displayed, but I'll point out what I think is notable.  It says:

Linux Ubuntu 2.6.24-19-generic #1 SMP

To run a command as administrator (user "root") use "sudo <command>"

See "man sudo_root"  for details

ubuntu@ubuntu:~$


I really have no idea what to do as I am lost when it comes to command prompt.  From all the Ubuntu installation guides I have read, I should be encountering a wizard after the installer progress bar finishes.

Sorry if this is hard to understand and thanks for your help.

---

### Post by fmartinez on 2008-09-11
Sounds like you got the system installed ok. It's probably not what you cause there's no GUI interface. Just a couple of questions to help us help you: 
- What is the name of installation you downloaded. ie: Ubuntu Desktop Edition, or Ubuntu Server Edition? The server edition doesn't come with a GUI interface which may explain why you booted straight to command line. 
- What are you system specs? You may not have enough RAM to run a GUI interface. 
- What's the purpose you installed Ubuntu Linux? Where you looking for a server? Where you looking for an alternative to Windows? 
- The command prompt where your at will not have a GUI interface. You will have to use command line tools to help you navigate through the system. 

Good Luck Post Back!!!

---

### Post by hijoe99 on 2008-09-11
It's called ubuntu-8.04.1-desktop-i386 and I downloaded it right off of ubuntu.com.  I'm sure I have enough RAM, I have 3gb right now and I'm using a Core 2 D at 1.7 ghz.  I'm also just looking for a Windows alternative.

Thanks for replying.

---

### Post by Junk_head on 2008-09-11
Hijoe: this is strange...what option did you choose on the ubuntu live cd booter?

---

### Post by fmartinez on 2008-09-11
OK well that sounds like the right install disk and like you have enough ram. At the command line type: 
```
startx
```
and post the output. This will attempt to start the GUI interface.

---

### Post by hijoe99 on 2008-09-11
This is getting kind of frustrating.  I tried the startx command as suggested and this is what came up.

```
Fatal server error:
xf86 MapVidMem: Could not mmap framebuffer (0xd0200000 , 0x0) (Invalid argument)
Waiting for x server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno104) : unable to connect to x server
xinit: No such process Cerrno 31 : server error 

Ubuntu@ubuntu: ~$
```

Thanks for the help so far.  Any new ideas?

---

### Post by hijoe99 on 2008-09-11
> **Junk_head said:**
> Hijoe: this is strange...what option did you choose on the ubuntu live cd booter?

I  used "Install Ubuntu"

---

### Post by fmartinez on 2008-09-11
Calm down, calm down.... getting frustrated won't help things. Let's check the installation CD. Insert the installation CD and boot it. On the initial screen after you pick you language select the option that checks the disk. If you have any errors i would recommend to re download Ubuntu and burn another copy and reinstall the OS. If not post back and we'll go from there.

---

### Post by fmartinez on 2008-09-11
Update: A couple of days ago I had to re download Ubuntu about 2 times before I got a good download and was able to install a fresh copy on my laptop. That's why I suggest to check the CD. It may have missed some packages if they were corrupted on the installation disk.

---

### Post by hijoe99 on 2008-09-11
Hmm..I'll try it thing is I've already downloaded and burned it twice.  I'll try to get a torrent for it this time.

---

### Post by hijoe99 on 2008-09-12
I guess I'm just not meant for Ubuntu.  I've dled it from 3 different sources and I'm getting the same problem every time.  :icon_frown:

---

### Post by fmartinez on 2008-09-12
hmmm... That's very strange. I've had problems with some downloads this past week as well. I use US sources, but I had to use different sources about 2 - 3 times. Did your CD's check out ok?

---

### Post by hijoe99 on 2008-09-12
Yup, all the disks checked out just fine.

---

### Post by frankleeee on 2008-09-12
I am assuming that nobody is trying to burn the CDs faster than 4x.

---

### Post by hijoe99 on 2008-09-12
I did them all at 1x..

---

