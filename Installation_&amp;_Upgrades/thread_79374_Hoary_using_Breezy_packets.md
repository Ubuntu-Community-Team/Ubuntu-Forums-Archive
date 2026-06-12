---
title: "Hoary using Breezy packets"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by WOteB on 2005-10-20
Hello,

Updating Hoary > Breezy en new-installing Breezy is a nightmare. No X-server, no reboots (hangs on hotplug subsystem), no DHCP when installing etc, no correct keyboard layout (US - deathkeys) etc.
So, I want to continue Hoary, but want to use some Breezy packets like OpenOffice-2. Is it possible to use the Breezy CD's (Ubuntu and Kubuntu) for instaling them on my Hoary systems, just like a partial upgrade for some packets?

I'm missing a normal upgrade possibility on de (K)Ubunu install CD's like Red Hat and Fedora have.

I'm using Hoary Kubuntu installed from the regular Ubuntu CD, after that installed kubuntu-desktop and removed the ubuntu-desktop.

---

### Post by XjFrank on 2005-10-20
Same.  I upgraded to 5.10 and it didn't work out well for me.  So I have freshly reinstalled Hoary, gotten VMWare back in order, and am wondering how I can get those php5 packages on this machine?  Open Office 2.0 would also be nice, since now that it supports the new format I can begin my attempts to get that into the enterprise baseline here as well.  I downloaded OO2 and it's a bunch of RPMs (great if I were in RedHat).  I'd like to do this using ubuntu's install system.
...Frank

---

### Post by WOteB on 2005-10-20
I'm Happy with using Paragon Backup (also Linux...), so I can quickly restore the complete partition with the Hoary Kubuntu... ;)

An additional question: Is it possible to extend the /etc/apt/sources,list with the Breezy lines? Or isn't possible to use a hybrid Hoary/Breezy system?

---

### Post by XjFrank on 2005-10-20
I'll let you know tonight.  I'm going to try since the upgrade method was to replace hoary with breezy in that sources file perhaps if I add them rather than change them I can get the php5 packages installed.  If not, then I have to compile it myself.  If that's the case, then this becomes trickier.  I don't want to go through a long process of seeing what ./configure complains about not having installed one development tool at a time until I can compile.

Anyone know a nice apt-get developers-baseline-tools sort of trick to snag it all in one scoop?  

Very good "user's" linux distro.  And a savior for one project I had to migrate when FC4 planted itself firmly on its face with my graphics adapter.  Of course, the upgrade experience to 5.10 wasn't fun.  But I'm back to stable on the old rev, and now I need my tools and I'm a developer and not a sysadmin-type and on top of that this is my first real time in a debian-based distro so I need the help of some with more experience in configuring a solid developer's baseline.

I need apache (which I have up and running from synaptic), php 5 (working on it, hoping to simply install it with synaptic as well), MySQL 5 when it comes out (finally support for enough of what we use in oracle that I may be able to migrate one AIS off of an oracle internet license and actually allow us to return two cpus back into the box that were disabled due to Oracle's pricing), and the new Open Office (I do govt contracts, and I'd love to see things swing more in the OSS direction).  

...Frank

---

### Post by Kyral on 2005-10-20
[quote=XjFrank]I'll let you know tonight. I'm going to try since the upgrade method was to replace hoary with breezy in that sources file perhaps if I add them rather than change them I can get the php5 packages installed. If not, then I have to compile it myself. If that's the case, then this becomes trickier. I don't want to go through a long process of seeing what ./configure complains about not having installed one development tool at a time until I can compile.

Anyone know a nice apt-get developers-baseline-tools sort of trick to snag it all in one scoop?  

Very good "user's" linux distro. And a savior for one project I had to migrate when FC4 planted itself firmly on its face with my graphics adapter. Of course, the upgrade experience to 5.10 wasn't fun. But I'm back to stable on the old rev, and now I need my tools and I'm a developer and not a sysadmin-type and on top of that this is my first real time in a debian-based distro so I need the help of some with more experience in configuring a solid developer's baseline.

I need apache (which I have up and running from synaptic), php 5 (working on it, hoping to simply install it with synaptic as well), MySQL 5 when it comes out (finally support for enough of what we use in oracle that I may be able to migrate one AIS off of an oracle internet license and actually allow us to return two cpus back into the box that were disabled due to Oracle's pricing), and the new Open Office (I do govt contracts, and I'd love to see things swing more in the OSS direction). 

...Frank[/quote]

Sounds like you are trying to build a server yes? They just released a Breezy Server Edition that comes with LAMP preinstalled, or so I have heard

---

### Post by WOteB on 2005-10-20
[QUOTE=XjFrank]Anyone know a nice apt-get developers-baseline-tools sort of trick to snag it all in one scoop?  
[/QUOTE]

I'm using MC (Midnight Commander) for that. Very nice tool. Just copy lines and change them. But I'm very curious about your experience with your mixed sources.list.

---

### Post by XjFrank on 2005-10-20
I changed Hoary to Breezy and this time rather than shoot to upgrade the entire system I just upgraded gcc, added the newer xml tools and libraries that I found in a synamptic search (which indicated it was definately going against breezy), upgraded to php 5.0.5 through it, added pear, and a few other minor things.  So far it's going well, there is some config I need to do to load the php modules in apache and setup the ports and servers for the different parts of this.

The mention of a server version of this interests me and I'm going to look into that, but if all of the php and extensions plus xml work then I'm running with this setup until I get this next rev out the door.  

So, to conclude, I think that if you choose to point a Hoary base at the Breezy stuff and keep what you decide to upgrade reasonable you can bridge the gap while the hangups with the upgrade get figured out.  I'll let you know once I'm actually coding and running on it if it all worked out as well as I've found thus far.


...Frank

---

### Post by XjFrank on 2005-10-21
Ok.  I have php running under apache, all the pear and pecl extensions I use setup, and am doing well.

I had to change the apache config to load php (to be expected), I had to change the gcc link to point to the newer gcc, and the php link to point to the newer version of php, both by hand.

The only thing that broke (that I noticed) is gksudo which is used by the root prompt terminal window launcher and the add/remove programs app (both of these on the menu).  I pretty much launched everything else I have on the menu at least once to check.  That's about as far as I went before moving on to my code.

So, I'm running a hoary/breezy mix now.  (Really just Hoary with updates on what matters to me)

...Frank

---

### Post by WOteB on 2005-10-21
Hi Frank,

Nice to hear it's working, but I've a question:

Do you use a mutated /etc/apt/sources.list (with the breezy line appended), or are you using a (K)Ubuntu CD, or both?

Willem

---

