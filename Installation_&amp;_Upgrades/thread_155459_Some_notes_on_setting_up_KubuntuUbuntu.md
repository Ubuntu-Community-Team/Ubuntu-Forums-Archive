---
title: "Some notes on setting up Kubuntu/Ubuntu"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by jkeirstead on 2006-04-05
Hi,

I've been running Kubuntu for a week now and really like it so I wanted to make a contribution to the community.  This post, which I'll probably add bits and pieces to as I go along, describes all the things I had to do to get Kubuntu running the way I thought it should.  It should hopefully be a useful reference to other new users and flag things that developers might want to consider for future releases (i.e. not a separate script but core part of the system, can't it just be packaged like anything else?)

**[SIZE="3"]My previous Linux experience[/SIZE]**
A year and half running [Yoper 2.1]("http://www.yoper.com") as my home system on the same laptop.  Had numerous teething problems with it, i.e. compiling wireless support from scratch, coping with poor packaging etc.

**[SIZE="3"]My setup[/SIZE]**
Dell Inspiron 8100 laptop, NVidia GeForce 2 video card, D-Link 650+ TI acx-100 wireless card, Freecom FHD-3 USB2/Firewire External Hard Drive.  

Installed Kubuntu 5.10 Breezy

**[SIZE="3"]Installation tweaks[/SIZE]**
These are the steps that I had to take following the basic installation.  I've tried to list them in order with relevant details.

[LIST=1]
[*]**Adding universe multiverse** Like many of the initial set-up steps, a quick Google will turn up a useful page like [this one]("https://wiki.ubuntu.com/AddingRepositoriesHowto").  But again, couldn't this just be a tick box somewhere?
[*]**Automatix, mp3s etc**  When I first booted up, I obviously wanted some tunes while I tinkered.  I had heard about [automatix ]("http://www.ubuntuforums.org/showthread.php?t=138405")before installing, so I immediately went and downloaded the script.  It worked great and I soon had all the necessary bits and pieces.  Some complaints though:
[LIST]
[*]*MIDI doesn't work* Timidity's installed and everything but can't seem to play a MIDI file yet.  Forum searching suggests I might need a soundfont installed.  Need to check this one more myself but to my mind, shouldn't you just be able to install MIDI support and immediately open a midi file from konqueror to play it?
[*]*Ugly firefox 1.5* Was the automatix package compiled with some library I don't have?  It looks like an old gtk app with no adherence to KDE's general look and feel.  Might be better on Gnome. 
[/LIST]
Apart from these minor things, Automatix is great.  Hope it's an integral part of future releases.

[*]**Stuttering sound**  Eventually I did get around to playing an mp3 and it worked fine for the first few seconds before stuttering.  I poked around and amaroK's help suggested playing with the buffer settings.  Small improvement but in the end what appears to have fixed it is some combination of the powernowd fix below and installing the 686 kernel.  It would be great if after a fresh install, Ubuntu could scan your system and pop up a notice saying something like "I see you're running a PIII or better.  Would you like to install the 686 kernel since it'll make your life easier?''

[*]**NVidia** Automatix can also install the proprietary NVidia drivers.  It did this fine but for some reason the driver made all the text in KDE twice as big.  Overall resolution was still the same and text settings still said 12pt DejaVu etc. but the text was huge.  I haven't sorted this out yet so I'm using the default nv driver.

[*]**Powernowd** In addition to the stuttering tunes, the mouse wasn't moving smoothly and the syslog was full of messages about having problems with the cpu frequency.  I found a thread that said to install cpufreqd from Adept instead of powernowd.  That worked but looking at [this thread]("http://www.ubuntuforums.org/showthread.php?t=75598&highlight=powernowd") there may be a more subtle fix.

[*]**Slow internet** See [this thread]("http://ubuntuforums.org/showthread.php?t=87798&page=4") for how to turn off ipv6.  Couldn't this just be a tickbox in the settings somewhere?

[*]**Couldn't mount external hard drive at boot** I added my external hard drive to /etc/fstab and from the command line, I could mount it no problem with a mount -a.  The fstab entry doesn't have noauto in it but every time I'd boot, the "Mounting external filesystems" line would fail.  Turns out the necessary modules aren't installed by the time the boot process tries to mount the drive.  The general fix is to a) mount it manually b) do a lsmod and see what modules are used by the device (in my case, sd_mod, ieee1394, scsi_mod and a couple others - I'll check at home tonight)  c) add these modules to /etc/modules.  Works like a charm. 

[*]**Kubuntu only, Konsole font issue** Good grief.  I know this is an easy fix (just pick a different font from the settings menu) but how on earth did overlapping "monospaced" fonts make it into one of the most important apps on the system?! 
[/LIST]

**[SIZE="3"]Good things[/SIZE]**
Just so it's not all bad news, some of the great features I've found.
[LIST]
[*]KDE-look sync for wallpapers, splashes, etc.  Lovely!
[*]Wireless just works! Except that I can't find anywhere in KDE to change my settings so I had to manually change the tx power from the command line.
[*]Easy upgrading.  Ran the Adept Upgrade tool after installing and got KDE 3.5 with no fuss - wonderful!
[/LIST]

So basically Kubuntu/Ubuntu is brilliant and I've noticed a big difference from the smaller Yoper distribution.  However these fiddly little things are a big turn-off to new users and it would be great if some more polish could be applied to these major issues.  For example, with the non-free mp3/DVD codecs, couldn't it just be a package in the repository with a big disclaimer on it, saying "Are you sure this is legal where you are?"?  If the player software then beeped the first time and said "You don't have mp3 support installed.  Would you like to get it?", things would be so much easier.

Anyway hope this helps and I'll try to put more useful detail in soon.

---

### Post by localzuk on 2006-04-05
> Ugly firefox 1.5 Was the automatix package compiled with some library I don't have? It looks like an old gtk app with no adherence to KDE's general look and feel. Might be better on Gnome.

It is just the way Firefox is in KDE, IME. What i usually do is visit the addons.mozilla.org site and download the qute skin which is much nicer. There are also KDE specific skins also.

> Adding universe multiverse Like many of the initial set-up steps, a quick Google will turn up a useful page like this one. But again, couldn't this just be a tick box somewhere?

As the universe and multiverse repositories are unsupported, I don't think adding tick boxes would work. The repositories should be mirrors anyway (so if you are in the usa it would be us.archive... and in the uk uk.archive... etc...). I think the current method is fine as the customisable nature of repositories could not easily be harnessed and made any simpler without restricting the changes you can make.

Other than that I think your suggestions make sense.

---

