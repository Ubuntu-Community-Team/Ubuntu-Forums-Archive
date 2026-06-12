---
title: "Xubuntu Installation Problems (pics and error logs)"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by Nanoon on 2007-08-07
Hi everyone, I'm trying to install Xubuntu on my old computer, but I'm consistantly getting errors.

Here are some basic specs of the computer:

P2 233MHZ 
64MB RAM
10+GB Hardrive

It's pretty old, but hopefully it still has some life in it.

Since I don't have enough RAM, I'm using the ALT Install Disk (I've checked the integrity of the disk and it's fine).

I put the disk in the drive, boot it up, and do the keyboard set up and then get to this screen.
[IMG]http://img511.imageshack.us/img511/6294/200708070011resizexn1.jpg[/IMG]
I don't know which one to pick, so i just pick the one that starts on (the one that's highlighted in the picture).

I start the installation, and it goes fine until it gets to 6%

I get this error:
[img]http://img403.imageshack.us/img403/7135/200708070015resizecr1.jpg[/img]

It says:
```
"Install Base System
Base System Installation Error

The debootstrap program exited with an error (return value 1)

Check /var/log/syslog or see virtual console 4 for the details"
```

Here's the Virtual Console:
[IMG]http://img178.imageshack.us/img178/2214/200708070018resizehx7.jpg[/IMG]

Then I hit continue, and then I get this error:
[img]http://img123.imageshack.us/img123/5131/200708070019resizedz1.jpg[/img]

Along with the Virtual Console log that says:
```

Aug 7 14:21:50 base-installer: error exiting on error base-installer/debootstrap-failed.
```

After that error the installation terminates and leaves me with a message that says:

```
Installation Step Failed
And installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. 
The failing step is: Install the  base system
```

And the Error log reads:
```
Aug 7 14:24:50 main-menu[2095]: WARNING**: configuring 'base-installer' failed with error code 1
Aug 7 14:24:50 main-menu[2095]: WARNING**: menu item 'base-installer' failed
```

Then I'm redirected back to the main menu


Anyone know what could be causing the errors that I'm getting, and is there a way to fix it?

---

### Post by Gremlinzzz on 2007-08-07
[http://distrowatch.com/?newsid=04403](http://distrowatch.com/?newsid=04403)
[http://distrowatch.com/?newsid=04341](http://distrowatch.com/?newsid=04341)
think it needs a system for older computers heres 2
:guitar:

---

### Post by merlinus on 2007-08-07
[B]Minimum system requirements for xubuntu
[/B]

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

-merlin

 

---

### Post by Nanoon on 2007-08-07
> **merlinus said:**
> [B]Minimum system requirements for xubuntu
[/B]

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

-merlin

I have 64MB of ram, and I'm using the Alternative install CD. I mentioned that in my original post.

---

### Post by Pumalite on 2007-08-07
I doubt you will be able to install Xubuntu Alternate CD. Try Zenwalk or DamnSmallLinux.

---

### Post by Nanoon on 2007-08-07
> **Gremlinzzz said:**
> [http://distrowatch.com/?newsid=04403](http://distrowatch.com/?newsid=04403)
[http://distrowatch.com/?newsid=04341](http://distrowatch.com/?newsid=04341)
think it needs a system for older computers heres 2
:guitar:

Linux mint was a no go


I'm going to do try damn small linux

---

### Post by Nanoon on 2007-08-07
DSL was a no go also, and now i can't boot from the optical drive.

Linux adventure over.

---

