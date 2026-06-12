---
title: "Can't install Ubuntu in Santa Rosa laptop"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by petoro on 2007-07-21
I can not install Ubuntu in a new Santa Rosa laptop.

The graphics card is an Intel X3100, and the hard disk is a SATA Toshiba MK2035GSS

When I start the computer with the CD inside I get the usual initial menu but, when I press Enter to start with the LiveCD, it tries to start and, after a minute, I get the following message:

/bin/sh: cant access tty; job control turned off
(initramfs)

Then, I write 'help' at the command prompt and I get the available commands, as in the photo.

This gives not clue about why the installation fails nor what to do next.

Any suggestion to make a succesfull installation?  Thanks

Petoro

[IMG]http://farm2.static.flickr.com/1294/860976913_5775ebe114_b.jpg[/IMG]

---

### Post by Pumalite on 2007-07-21
Try Alternate CD. It's text mode, but it has more chance of success in your laptop.

---

### Post by Gremlinzzz on 2007-07-21
If you can't install ubuntu try another linux system.Think feistys kernel is giving laptops allot of problems.
[http://distrowatch.com/](http://distrowatch.com/)
ya have allot of choices even a older version of ubuntu.

---

### Post by petoro on 2007-07-21
I have tried Feisty and I have also tried Gutsy Gibbon Tribe 3, both normal and alternate.

Installing alternate I can have a little more things done, for example the ext3 and swap partitions, but I end up with a text screen full of garbage -and a corrupt Vista MBR :(-.

Any other suggestion?


Petoro

---

### Post by Pumalite on 2007-07-21
If you are dual booting with Vista in the same hard drive, then partitioning becomes important. First off, you can recober MBR with your Windows installation disk. I don't know in Vista ( I don't want to know), but in XP I seem to remember: hit 'r' for Recovery console, then>FIXMBR.
Anyway, with Vista, you HAVE TO partition from WITHIN Vista, or else Vista won't let run anything in your comp. ( if you have only one hard drive).

---

### Post by petoro on 2007-07-21
Thanks for the advice.

I have managed to recover Vista after a few unsuccesfull routines.  I'll post the method in the Web.

I have had no problems to create the ext3 and swap partitions because I had already reserved an empty partition for Linux.


Petoro

---

### Post by Pumalite on 2007-07-21
You have to use the Vista partitioner, otherwise, no go.

---

### Post by petoro on 2007-07-31
Nothing seems to make the laptop run Ubuntu.  I've tried:

Feisty,

Alternate,

Gutsy Tribe,

Wubi,

Nothing installs well in Santa Rosa laptop.


Petoro

---

### Post by J-Red on 2007-07-31
You can do it. This is what I did (from my brother's blog) 

[http://blaise.ca/blog/2007/07/01/ubuntu-704-feisty-fawn-with-an-hp-compaq-6710b/](http://blaise.ca/blog/2007/07/01/ubuntu-704-feisty-fawn-with-an-hp-compaq-6710b/)

My computer has the Santa Rosa chipset on it too, and Ubuntu works fine.

---

### Post by petoro on 2007-08-09
What I would like is to install Gutsy without the need to modify configuration files.

I have just tried to install Gutsy (Tribe 4) but without success.  I keep getting the same abrupt ending as in the photo in the first post.

May be faulty drivers for the Intel X3100 graphics card? I am not sure.

Will the final release of Gutsy released in November install in a Santa Rosa laptop?

Let's see...



Petoro

---

### Post by petoro on 2007-08-26
Tribe 5 works at last!!

I'm the original poster of this thread.  I have just downloaded and installed Tribe 5 and I am amazed with the improvements.

Installation results to be very fast and simple.  In a dual boot with Vista it even maintains the BIOS emulator "Loader 2.2.0" I had installed yesterday just for experimental purposes.

My draft N Intel(R) Wireless WiFi Link 4965AGN card works fine.  No configuration required, just entering the WEP key.

My Sata disk works fine and I am able to write to my NTSF partition without any kind of configuration.

The Compiz effects work very smoothly in my Intel X3100 graphics card.

Even the Sleep mode works flawlessly as in Vista.

The laptop buttons for launching the Navigator, Email Reader, Mute..., works by default as in Vista.

The one thing that seems not to work "out of the box" is the Realtek sound system :( 

Oh, and I'm not sure if the Bluetooth works...

Any clue for installing those?


Petoro

---

### Post by RemyH on 2007-08-28
a

---

