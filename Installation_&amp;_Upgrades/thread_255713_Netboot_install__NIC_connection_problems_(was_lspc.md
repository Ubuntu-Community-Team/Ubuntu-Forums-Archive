---
title: "Netboot install:  NIC connection problems (was: lspci returns NOTHING.)"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by bunglerJ on 2006-09-11
My problem started off as what I thought was a Networking problem.  I've recently installed Ubuntu 606 on an oldish Tyan Dual P3 board.  I've searched high and low and tried a total of 6 differrent NIC's to no avail.  Durring all the threads I've seen they ask the user to do lspci and then tell them what to do when it detects their card.  What do I do if lspci returns nothing?  Does this mean that my NIC (all 6 of them) are bad or does this mean they simply aren't detected?  If the latter is true then how do I get them to "detect"?

The NIC I started with and the one I've put the most effort to get working is a PCI 3com 3c905c.

I'm a bit frustrated at this point as this is day two working on this problem so please forgive me if I sound vexed.  I'm very strong with Windows and I don't think I've ever worked this hard before to do something like install a NIC.  Please help. ](*,) 

I guess it is still possible my NIC is bad so I won't rule that out but can anyone shine a light on my situation.

---

### Post by dickohead on 2006-09-11
Could be a bad PCI slot?

But do see an output from lspci, try 'sudo lspci' and see if that helps.

NICS are usually picked up by default and configured via DHCP automatically, try typing 'ifconfig' and see if you have any eth interfaces.

---

### Post by elvis on 2006-09-11
> **bunglerJ said:**
> What do I do if lspci returns nothing?
Can you expand on this?  lspci returns "nothing" as in completely blank output?  Or it returns all devices EXCEPT for the one you need to look at?

For starters, lspci needs to be run as root as it accesses hardware directly.  So the user needs to run "sudo lspci" to get useful information.

lspci scans the PCI bus looking for PCI and manufacturer serial IDs.  Any devices that are physically present will be reported.  If the device is known to the kernel, it will be represented by the name that the system understands it as.

If however the device is physically connected but unknown to the system, it will report it as an unknown device.  Sometimes with network cards if will report the chipset but also mention it as an unknown provider or manufacturer.

If lscpi shows a list of all your installed hardware but the network cards don't show up, there's a good chance that the card is not installed properly, or is faulty.

Try swapping PCI slots.  Try also forcing an ESCD update via your BIOS.  This will refresh the hardware device table in your BIOS on the next boot.

A PCI 3Com 3c905 is a common-as-mud chip.  Support for it was added to the Linux kernel eons ago.  For it not to work, particularly with Ubuntu/Debain's "load everything under the sun" type module loading is very strange, and hints to me a hardware related issue.

---

### Post by bunglerJ on 2006-09-11
I've tried multiple PCI Slots (this board has 6 slots although I haven't tried every single one).  Card where working in these slots previous to rebuilding the system in a smaller case and putting Ubuntu on it.

As for expanding on lspci returns nothing...  I'm in Terminal and I type sudo lspci.  It asks for root password and I type it and it immediantly returns me to the command line.

I'll try forcing an ESCD update via BIOS as suggested and wait for further comments.  

Thanks for the quick replies.

---

### Post by elvis on 2006-09-11
> **bunglerJ said:**
> As for expanding on lspci returns nothing...  I'm in Terminal and I type sudo lspci.  It asks for root password and I type it and it immediantly returns me to the command line.

OK that's a big problem.  

Do you get the same issue with "sudo lspci -vvvn" ?

I would also consider using the BIOSes "reset to failsafe defaults" option as well (remembering to correctly set your boot order once you've done that).  Something sounds very screwey with either your install or the hardware itself.

---

### Post by bunglerJ on 2006-09-11
I did the force ESCD.  I get the same from sudo lspci -vvvn.  I guess next is reset BIOS to fail-safes and the possibly reinstall(just in case).  I'll report back after that.

---

### Post by bunglerJ on 2006-09-12
Ok.  BIOS Fail safes had not effect.  I'm going to be sitting at this desk for a bit doing the reinstall of the OS.  Anyone have anymore suggestions?

---

### Post by elvis on 2006-09-12
Can you tell me the northbridge chipset of the system?

And does dmesg tell you anything?  Is it successfully picking up any of your other PCI devices?  For example, does sound work?

---

### Post by bunglerJ on 2006-09-12
Just FYI lspci on the live CD does the same thing.  I have no sound card.  Only other card is a usb card and I don't know if that is working.  What if it isn't?

---

### Post by bunglerJ on 2006-09-12
[http://www.tyan.com/products/html/tiger133.html](http://www.tyan.com/products/html/tiger133.html)

Via Apollo Pro 133A.

---

### Post by bunglerJ on 2006-09-12
dmesg spits out tons of stuff.  I can't see anything concerning a 3com nic.  What am I specifically looking for?  I just type dmesg?

---

### Post by elvis on 2006-09-14
The 3c905 uses the "vortex" kernel module.

dmesg | grep -i '3c'
dmesg | grep -i 'vortex'

See what those commands spit out.

---

### Post by bunglerJ on 2006-09-16
I get no output from either of those commands.

dmesg | grep -i '3c' = nothing
dmesg | grep -i 'vortec' = nothing

Should lspci show all installed PCI devices?  Do you have any idea why it would show nothing? aren't things like USB and hard disc controllers built into the motherboard considered PCI devices?

---

### Post by elvis on 2006-09-18
> **bunglerJ said:**
> Should lspci show all installed PCI devices?
Yes.

> **bunglerJ said:**
> Do you have any idea why it would show nothing?
No. :(

> **bunglerJ said:**
> aren't things like USB and hard disc controllers built into the motherboard considered PCI devices?
Yes.  Generally they are either PCI or PCI-Express, either of which should show up under lspci's output.  I'm honestly stumped as to why nothing is showing up for you.

All I can suggest is trying a newer kernel, and hoping that it supports your particular board chipset better?

---

### Post by bunglerJ on 2006-09-18
I have the latest Ubuntu.  Does this not mean that I also have the latest kernel?  Where would a find a newer kernel?  My chipset is very old at this point.  Could I asume that the current kernel is going to have all the support it is ever going to have for my chipset or do they still develop support for old hardware?

Why do I keep wanting to type that word "kernal" instead of "kernel"?

---

### Post by bunglerJ on 2006-09-21
Bump.  New Kernel?  Where?

---

### Post by Brunellus on 2006-09-21
> **bunglerJ said:**
> I have the latest Ubuntu.  Does this not mean that I also have the latest kernel?  Where would a find a newer kernel?  My chipset is very old at this point.  Could I asume that the current kernel is going to have all the support it is ever going to have for my chipset or do they still develop support for old hardware?

Why do I keep wanting to type that word "kernal" instead of "kernel"?
kernel updates are part of the usual set of ubuntu periodic updates.  

Have you tried booting into your old kernels and figuring out which was the 'last good' one?

---

### Post by bunglerJ on 2006-09-22
This is a fresh install from the disk burned from the ISO I just downloaded days ago.  There are no previous kernels.

I tried to apt-get the 686-smp kernel since I'm mutliprocessor but it said package not found.  I then tried to get the 686 kernel cause I thought that might help over the 386 kernel but I got the same error: package not found.  I tried to update apt-get but I can't because I have no working network card (ROOT OF THIS PROBLEM).

---

### Post by Brunellus on 2006-09-22
> **bunglerJ said:**
> This is a fresh install from the disk burned from the ISO I just downloaded days ago.  There are no previous kernels.

I tried to apt-get the 686-smp kernel since I'm mutliprocessor but it said package not found.  I then tried to get the 686 kernel cause I thought that might help over the 386 kernel but I got the same error: package not found.  I tried to update apt-get but I can't because I have no working network card (ROOT OF THIS PROBLEM).
I had some issues with the stock Dapper kernel on some older hardware--no PCMCIA services.  Very strange.  

A breezy livecd, however, ran flawlessly, which suggested a possible fix:

The fix went like this:

1) Install BREEZY...but only the "server" version.

2) change all references to 'breezy' to 'dapper' in /etc/apt/sources.list

3) Dist-upgrade to Dapper online.  More recent kernels seem to have fixed this particular issue:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

4) now install the desktop package of your choice:  

sudo aptitude install ubuntu-desktop

OR

sudo aptitude install kubuntu-desktop

OR

sudo aptitude install xubuntu-desktop

---

### Post by bunglerJ on 2006-09-22
Found a mirror ([http://espelhos.edugraf.ufsc.br/ubuntu-releases/5.10/](http://espelhos.edugraf.ufsc.br/ubuntu-releases/5.10/)).  Getting breezy.  I'll updated with results.  Thanks.

---

### Post by bunglerJ on 2006-09-22
During the Breezy install it pics up my NIC but tells me it can't configure it.  I can't get it to get an address via DHCP.  DHCP is being supplied by a Smoothwall box connected to a hub.  My Windows PC gets DHCP from it just fine.  I've selected the option to not configure the network but I assume this means I won't be able to do apt-get update.  Any ideas?

---

### Post by Brunellus on 2006-09-22
> **bunglerJ said:**
> During the Breezy install it pics up my NIC but tells me it can't configure it.  I can't get it to get an address via DHCP.  DHCP is being supplied by a Smoothwall box connected to a hub.  My Windows PC gets DHCP from it just fine.  I've selected the option to not configure the network but I assume this means I won't be able to do apt-get update.  Any ideas?
try specifying an IP for it manually, and attempting a dist-upgrade that way.

---

### Post by bunglerJ on 2006-09-22
Could you shed some light on how I might "2) change all references to 'breezy' to 'dapper' in /etc/apt/sources.list" from the command line?  I am a total linux noob.  It's kinda hard to learn it if I can't get it installed.

UPDATE:  Guess I'm to use nano and I'm reading a how to on that now.

---

### Post by bunglerJ on 2006-09-22
Ok.  I can work with Nano but could you still elaborate on the "change references to breezy to dapper" part.  Like the first line says 5.10 _Breezy Badger_.  Should I change that line?  Should I simply change all instences of the word breezy to dapper?  Should I uncomment any lines?

---

### Post by Brunellus on 2006-09-22
yes.  all instances of "breezy" should now be changed to "dapper."  

You don't have to uncomment the universe and multiverse lines just now if you don't want to, but I imagine you'll want them after the update, anyway.

---

### Post by bunglerJ on 2006-09-22
Hrrmmmm...  cdrom line at top of sources.list kept erroring so I commented it out.  I added:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted 
at the top (found in another post).  I ran sudo apt-get update and I get > Temporary Failure resolving 'us.archive.ubuntu.com' on most of the lines.

This looks like a network connection issue so I did a ping to 192.168.0.1 (which is my smoothwall address).  I'm getting 53% packet loss to a local address.  This hardware all works in Windows.  I'm at a loss.  Flaky hardware?  Bad driver?  Ideas?

UPDATE:  I've tried 2 other NICs (one the same kind and the other a Kingston card), different networking cables, and move everything from the little 4 port hub I have to my big switch and I still have the same problem.  I tried hitting us.archive.ubuntu.com from my windows PC and it worked fine.

---

### Post by Brunellus on 2006-09-22
> **bunglerJ said:**
> Hrrmmmm...  cdrom line at top of sources.list kept erroring so I commented it out.  I added:

at the top (found in another post).  I ran sudo apt-get update and I get  on most of the lines.

This looks like a network connection issue so I did a ping to 192.168.0.1 (which is my smoothwall address).  I'm getting 53% packet loss to a local address.  This hardware all works in Windows.  I'm at a loss.  Flaky hardware?  Bad driver?  Ideas?

UPDATE:  I've tried 2 other NICs (one the same kind and the other a Kingston card), different networking cables, and move everything from the little 4 port hub I have to my big switch and I still have the same problem.  I tried hitting us.archive.ubuntu.com from my windows PC and it worked fine.
now you've got me stumped.  I'm going to move this to the general Install/upgrade support forum and see if the regulars there have anything to say about it.  I'm also changing the thread title to reflect where we are and what the issue is.

---

### Post by bunglerJ on 2006-09-22
Thank you and the other posters very very much for all the help.  I look forward to other views on this.

I'm going to try to further eliminate hardware as a possible cause by trying a couple of other NIC's.  Is there anything special I should do when installing a new NIC?  Should Ubuntu pic up most of the common NICs?  Am I hurting anything by doing this (like in Windows where drivers and stuff are left cluttering the system)?

---

### Post by bunglerJ on 2006-09-23
UPDATE:
Ok.  After testing I've put in 7 different NICs (one ISA).  5 of them where detected by the OS and all of them exhibited the same problems.  I have a friend who I consider Linux savy and I asked him about it and he could give no answer.  He recomended CentOS as that is what he is using and familar with.  I downloaded CentOS and booted off the Live CD.  I was able to get on the internet just fine which means that under CentOS even DHCP worked (it doesn't work under Ubuntu).  I think at this point I've proven beyond a shadow of a doubt (atleast to myself) that this is not a hardware issue.

---

### Post by K.Mandla on 2006-09-23
I was going to suggest a completely different kernel version and/or a different distro. Perhaps dropping back to slackware and the 2.4 kernel would help.

I ran into the PCMCIA issues Brunellus mentioned on an old laptop, and like some others, I managed to circumvent the issue by moving back to 2.4 under Slack 10.

Aside from that, my only other suggestion would be to completely rearrange the PCI cards and see if that helps detection.

But not getting ANYTHING out of lspci would be scary to start with.

Well, I doubt I really helped anything. Just another $0.02, I suppose. Good luck. ...

---

### Post by bunglerJ on 2006-09-24
To sum up the current issue:
Moving from Dapper to Breezy helped detection.  My problem now is use.  The network card is detected and loopback pings and pings to its static assinged address work fine.  It fails to ping my router.  If I set it to DHCP it fails to obtain an address.  Under CentOS and Windows it's fine.  And this problem occurs accross multiple NIC's in different PCI slots on different network cables. 

I guess I could choose another distro but doing that seems like I've failed.  I'm savy in Windows and I can't imagine saying, "well my PC should be able to run this OS but it gets this error so I'll have to go back to 2k or NT".  I'd just find a fix.  I'm not savy enough in Linux to "find a fix" and going backward would just seem like giving up.  I guess if this is supposed to replace Windows for me then I'd expect it to do better (and oh how I want so badly for this to replace Windows).

---

### Post by Brunellus on 2006-09-24
> **bunglerJ said:**
> To sum up the current issue:
Moving from Dapper to Breezy helped detection.  My problem now is use.  The network card is detected and loopback pings and pings to its static assinged address work fine.  It fails to ping my router.  If I set it to DHCP it fails to obtain an address.  Under CentOS and Windows it's fine.  And this problem occurs accross multiple NIC's in different PCI slots on different network cables. 

I guess I could choose another distro but doing that seems like I've failed.  I'm savy in Windows and I can't imagine saying, "well my PC should be able to run this OS but it gets this error so I'll have to go back to 2k or NT".  I'd just find a fix.  I'm not savy enough in Linux to "find a fix" and going backward would just seem like giving up.  I guess if this is supposed to replace Windows for me then I'd expect it to do better (and oh how I want so badly for this to replace Windows).
I wish I had an answer for you, I really do.  But it seems that there's some funky hardware/kernel voodoo going on that I don't really understand.

If CentOS works for you, and if it does what you need it to do...well, move to CentOS.  Software is nothing but a solution to a problem, and if this solution doesn't match your set of problems, it'd be irrational to keep with it.

---

### Post by K.Mandla on 2006-09-27
> **bunglerJ said:**
> I guess if this is supposed to replace Windows for me then I'd expect it to do better (and oh how I want so badly for this to replace Windows).
What if you used another Debian-based distro, or even Debian itself? This sounds like a massive step sideways, but if you can get it to work under another Debian variation, you can jump to the Ubuntu repositories and more-or-less use Ubuntu. I've done that with Dreamlinux.

---

### Post by bunglerJ on 2006-09-27
> **Brunellus said:**
> ...funky hardware/kernel voodoo going on...
If CentOS works for you, and if it does what you need it to do...well, move to CentOS.  Software is nothing but a solution to a problem, and if this solution doesn't match your set of problems, it'd be irrational to keep with it.

But...but...CentOS is ... ugly ... and Ubuntu is so purty.  I'm thinking the other suggestion to try some other debian may be my next step.  At any rate if that is the case then I guess this thread has ended as I would then seek support on some other non Ubuntu forums.  Thanks for everything.

---

### Post by Brunellus on 2006-09-27
> **bunglerJ said:**
> But...but...CentOS is ... ugly ... and Ubuntu is so purty.  I'm thinking the other suggestion to try some other debian may be my next step.  At any rate if that is the case then I guess this thread has ended as I would then seek support on some other non Ubuntu forums.  Thanks for everything.
We'll still be happy to have you around...even if it is in the "other OS talk" forum.

There are plenty of other distro users here.  Arch, Suse, and Gentoo seem to be the popular "other" distros.

---

### Post by aethos on 2006-09-29
This is the only place I've been able to find someone discussion this issue. I'm troubleshooting it right now and working on a couple kernel compiles to see if I can figure out what's happening.

The short is that the kernel is not detecting the PCI bus on the Tyan Tiger 133. No one is crazy so set yourselves at ease. So far it looks like Ubuntu, FC5 and Gentoo 2006.1 are all affected.

I'm wondering if it might have to do with recent changes over the order of priority in detecting the PCI bus. (With 2.6.15-17 there have been changes.) Meh.

---

### Post by aethos on 2006-09-29
The problem starts with kernel 2.6.12. Kernel 2.6.11 works without any trouble that I can see. (Cards are seen and networking works.) I 2.6.12 networking stops working on this board and after 2.6.15 the PCI bus will not be recogized. I have a thread posted on kerneltrap so hopefully someone will recognize the symptoms.

---

### Post by bunglerJ on 2006-09-30
So there is hope for this problem.  Thank you for looking into it.  Will you keep updating us here or should we follow the troubleshooting process at another thread?

---

### Post by aethos on 2006-10-02
Well, [this]("http://kerneltrap.org/node/7179") is the thread I started on kerneltrap but after 189 views no one has had anything to say. The change logs are huge so I'm wondering if it's not going to come down to reverting each change individually to see where it stops working. I hope to god that's not the case.

---

### Post by jomikl on 2006-10-16
i think i found a solution.

i have the exact same motherboard, and the exact same nic. and i had the exact same problem. (lspci did not say a thing)

what i did was disable "acpi function" in the bios and also said "pnp os" = "yes" (but that might not be necessary). and after that lspci told me everything i needed to know (and even without "sudo")

that seems to have been the problem.

hope that helps,
jomikl

ps: i am installing ubuntu 6.10 beta while i am writing this - i'll report back when its done
pps: its done and works flawlessly (kernel 2.6.17-something) - network and everything

---

### Post by aethos on 2006-10-28
You're right about disabling ACPI function. That will make it work. I also came up with a kernel config that works with later configs. Interesting bug. Not sure if it's worth looking for a fix in the kernel itself...?

---

