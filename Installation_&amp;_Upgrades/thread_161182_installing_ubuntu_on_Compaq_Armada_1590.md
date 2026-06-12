---
title: "installing ubuntu on Compaq Armada 1590"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by mancunianweather on 2006-04-16
Hi!

I'm completely new here, and new to linux too , but I was wondering if anyone could help me (or direct me towards some helping) in installing ubuntu on a compaq armada 1590DT laptop., as Ubuntu seems to have trouble doing so automatically (I know - I think - that there are some issuses regarding drivers, but being pretty much a complete ignorant in hardware matters that's the (pathetic) extent of my understanding... :( )

Anyway, I hope I've posted this thread in the right place/sub-forum (I've put it in the wrong sub-forum to start with methinks :-k ), and I'd be very grateful indeed for any answers to my problem! :D

---

### Post by cilynx on 2006-04-16
TuxMobile has a couple of entries for the 1592.  I bet the specs are pretty similar.  Where is the install dying on you?

[http://tuxmobil.org/compaq.html]("http://tuxmobil.org/compaq.html")

---

### Post by mancunianweather on 2006-04-16
Thanks a lot for your reply!!

Will be checking Tuxmobil's site for info as you suggested (though how much I'll be able to understand is another question!  :-?  )

The install goes through detecting hardware fine (in Low memory mode, given the specs of the laptop). It dies when loading installer components:

md-modules-2.6.12-9-386-di

"failed for unknown reasons. Aborting"

Much more than that - or what it means (my knowledge being pretty pitiful) I don't know :(

Thanks in any case for your reply, it is greatly appreciated! :D

---

### Post by cilynx on 2006-04-16
The md-modules are RAID and LVM crap for the install system.  If you're not using RAID or LVM (which you're probably not on a low-spec laptop), then you don't need them.  I think Ubuntu wants to use LVM by default.  You can choose not to when setting up your hard drive.  Choose the option that isn't LVM =)

---

### Post by mancunianweather on 2006-04-16
Thanks, though being an illiterate I'm not too sure what to do with the info! :confused: :( ](*,) 

I think the hard drive is already partitioned (does that make sense?), so I'm not too sure at what stage of the installation process I'm supposed to set it up...


Sorry for being so useless! :???:

---

### Post by cilynx on 2006-04-16
Welcome to Linux =)

Are you dual booting or just doing Linux?

Does the installer make it so far as "setting up your hard drive"?  If so, it should give you some options: resize, use all, use all LVM, and maybe some others.  You want "use all" without LVM.

Some terminology:

LVM: Logical Volume Manager.  A reasonably new theory in partitioning.  I don't know much about it other than it makes resizing partitions easier later.

RAID: Redundant Array of Inexpensive Disks.  Basically, you get a bunch of cheap hard drives and kludge them together into one big one.  You don't have this on your laptop, trust me.

How much RAM does the machine have?
Does it get to the point of asking if you want to do a 'server' or 'desktop' install?  If so, try choosing 'server' and see where that gets you.

You may want to look into [UbuntuLite]("http://www.ubuntulite.org") or [Xubuntu]("https://wiki.ubuntu.org/Xubuntu").  They're both designed to run well on older hardware.

---

### Post by mancunianweather on 2006-04-17
Thanks for your reply! :)


> 
Are you dual booting or just doing Linux?


Just doing Linux. I used to have win98 but I re-formatted the hard-drive.

> 
Does the installer make it so far as "setting up your hard drive"? If so, it should give you some options: resize, use all, use all LVM, and maybe some others. You want "use all" without LVM.


Thanks for the precision, though sadly I don't make it that far! The only option I'm given at the beginning is whether to do a standard install, a base install (server) or an expert install. I tried the server install (as you suggested) and got the same result.. this md-module doesn't seem to get along with my laptop ;) :( 

....

> 
How much RAM does the machine have?


Here are the specs
Compaq Armada 1590DT
Processor: Pentium (166 MHz)
RAM: 80 Mb
HDD: 4.3 Gb

Errrr... That's all I know!

Thanks a lot again for your help.... Will have a look into Xubuntu and UbuntuLite. Though I'm bugged by not being able to do even the simplest install on a computer - I know I'm rubbish but still! ](*,) :D

---

### Post by cilynx on 2006-04-17
No worries.  It's quite common that high-end operating systems don't get along with older hardware.  Give one of the light-weight distros a shot and let us know how it goes.

---

### Post by allenlux on 2006-04-30
Can I try reviving this thread? I have a very similar Compaq Armada:

Model: 1598DT
RAM: 32MB
CPU: Pentium 233
HD: 3 GB

I'm seeing the same problem: the Ubuntu 5.10 installer crashes on the step "unpacking md-modules....".

I'd like to find an installation option which bypasses the loading of md-modules: any idea if there is such an option? I only need a server installation, and I have already set up appropriate partitions on the hard disk.

I've also tried the Ubuntu Dapper Flight 6 installation, but this also crashes, for reasons that are unclear.

Knoppix and DSL-N run with no problems (as Live CDs).

---

### Post by cilynx on 2006-04-30
What does the Dapper Live CD do for you?  

You say the Dapper Install crash is "unclear"...does it give you any ouput or hang anywhere in particular?

---

### Post by allenlux on 2006-04-30
I haven't tried the Dapper Live CD, only the installation CD.

As I recall, the Dapper Install crash occurred well into the installation, during the phase "copying kernel". It got up to around 83% on the progress bar, then nothing more happened. After half an hour I pulled the plug and started over with another distribution.

I'm aware that 32MB RAM is very low. I'm wondering if the 2.6.x kernel is just too big (the Knoppix LiveCD uses a 2.4 series kernel).

---

