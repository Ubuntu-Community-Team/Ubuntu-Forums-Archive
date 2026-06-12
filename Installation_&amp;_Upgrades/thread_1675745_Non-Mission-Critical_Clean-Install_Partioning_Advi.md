---
title: "Non-Mission-Critical Clean-Install Partioning Advice"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by OldManAP on 2011-01-26
I have been happily using Ubuntu for a good while now. It started out sometime around the end of '09 when I purpose-built a machine to continue using WinXP Pro as my primary OS, but using a ROMTEC Trios to mechanically switch to another hard disk, booting Ubuntu Karmic. I liked the fact that the Trios kept my two disks from "seeing each other", because, at the time (and perhaps, still now), I was not ready to keep the peace between a Linux boot and a Windows boot. It was simple: use XP for "day-to-day" for a while, then power down, flip a switch, and boot up Ubuntu to get my toes wet in the Linux world.

I very quickly developed an affinity for the Ubuntu experience, and ditched my XP installation in favor of a blank slate for Linux experimentation. The disk which previously contained XP has since housed various musings of mine, including Ubuntu Studio, Puppy Studio (yes, I am a recording musician), and straight Puppy, along with some recent tinkerings with straight Ubuntu Maverick (which I've had problems with due to what I believe is lack of driver support for nvidia-96).

BTW, my current primary install is that of the original Karmic install, but upgraded to Lucid...running just fine to this date, but wondering a bit at how I'm only showing 11GB of free space on a 160GB disk...I can't quite figure where the space has gone...the math doesn't seem to work in my head, but then again, I'm still a n00b in a lot of ways.

At any rate, I've gotten a lot of mileage out of Ubuntu so far, and I'd like to experiment with "pimping" a clean Lucid installation from the ground up (as I said, I'm having graphics driver issues with Maverick, and I'd kinda like to stay with an LTS release for the time being anyway).

I'm thinking that a customized partition scheme would be a good thing to think about, and the geek in me is inclined to reach beyond the installer defaults and even beyond the common recommendations of adding a separate /home partition. I've read an awful lot about the subject, and there are as many opinions as there are underarms, but I've just gotta ask it anyway:

For a single-user desktop, is there any efficacy in using separate partitions for /boot, /tmp, /usr, /var, /opt, and/or /usr/local?  I know most that I can do without a separate /srv partition, but for the others, I just wonder if I can use separate partitions for both security and optimization reasons.

Any suggestions, beyond RTFM?

Thanks in advance, all!
-W

---

### Post by OldManAP on 2011-01-26
To give more information on my computing habits, I mostly use this machine to browse the Web, check emails, edit documents, listen to music (although very little of my CD library has actually been ripped to my HD), and occasional tinkering with audio recording by way of Ardour, JACK, etc. (mostly live-by-mic stuff, although I'd like to get into some MIDI stuff eventually).

Also, I haven't really dipped into the waters of gaming very much, but I'd like to. Finally, I have fooled around with WINE to some extent, mostly to get a $10 bargain Windows-based game or two that I picked up at Wal-Mart to work, mostly successfully.

I haven't done any VM stuff, but may eventually need to, as I do a fair amount of music composition and orchestration work (or, at least, used to, and would like to get back into it), and I'm way more familiar with the Finale software than just about anyone I know, and don't really want to re-learn a new music scoring program (although I've tried out some of the native Linux offerings, such as MUSE and such, I'd like to stick to Finale for this aspect, and I've never got it to work under WINE, so perhaps a VM solution is gonna be the ticket).

As for my current primary Lucid install, the numbers I'm gonna give are only approximate, as I'm still learning my way around the appropriate terminal commands, and I'm mostly going by what the graphical tools tell me within Gnome, but here goes, as of a few minutes ago (by way of a lot of right-clicking and selecting "Properties"):

BTW, this is from a default installation, where the installer sizes Swap as it wants, and then everything else goes into /

/ = pretty much everything unknown, as I'm not yet savvy enough to get around the permissions handling
/boot = 99.9 MB
Swap = the installer set this to ~3.1 GB
/home is at 8.5 GB with some contents unreadable
/tmp is at 49.9 KB with some contents unreadable
/usr is at 2.9 GB
/var is at 599.3 MB with some contents unreadable
/opt contains nothing
/usr/local is at 395.0 KB

Does that help explain my needs at all? I'm not sure what will help me and my "dream system" the most, so please advise!
-W

---

