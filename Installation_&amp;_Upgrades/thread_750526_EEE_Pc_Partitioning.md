---
title: "EEE Pc Partitioning"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by IntelOfficer on 2008-04-09
Ok, I'm brand new to this whole Linux thing.  I'm trying to get Ubuntu installed on my EEE Pc.  The problem I have is that I don't understand how to partition this thing correctly.  I've read a couple different ways to do it.  One place said use EXT2 another said use JFS.  If anyone can help give me some instructions on how to properly create the partitions it would be much appreciated.  Also, I'm sorry if this question has been asked before.

---

### Post by artir on 2008-04-09
I dont know the exact partitions, but try xubuntu. there is a special version of it for eee

---

### Post by IntelOfficer on 2008-04-09
First off, wow...  I didn't expect to have a reply within minutes of my post.  Now, do I have to download another type of ISO for Xubuntu?

EDIT: Googled and found it's a different ISO.  Kind of hoped it wasn't, I'm basically on a 56K connection, so downloading takes a while.  I'm sure I'll be back with more questions.  Thanks for the help.

---

### Post by fela on 2008-04-09
yes, there's a special version called EEEXubuntu. On their site (can't remember URL, google for it), there's a special howto to get it on a usb stick, then install from that onto your eee. (so you don't need an external cd drive for your eee while you install)

edit: if your on a 56k connection, it wouldn't be very realistic downloading the whole 500-and-something MB iso file. If you know anyone with broadband, i reccomend asking if you can borrow their connection to download the iso.

---

### Post by bradwilliamson on 2008-04-09
With regard to the partitioning/formatting of the eeePC, remember this:

**It's a solid state drive with a finite lifespan.**

Therefore, for the life of the system: 

- NO SWAP PARTITION! (Waste of space on something this small anyway)
- NO JOURNALING FILESYSTEM(s)
- Disable last accessed time in /etc/fstab by adding noatime to the list of parameters

Otherwise, you just partition it like your average Windows box, all one partition.

Format it as ext2 (yes 2, not 3, we don't want the journal eating the drive)

Ignore the complaints about the lack of swap, and off you go.

I used the Xandros for a few days, wiped it out with eeeXubuntu and have been totally happy with it since!

Hope that helps
Brad

---

### Post by aysiu on 2008-04-11
> **bradwilliamson said:**
> 
I used the Xandros for a few days, wiped it out with eeeXubuntu and have been totally happy with it since! I'm thinking about doing this, but not having an external DVD-ROM drive, I'm a little scared of not being able to restore the default Xandros in case something goes wrong.

Does everything work with eeeXubuntu? Special keys? Microphone? Webcam? Wireless? Screen resolution?

---

### Post by articpenguin on 2008-04-11
you could use jfs and use nointegrity mode on it.


nointegrity	Do not write to the journal.  The primary use of this option
		is to allow for higher performance when restoring a volume
		from backup media.  The integrity of the volume is not
		guaranteed if the system abnormally abends.

---

### Post by fela on 2008-04-11
> **aysiu said:**
> I'm thinking about doing this, but not having an external DVD-ROM drive, I'm a little scared of not being able to restore the default Xandros in case something goes wrong.

Does everything work with eeeXubuntu? Special keys? Microphone? Webcam? Wireless? Screen resolution?

my approach with Linux is: it works if you want it to!

the devs of eeexubuntu made it especially so that it'd have all the drivers for the eee stuff, so i reckon it should work. I installed it on my friends eee, and it worked fine. If it goes wrong, just reinstall eeexubuntu! I don't think Xandros is any less likely to go wrong, or fubar the system. And IMHO gnome or even xfce is nicer than the hacked KDE and it's windows theme that is with xandros (i think it's kde). You can install gnome once your in xubuntu by running ```
sudo aptitude install ubuntu-desktop
``` or KDE by running ```
sudo aptitude install kubuntu-desktop
``` Although i guess you wouldn't want to do that, to save drive space (should no longer be called 'disk' lol)

---

### Post by aysiu on 2008-04-11
While I have read reports in the past of people having problems with the preinstalled Xandros, I think Asus has gone pretty far in correcting most of those problems. Mine is newly purchased (not from November, for example), and so it didn't have the warning about voiding the warranty if I upgrade the RAM, weird noises coming out of it, overheating problems, etc.

Everything has just been working. I didn't even have to enable the webcam in the BIOS (which I've heard people in the past have had to do). So I'm a bit wary of messing with a good thing if I'm not able to restore it. Still, I'm a little conflicted, since I've been using Ubuntu for almost three years... hard to say "Goodbye," you know?

---

### Post by fela on 2008-04-11
would it be possible to create a usb stick that you could restore xandros from?

---

### Post by aysiu on 2008-04-11
> **fela said:**
> would it be possible to create a usb stick that you could restore xandros from?
I don't know. I could probably *dd* the drive, but wouldn't I have to not be using the OS in order to *dd* it?

---

### Post by ExWindoughs on 2008-04-12
aysiu,

I've had my e for about 3 weeks.  Really wondered if I did the right thing, given the limitations of the stock systems.  I had the same concerns you raised, but by the 2nd night had made a eeeXubuntu usb, crossed my fingers and let it fly.

I am delighted with the results.  Absolutely no problems that couldn't be easily worked out.  I can run the apps I have on my desktop (e.g. GnuCash).  I find myself (like now) using the e even though my desktop is 10 ft. away.

Go for it and see what this thing can really do!  For what it's worth, I bumped mine to 2gig ram, prob. not necessary but what the heck ...

---

### Post by aysiu on 2008-04-12
I'm kind of a stickler for having a back-up plan, but thanks for the words of encouragement! When I have an easy way to restore the Xandros installation, I'll probably start playing with eeeXubuntu... maybe even dual-boot off an SD card.

---

### Post by DianeHelen on 2008-04-12
My eee is on the way, so naturally I am very interested in anything relating to how you guys are making the switch from the pre configured Xandros, to Ubuntu. 

So, am I reading correctly, that by downloading the regular Gutsy 7.10, Ubuntu, it would not be correct for my new eee that arrives Monday? Do I need to d/l a special version? And would that special version be basically the same to me, as far as software , useability, look and feel, etc?

I have read some of the How To's on re doing it to Ubuntu, and would most likely be doing that via a USB flash stick. 

Im a bit confused about all the other stuff, the guides have mentioned, to do after the install.

I guess its a process and I need to do it piece by piece,. and with the help of the fine fokls around here 

:)

---

### Post by aysiu on 2008-04-12
Well, just to be clear, I am still using the Xandros installation that came with the Eee, as I don't currently have an easy way of restoring it should something go with a Ubuntu installation.

My understanding is that you can get a regular Ubuntu installation working with the Eee, but it takes some work and extra tweaking; the eeeXubuntu version supposedly incorporates those tweaks, saving you the trouble.

---

### Post by DianeHelen on 2008-04-12
Ahh ok, so when I get it, and IF I want to make the move to U, maybe wait till the 8.0 release, and just get the 8.0 eeeXbunto version?

Then just stress my brain on all the instruction to make the bootable stick...

May just see if I can use my old portable usb Zip CD drive. Would that be any easier?

---

### Post by aysiu on 2008-04-12
If I make the move, I'll probably wait until after the 8.04 release as well.

And I think a USB CD-ROM drive would probably be more useful than a zip drive.

---

### Post by DianeHelen on 2008-04-12
would an old USB Zip CD drive, be recognized easily on the eee?

or, would something like THIS work?


[http://cgi.ebay.com/NEW-Super-Slim-External-USB-Portable-24x-CD-ROM-Drive_W0QQitemZ300214896722QQihZ020QQcategoryZ42180QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/NEW-Super-Slim-External-USB-Portable-24x-CD-ROM-Drive_W0QQitemZ300214896722QQihZ020QQcategoryZ42180QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Price seems great! and would be a great addition to the overall system, to have access to a CD when needed


Any opinions?

---

### Post by mrsrandallthomas on 2008-04-12
I have the ASUS Eee PC 4G Surf. I installed 1 GIG of RAM on day one. (So far so good.)

I purchased an external DVD Burner. (Plug and play, all is good.)

LINUX; I'm new to it but learning kinda quick. Yet I still need instructions to be written in crayon.
(Too many posters on the web assume the reader knows some LINUX basics. Not Good For Me.)

Now.....Having said that. I download Ubuntu made the boot able CD(s) several times. The downloads didn't work on the Eee PC for one reason or another. (64 bit vs. 32 bit and son on.)

However, I found a Ubuntu version that was/is perfect for the Eee Pc. Seems that it was designed specifically for the Eee PC.

PROBLEM: In a word "Partitions".

I think I understand the concept. Something like Pocket PC, when you check the memory there's a slider that is used to allocate memory. You can allow more to the RAM (if available) on the fly if the machine seems to be running slow from too many applications being open, etc.

With LINUX and Ubuntu I haven't a clue as how to correctly set this critical feature. I should note that I only want to run Ubuntu and I don't care if it uses all of the memory. How the partitions are set matters not to me as long as it allows the system to function.

So.......I get Ubuntu up and running. (GREAT!) However, if I shut the machine down it will not reboot. In fact, it doesn't really shut down. The screen goes black and I get an Error 15, which stays there. Can't fully power off. I'm pretty sure this error is a result of how I set the partitions.

{If you don't already know, there two tiny holes on the bottom of the Eee PC. One is a mic, the other is a reset like you'd find on the back of a Palm or Pocket PC.}

I hit the reset, if it won't work I'll also remove the battery for about two minutes. Restart and hit "F2" then reboot the original ASUS Support DVD.

This is a bit long but I want my problem to be stated as clear as possible.

I'm looking for the easiest answer, which should come in the form of STEP-BY-STEP Instructions. Please don't give me some code and ASSUME that I know where it is to be entered. Please don't give "$" "#" or other symbols and ASSUME that I know that they are not to be entered with the code.

Please feel free to send me a private message if need be. I'm new to the forum and don't know that I will see a post in response to this one.

In any case, I will be forever thankful to whom ever has the knowledge base and the generosity to offer me assistance.

---

### Post by KenBW2 on 2008-04-12
I stuck with Xandros for a while, thinking I'd try and stick KDE out (I'm an Ubuntu fan at heart), but alas, KDE wasn't for me.

So I decided to go in for the dive and install EeeXubuntu.

The outcome? A definite improvement! I'm typing on it now.

Positives:
- A more familiar and (imo) better GUI
- No XP lookie-like theme :)
- COMPIZ! :D

Negatives:
- Slower boot time (~30secs)
- More 'disk' usage
- Slightly slower performance
- You lose out on a few hotkeys, although there are fixes available

Overall I'd definitely say it's worth the plunge. Here's the steps I took:

1) Download [[COLOR="Sienna"]EeeXubuntu[/COLOR]]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home") on a PC with a CD/DVD drive
2) Follow the instructions for installation
3) In live, er, USB-mode, format the whole (yes, whole) HDD as ext3 (although whoever said it could be right about ext2). Don't put a swap partition on: save that for later. If however you have a >2GB HDD unlike me you'll probably be better with one for hibernate, standby etc, but beware the read/write on the HDD - SD cards are MUCH cheaper to replace)
4) Install EeeXubuntu
5) Enjoy your new Eee :)
= Optional steps =
Pick and choose some of the [[COLOR="Sienna"]tweaks from this page[/COLOR]]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization"). I recommend as a priority:
   - [[COLOR="Sienna"]Enable Compiz - it works really well[/COLOR]]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#enabling_compiz-fusion_desktop")
   - [[COLOR="Sienna"]Fix the bug where it (why?) looks for a CD drive[/COLOR]]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#mounting_external_devices_usb_disks_sd_cards_etc")
If you want a swap partition (I have one and it does seem to have an effect): This is assuming you use an SD card in the slot pretty much permanently
   - Partition all but around 1GB as FAT16/FAT32 (depending on the size) for storage, and the remaining as swap.
   - Add the new drive (sdb1 and sdb2 respectively) in your fstab file to have them auto-mount as bootup. (Warning: This gives me a bit of a problem where I have to be root to unmount either, but at least it saves me having to mount them myself - suggestions welcome)

Have fun and check the amazing community at [[COLOR="Sienna"]Eeeuser[/COLOR]]("http://www.eeeuser.com/")!

---

### Post by dcstar on 2008-04-12
> **bradwilliamson said:**
> With regard to the partitioning/formatting of the eeePC, remember this:

**It's a solid state drive with a finite lifespan.**

Therefore, for the life of the system: 

- NO SWAP PARTITION! (Waste of space on something this small anyway)
- NO JOURNALING FILESYSTEM(s)
- Disable last accessed time in /etc/fstab by adding **noatime** to the list of parameters
.........

There is also a "**nodiratime**" directive that doesn't update directory access timestamps  - this should also reduce the unnecessary writes which will reduce the life of the solid state drives.

I would assume that installing like this would also help, as a lot of the O/S would be in RAM:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

A journaling fs is probably not as necessary as with a mechanical drive, and extending the "sync" time for cached disk writes could also be something to be experimented with for the same reason.

---

### Post by i.am.technofreak on 2008-04-13
my eee came with a dvd with loads of stuff on, along with the backup of xandros.  because the eee doesn't have a dvd drive, there will most likely be a utility on the disc to stick it on a usb stick. 
technofreak

---

