---
title: "BUG: soft lockup - cpu #0 stuck for 11s [modprobe:1282]"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by vluhd on 2008-10-01
Hi,
Whenever i start ubuntu (8.04) i get the following message:
BUG: soft lockup - cpu #0 stuck for 11s [modprobe:1282]

i have no idea what to do.
no matter how i install/attempt to run ubuntu the same thing happens.

this installation was installed through windows, but whenever i try to run the installation/live cd the same thing happens.

---

### Post by vluhd on 2008-10-01
i just tried 8.1 intrepid.
that doesnt work either.
but instead of actually giving me an error message, it just does nothing. it never gets past the boot splash screen. it just shows the splash, and freezes.

---

### Post by Partyboi2 on 2008-10-01
Go back to trying the hardy cd, when you get to the main menu press F6 and remove  splash and add ```
noapic
``` to the end of the line and press enter and see what happens.

---

### Post by vluhd on 2008-10-01
now it says:
PCI: BIOS BUG #81 [49435000] found
Loading, please wait...
BUG: soft lockup - CPU#1 stuck for 11s! [modprobe:1262]

---

### Post by vluhd on 2008-10-02
come on, this cant be unsolvable.
also, i tried 64-bit last night.
same deal.

---

### Post by Partyboi2 on 2008-10-02
Try updating your bios if you are able to.

---

### Post by vluhd on 2008-10-03
There are no BIOS updates available.
Acer doesn't support this model very well at all.

---

### Post by prostar on 2008-10-03
> **vluhd said:**
> There are no BIOS updates available.
Acer doesn't support this model very well at all.

Which Acer model do you have?  Also if you post your BIOS type (or motherboard type) someone might know more ways to help you.

---

### Post by vluhd on 2008-10-03
acer aspire 5430
my system bios are pheonix bios version 1.3309 (this is stated within the bios)
when i start it up the first thing it says is pheonix bios 4.0 release 6.1
right after that it tells me the following: BIOS Revision BOWFIN BIOS BW-B16-16Feb2006-BR17213(rev8.050I.000)

---

### Post by Partyboi2 on 2008-10-03
Are you trying to install the 64bit version or 32bit version of ubuntu?

---

### Post by vluhd on 2008-10-04
i would prefer to install the 32 bit version, but i was trying the 64 bit version to make sure it didnt work as well.
so yes, im trying to install the 32 bit version.

---

### Post by vluhd on 2008-10-06
im not sure if it makes a difference in the situation, but i tried installing a bunch of other distros of linux, none worked.
i tried fedora, knoppix, backtrack, mandrake, i even tried solaris.
however, there was one that worked, DSL.

---

### Post by vluhd on 2008-10-07
bump because id like to not have vista anymore..

---

### Post by Partyboi2 on 2008-10-07
Try using some different boot options by themselves and in different combinations
no_timer_check
noapic 
nolapic 
acpi=off
Someone else had success with a similar problem by removing quiet and splash from the boot options.

---

### Post by JustinThomas on 2008-10-09
Same problem here with Ubuntu 8.04 on my Xen server.  I tried removing quiet and splash, setting acpi=off, noacpi, etc. - none work.

The (temporary) solution for me was to change my CPUs to 1.  This appears to be an issue with SMP.  As soon as I bump the CPU count to 2 (or 4 as I'd like to use all 4 cores in my dual socket, dual core system), I start getting these lockups.

When I use a Debian Etch install on the same host, I have no problems with using all 4 CPUs.  This appears to be unique to the Ubuntu kernel 2.6.24-19.  Apparently 2.6.24-18 is un-afflicted.

Take a look at this board:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/245779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/245779)

---

### Post by Partyboi2 on 2008-10-10
Maybe you could try intrepid and see if the problem presists. You can either wait for a few more weeks till its release or you could download  intrepid beta.
[http://releases.ubuntu.com/releases/8.10/](http://releases.ubuntu.com/releases/8.10/)

---

### Post by vluhd on 2008-10-15
as of right now 8.1 isnt helping.
i just downloaded it again and tried it.
not exactly the same prioblem, but similar.
this time im told the following:
BUG: soft lockup - CPU#0 stuck for 61s! [modprobe:5228]
BUG: soft lockup - CPU#1 stuck for 61s! [kstop0:5298]

---

### Post by Partyboi2 on 2008-10-15
Have you tried what is mentioned in post #15 by JustinThomas, and change your cpu's to 1?

---

### Post by lores on 2008-10-17
Hello!
On my notebook, HP 6720s CoreDuo, I have a similar problem: I get the "CPU stuck" message, yet it occurs only sometimes, ie. sometimes I can boot properly with no error and sometimes Ubu gets stuck and I have to hard-restart. WTF? :D

Ubuntu 8.04.1 fully up-to-date (previously only important + recommended, now also proposed - in both cases same problem - 2.6.24-19 and 2.6.24-21).

PS It didn't happen before at all or happened very, very rarely (not sure now).

---

### Post by vluhd on 2008-10-20
wel, i cant do it anywhere in my bios, but as soon as  can ill try the bootline code and see if that works.
i cant lie, i have my doubts, but ill give it a shot.

---

### Post by vluhd on 2008-10-20
yeah, i tried the only discernable thing, NO_HZ=y
no luck, exact same results.
is there some way to tell ubuntu to only use one core when booting? maybe that would help?

i just want to clarify this a little better.
every post i find on this seems to be a description of how ubuntu would crash after a while of uptime. this is not the case for me. it doesnt boot, at all, ever.
the only thing i can do to change anything is edit the boot code.

---

### Post by lores on 2008-10-23
Well, there's the option concurrency=shell in /etc/init.d/rc to enable 2core booting, but it's disabled by default - unless You somehow got it enabled, it won't help; however - worth a try...

---

### Post by vluhd on 2008-10-25
well, ive never had ubuntu installed on my laptop, so im going to go ahead and assume it's not enabeled.
but then could you explain why it says that both of my cores soft-lock when booting the 8.1 setup?

---

### Post by lores on 2008-10-25
It's really weird... :/
Additionally, on my laptop (6720s), I've gotten this error just a few times, though I've been booting into Ubuntu plenty of times every day...

---

### Post by dmm1000 on 2010-11-06
Hi Everyone
i had the same problem installing 10.04 on a A7N8XE motherboard getting the same error message but i downloaded 10.10 and installed it witout problems so this bug seems to be fixed (for me anyway) in 10.10 

hope this helps

---

### Post by Ice.Singapore on 2010-12-10
[RIGHT][BUG: soft lockup -  cpu #0 stuck for 11s [modprobe:1282]]("http://ubuntuforums.org/showthread.php?t=935396") 		Reply to Thread  	I have many these message ,And I can't boot into my ubuntu10.04
[/RIGHT]

---

