---
title: "&quot;Could not find kernel image: cli&quot; heron alternate cd install"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by nocheeseman on 2008-05-11
Hi all, first post, so excuse the layout! :confused:

I'm trying to install a command line only version of Heron using the i386 alternate CD, using [ The Low Memory Systems Install HowTo]("https://help.ubuntu.com/community/Installation/LowMemorySystems") as a guideline.

However, when i type cli to start the install on the CD, i get the message:

"Could not find kernel image: cli"

I know the CD is good - i've checksumed it on another machine, and have installed a (extremely clunky!) fully working install of Heron with Gnome and all the rest of it when i typed "install cli-expert" command at the boot prompt, but what i really want to do is install a command line base system and then add packages manually to customize the window manager etc to make it run faster.

From trial and error, the "expert", "memtest86" and "install" commands do work, but they're no good to me!

I'm entering just 'cli' or 'install' and pressing enter at the boot prompt now.

I've tried cli and cli-expert commands, but they return the error as above.

I've tried to find out which kernel images are on the CD to no avail to try and work out where i'm going wrong here.

I've googled extensively for answers to this and read all the install guides/CD documentation/boot help screens on the CD, so any feedback would be very helpful. I'm no Ubuntu expert, but i have it running well on 2 other systems (Ubuntu Server and X64 desktop), and have done quite a few installs now ;)

The hardware in question is: 

Epia 5000 board (Via C3 533 processor)
768MB PC133
20GB Seagate 2.5" drive connected to primary IDE
CDRW connected to secondary IDE.
Netgear WG111v2 Wireless USB (RTL8187L chip) (when i get that far!)

Thanks in advance for any pointers... :)

---

### Post by nocheeseman on 2008-05-11
Ok, little update - downloaded same alternate CD from torrents rather than main mirrors, burned at 4.7x, same issue :(

---

### Post by nocheeseman on 2008-05-11
...And another update...

Got curious and tried the CD on my laptop, and the screen you get when the machine boots from CD is very different.

On the laptop i get:

> Nice quality Ubuntu logo, then a menu with options:

install ubuntu
check CD for defects
rescue a broken system
test memory
boot from first hard disc

F key options at the bottom to display help


You also get an option to set language pop up over the top.
There isn't a place to type what sort of install you'd like!

I checked the CD for defects while i was in there, that's all ok.

When booted from the exact same CD, the "problem machine" gives me:

> Crunchy 256 colour logo, and text as follows:

The default installation is suitable for most desktop or laptop systems.
Press F1 for help and advanced installation options.

To install only the command-line base system, type 'cli' then ENTER.

boot:


I think this difference in boot screens is the root issue here, so my question now becomes - is it actually possible to do a command line only install from a Hardy Heron Alternate CD, and how?

Would love to know if there's someone else out there who sees this crunchy screen on low-end hardware, and if the cli option works at the CD boot prompt!

This is turning into a bit of a personal worklog, but at least someone may benefit at some point! :D

---

### Post by reknedsredna on 2008-05-12
Hi nocheeseman,

i've got the same problem :-(

The Installation on my desktop-system worked very well, but when I wanted to upgrade my server, I got the same screen and error like you.

My hardware is very similar to yours:
Via C3 - 800 MHz
512 MB Ram

So I think the different Screen depends on our hardware.

---

### Post by nocheeseman on 2008-05-12
Thanks for the reply there reknedsredna - it's good to know i'm not alone!

I'm going to stick my old server cd of dapper in the machine and see if i get anywhere with it - Watch this space... :)

---

### Post by nocheeseman on 2008-05-12
Dapper CD looks good, has more options and text mode etc on the Epia, i think it would work.  Let me explain, my server originally ran Dapper, and i've upgraded it up through the releases, but things are not quite right on there now that i'm on Heron - it probably just needs a fresh install!

Are you using the heron server CD or an alternate CD to attempt installing your Epia?

Either way, I'm now seriously thinking of trying an older server version (7.04 or 7.10) to avoid most of the dist-upgrading, upgrading to heron from that, before I put on all the eyecandy! Or... should i stay focused? is this a bug? Should we tell someone? :confused:

---

### Post by reknedsredna on 2008-05-13
I used the alternate CD  and got the same problems like you.

Then I tried the server CD, I got almost the same screens as using the alternate CD and typing "cli" created the same error.

But by pressing just ENTER it works! I feared that the CPU doesn't work with the special server kernel, but it works very well (up to now ;-)).

However, I think someone could report this as a bug a launchpad.net (I don't have a launchpad-account, do you?).

---

### Post by nocheeseman on 2008-05-13
Good to hear you're working there mate! :D

If you want a server, I reckon it'll work fine for you - the VIA CPU's are fully x86 compatible, so I can't see any reason why it wouldn't work!

As far as the bug reporting goes, I don't have a launchpad account either, but then I didn't have an ubuntu forums account until I had this issue!

Having said that, launchpad doesn't look like the kind of site that will be interested in a stumbling newbie like me saying "when i type 'cli' it doesn't boot" :confused:

I think i'll ask a question over there about this as well as bug-raising-worthiness and see what transpires from that.

Thanks for your time and useful input Reknedsredna, and i'm glad we've got somewhere with this! :biggrin:

---

