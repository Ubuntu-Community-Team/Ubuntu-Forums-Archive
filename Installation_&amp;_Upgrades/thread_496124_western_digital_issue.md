---
title: "western digital issue"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by jeb0044 on 2007-07-08
Hi, 

I am in the process of migrating to Linux.  To give a short brief, my windows machine always had problems with security.  This time, it really did wipe out my hard drive.  After replacing the drive, I am now able to see the boot menu from HP!!

The new drive is a western digital caviar SE 160 gigs.  I've never tried to get a computer up and running from scratch before...

I am getting nowhere with installation of ubuntu.  When I boot from the cd drive, the menu comes up, I choose to 'start or install..' and after a loading screen, it prints out some loading text, then a big error message.

Like a fool, I decided to insert the accompanying western digital cd.  I ended up doing nothing with it, but the next time I tried to install ubuntu, it did the same error message thing in a loop.

I don't get to the ubuntu desktop screen where I can partition drives and complete the installation.  I'm not worried about the graphics card because I can get a driver, and at least I see the screen for now.

I guess I am looking for help installing this thing.  I know it's just supposed to work but I don't think it likes the hard drive, which I didn't really think would matter.

Is there a driver for this HD that I need to install?  Or do I have to configure it some way in the bios?  I'm at a real loss here, any help would be greatly appreciated.  I really don't want to and can't really afford to get another windows install disk, especially knowing it will only last me 3 installs, or maybe 2 years before it goes offline like this again.

Thanks for reading and for the consideration.

R,,

---

### Post by Pumalite on 2007-07-08
What are your specs? Are you dual booting?XP? Vista? It all makes a difference.

---

### Post by phidia on 2007-07-08
It's a good idea to include you system specs ( cpu type and speed, amount of memory/ram and yes the video card ) so we can see if there are any big hurddles there. And what was the error message-that's definately important. People here will really try to help but we need a little more info to go on.

---

### Post by jeb0044 on 2007-07-09
OK.  Thanks for the reply.  I can respond with the hardware specs and hopefully the error message after work today.  *Hopefully* the error message, because right now it flashes so quick before I can read it and it is loop printing the stack.

Thanks for responding to this issue.  R,,

---

### Post by jeb0044 on 2007-07-09
The target system is an HP Pavillion a1010y with windows xp pre-installed  (I bought this about 4 years ago before I realized I could get good parts from newegg)

Specs:

Motherboard: ASUS PTGD-LA socket LGA775, Three PCI slots, 4 sata, realtek ALC880 8-channel audio codec,etc.

Processor:  Intel Pentium 4 HT

BIOS: HP BIOS

RAM: dual-channel 4X240-pin DIMM up to 4GB.  Currently has 2x512MB chips (included from vendor), and one GSkill 512MB chip.

HD: SATA Western Digital Caviar 160GB (newly installed after recent hd failure)

video card: Geforce 3x series, I have to find the box for sure,
drives: sony cd/dvd rw combo drive-is able to run the linux install cd

Ubuntu: I am attempting to install the standard computer distro, burned onto a cd as an ico image.  Error message before it actually hits any installation screen says 'loading hardware drivers..' then hits an error that looked like 'VF not found' then spit out a big error.  I say looked like because it flashed so quick I couldn't really see it.  However since I ran the HD accompanying cd, it now loops a big error msg when I try to install.

Thanks - help getting this OS up and running would be appreciated.

R,,

---

### Post by jeb0044 on 2007-07-09
Oh, I'm not dual-booting anything.  It's basically just a Windows Machine that somehow the HD got damaged and no longer functioned.  Getting a new hard drive at least got it to boot into the BIOS.  I was hoping to install ubuntu by itself on this new hd, but also hoping that the hardware can get the OS to run.

Thanks,,

---

### Post by dabl on 2007-07-09
Jeb, if you can make a CD, download and burn the GParted Live CD ISO image from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Burn it "as an ISO" and you will have a bootable CD.  Boot this CD, and use it to partition your new hard drive.  You didn't say you want to keep a Win XP installation, so I dunno about that.  If you DO want a Win XP system, then you need to make 4 partitions on that hard drive, as follows:

15 GB (for WinXP -- if you've got a lot of Win programs, make it 20GB) -- set the "bootable" flag on this one
10GB for Ubuntu's "/"
1 GB for Ubuntu's "{swap}"
the rest of it for Ubuntu's "/home" (this is where your data goes)

If you DON'T want a Win XP installation, then you can add that 15GB to the big partition for /home. In this case, set the bootable flag on the 10GB partition which will become "/" in Linux.

You don't need to do formatting with the GParted CD, just the partitioning.  When you've got everything set, you choose "Apply" or whatever it says to put the partitions into effect on the top menu.

Then, if you ARE installing Win XP, do that next, on the 15GB or 20GB partition that you made for it.

Then, boot your Ubuntu Feisty _Alternate Install_ CD -- that's the one that I have the best luck with.  You can use the Ubuntu Live CD to make sure that your hardware is going to function at some level, but I recommend the Alternate Install CD to actually do the installation, and I recommend you do it in "Text Mode" which is the first option on the installation menu.  You will use "guided installation" and when you get to the partitioning, you will simply highlight each of the available partitions, and set the mount point as I described above for each one, and then let it format them during installation.

Here's more about partitioning and dual boot systems: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Hope this helps!  :)

---

### Post by jeb0044 on 2007-07-09
well, I must be kind of stupid.

When I boot from the partitioner, it gives me options to '[boot an OS]'  The ones I tried appear to crash.  I mostly tried the first option, which was an auto configuration?

How do I get to the partition screen?

---

### Post by phidia on 2007-07-10
> **jeb0044 said:**
> Oh, I'm not dual-booting anything.  It's basically just a Windows Machine that somehow the HD got damaged and no longer functioned.  Getting a new hard drive at least got it to boot into the BIOS.  I was hoping to install ubuntu by itself on this new hd, but also hoping that the hardware can get the OS to run.

Thanks,,

Since you already said you want to install ubuntu by itself there's no need to use the gparted livecd. Just get the alternate iso  from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and start the install. If you run into problems post as much of the details as you can and people here will try to help.

---

### Post by jeb0044 on 2007-07-10
ok.  I'll try that sometime tonight.  Thanks for the help and the patience.

---

### Post by jeb0044 on 2007-07-15
sorry it took me so long to get back to you all..  I didn't have a chance to work on this until today.

I tried the alternate text-based install, seemed to install everything.

The only problem now is when I go to boot up ubuntu, it gets to the loading screen, loads for a couple of seconds and freezes up.

In the meantime I could try the menu before it gets to that screen and see what that does.

-jeb

---

### Post by dabl on 2007-07-15
> **jeb0044 said:**
>  it gets to the loading screen, loads for a couple of seconds and freezes up.


Prolly a video issue -- it looks "frozen", but what happens when you press Alt-F1?  How about Ctrl-Alt-F1?  If you get a login prompt that way, then log in, and we can tell what to do next to get a GUI display.

---

### Post by jeb0044 on 2007-07-15
on alt+f1, it gets to 

loading hardware drivers..

Then spits out a big error message, too big to scroll, but what I end up with is something like> (same as when I boot from recovery option)

release_console_sem+..
exit_mmap
input 
do_exit
printk
show_stack
do_invalid_op
do_invalid_op
kmap_atomic
seq_printf
show_stat
error_code
kmap_atomic
__handle_mm_fault
kunmap_atomic
get_page_from_freelist
do_page_fault
do_page_fault
error_code
do_notify_resume
attach_pid
wake_up_new_task
work_notifying

These have mixed codes after them, and before them on the same line they show [  33.1132342]...
and [<c0137ef4>]

Basically printing a stack dump, but it goes too quick for me to see the top part, so all I get is the bottom of the stack.  I don't know if any of this helps.

I can tell you the video card is a geforce, which previously ran when that machine had windows.  I haven't downloaded a linux driver for it yet-but I think it is the only piece of hardware that isn't running, especially since the graphical install didn't run and the text-based did.  I don't really know how to install the driver for it before I get into an os.

Oh-I also tried switching to on-board video, which is included in the asus chipset.  It was supposed to be intel-based, but I'm not sure of it exactly.  I may try un-hooking the geforce card and see if that does anything in the meantime.

-j

---

### Post by jeb0044 on 2007-07-15
This time it got to a text-based login after the loading screen.

But the screen was jumpy, and I had a weird sounding whine coming from the box.

It spit out the error:

...
Module loader present
(WW) No matching device section for instance (BusID PCI:0:2:0) found
(EE) No devices detected.

Fatal server error:
no screens found.

[Detailed]
Device - 'Intel Corporation 82915G/GV/910GL Integrated Graphics Controller'
...
Driver for Intel Integrated Graphics Controller ... i810, i810-dc100, ...
...
Primary device is : PCI 00:2:0
...
[same error msg as above]

---

### Post by merlinus on 2007-07-15
You might try this at a system prompt:

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

-merlin

---

### Post by jeb0044 on 2007-07-15
I'm up and running - this is a good sign, thank you all for helping me salvage my hardware after a nasty windows virus.

I've worked with unix/linux before but only through server shells.  It will take me some time to get to know the software and get my junk back, but I thank you.

Oh- the user name I set up seems to be a home user.  How would I log into my puter as root?  Or is the user that gets set up on installation the root user?

-j

---

### Post by jeb0044 on 2007-07-15
Oh-there's another thing-when I originally bought this graphics card, it was to run a game that needed a kind of 3d support.  The card ended up being slower than my on-board video, but by the time it became apparent the installation of that card in windows had wiped out the drivers for the on-board video.  When I went to microsoft to try and salvage the onboard card, they wanted me to pay a hefty fee for the drivers.

Now I'm back to my better graphics and can pawn off the old 'new' card.  Thanks..

---

### Post by merlinus on 2007-07-15
You can use 

sudo <command>  (or gksudo for gui apps)

in a terminal to get root access.  You will be asked for your user password.

There is no root account per se in ubuntu for security reasons.

-merlin

---

