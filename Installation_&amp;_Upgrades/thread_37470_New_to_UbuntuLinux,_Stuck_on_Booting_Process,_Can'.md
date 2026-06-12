---
title: "New to UbuntuLinux, Stuck on Booting Process, Can't Get Back to BIOS"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by segorese on 2005-05-27
Hi and thank you for entertaining my question(s)!
Keep in mind that at present, I'm a Linux newbie and don't understand where
command line syntax is supposed to be entered, if at all.

I have properly partitioned my hard drive and have set up BootMagic to see that there are XP and Linux partitions.  I have the ubuntu-*-x386.iso properly burned as an image file to a CD.   As I was trying to distinguish it from the name of the "regular" *.iso -- that I mistakenly did not burn as an image -- I changed the name to something like Ubuntu504.iso.  I've since wondered if this has had any effect on what's going on,   \\:D/ 

Looking at XP's (actually Partition Magic's)  instructions for adding a new OS, I gathered that one should prioritize the boot as follows:  CD drive, hard drive, floppy drive.  That's how I set up my BIOS settings.  I was also led to believe that the CD drive (for whatever reason) may not be bootable.   :neutral: 

As such, I found a copy of software called DiskBootManager and placed it on a floppy diskette along with RawWrite  O:).  I thought I was making progess when on one boot up, I saw RawWrite asking for the image file, which I supplied as being on the CD drive, but I was confused about its Read/Write choices. I assumed  
I was asking in to Write the image, but I'm not sure of this as the idea of "image file" very is new to me.

I can choose XP within Symantec BootMagic as it boots up with no apparent damage or slowness to XP.  But when choosing the Linux partition, I only get a message that reads, "Machine is preparting for you to run 'Linux" " and then 
hangs up indefinitely -- no surprise of course as nothing is there yet.   ](*,)  ](*,)  

I've tried disabling Boot Magic, to try to get into the BIOS to try to reset it to an order that's bootable to but no avail.  All I get is the screen on the BIOS for device settings which shows the familiare  Master:  CD Drive (Samsung and serial #s) and Slave: no drive that shows up on the screen prior to the Windows XP splash screen.  I can only choose F2 which does nothing, the arrow keys which simply go back and forth from Master/Slave and Esc which gets out of this utility.  On one boot, I was able to see and change BIOS settings, but didn't recall what I did.

So, first off, it would help to know how to get back into the BIOS to change the boot priority as needed.

I know this is very rudimentary, but I can't get any further.  

-  Have I characterized a common problem?  

- Doesn't the system try to boot from the CD first if I have it in the BIOS that way?  

- Could it be that the CD itself is not bootable though the drive is (it's a 1.5 year old machine, fairlly state of the art at that time)?   


I really appreciate help I can get with this.  Ubuntu seems like a very friendly place from what I can tell and I was encouraged by the home page's invocation that this was software for "everyone".  I am a longtime Windows datageek, trained in DOS and GUIs, but not really conversant in UNIX at all.  I'm familiar with mainframe type syntax but am a bit confused by the flippant  use of code lines that I've seen at other distros sites.  (I have no idea at present where one would even place such code...)

Plese bear these thoughts in mind when explaining the response.

Thank you.  I hope to be communicating with many of you for years to come
as I am excited about the prospect of jumping to this Brave New World of
open source!   \\:D/   \\:D/ 

Steve Segore
Albany, NY, USA

---

### Post by bored2k on 2005-05-27
[QUOTE=segorese]So, first off, it would help to know how to get back into the BIOS to change the boot priority as needed.

I know this is very rudimentary, but I can't get any further.  

-  Have I characterized a common problem?  

- Doesn't the system try to boot from the CD first if I have it in the BIOS that way?  

- Could it be that the CD itself is not bootable though the drive is (it's a 1.5 year old machine, fairlly state of the art at that time)?   


I really appreciate help I can get with this.  Ubuntu seems like a very friendly place from what I can tell and I was encouraged by the home page's invocation that this was software for "everyone".  I am a longtime Windows datageek, trained in DOS and GUIs, but not really conversant in UNIX at all.  I'm familiar with mainframe type syntax but am a bit confused by the flippant  use of code lines that I've seen at other distros sites.  (I have no idea at present where one would even place such code...)[/QUOTE]

Insert your windows disc > recovery console > type down fixmbr. Or use another tool [Ultimate boot cd](http://www.ultimatebootcd.com/) to fix it.

- Have I characterized a common problem?  No. 99% of us stick to Linux's boot loaders.

- - Doesn't the system try to boot from the CD first if I have it in the BIOS that way?  It should.

- - Could it be that the CD itself is not bootable though the drive is (it's a 1.5 year old machine, fairlly state of the art at that time)? Insert a windows disc. Is it bootable ? If so, it's not your drive, its a bad recording.

> I can choose XP within Symantec BootMagic as it boots up with no apparent damage or slowness to XP. But when choosing the Linux partition, I only get a message that reads, "Machine is preparting for you to run 'Linux" " and then
hangs up indefinitely -- no surprise of course as nothing is there yet.  

So you are trying to enter your linux partition before you install it ? that is not the right order. I recommend you get rid of boot loaders like SYmantec's and stick to Linux's LILO or GRUB.

---

### Post by logan2004 on 2005-05-27
hmmm, you can't get into the bios now, but you could get into it before??
i know that symantec boot magic wouldnt be able to affect any of this.

press del, or f12, or maybe even f2(dell?0 when your system boots up and that should bring you into the bios. play around in there and you should see something like "boot order" or "boot1", "boot2", or "boot3"

just make sure you CD-ROM drive is set to first and stick the ubuntu cd in. 

you can use grub(a common linux boot loader) instead of symantec bootmagic to set which partition you would like to boot from - this will setup automatically with ubuntu.

during the ubuntu installation process it will automatically configure your drive to dual boot, and will repartition your ntfs or fat32 drive to make room for ubuntu.

good luck, please ask any other questions you have

PS - once you get into ubuntu click Applications > System Tools > Terminal

this is where commands can be entered (similair to cmd, or command.com - on steroids)

BEWARE, bash(default terminal shell) **will** make you hate cmd

---

### Post by r.a.yarg on 2007-10-20
Another Albanian-NY - another New to Ubuntu, but I'm starting on a fresh hardrive & new laptop. Let me know how your change of OS goes. This will be totally different for me, too - an XP Pro person.
Best, R.A.

---

