---
title: "From Win2k to Ubuntu"
date: 2006-05-12
forum: Installation &amp; Upgrades
---

### Post by wirespot on 2006-05-12
You folks will probably be glad to hear I've gotten fed up with my dad's computer and Windows 2000 and decided on Ubuntu. I am new to Ubuntu but I am a happy Debian user for a few years now, so I hope it won't be too much trouble.

I won't insist (much) on why I'm getting rid of Win2k. He used to use a non-priviledged user account, with regular antivirus and Windows updates, regular antispyware sweeps, with firewall, behind a home router, with Opera as browser and The Bat for email. So security was not an issue (it had better not after all this trouble). But, for nefarious reasons, the whole thing start bogging down and going progressively worse after 4-6 months and needs a reinstall. So enough about that.

The migration will be an interesting one, so I hope to document it along the way so that others may benefit too. He's currently using:
* Microsoft Office (Word, Excel, Powerpoint)
* The Bat (3 accounts, no junk filter, lots of folders; considering Thunderbird because I use it at work and know my way around it)
* Opera (needs to migrate all the settings/bookmarks)
* a Canon photo camera on USB (works with gtkam)
* a Nokia 6230 phone on infrared (I hope it will work with OBEX)
* he needs other common stuff: multimedia player, Cd/DVD burner, HP printing drivers

Most of this stuff I expect to work out. For Office, which he absolutely must have, I think a recent Wine should work.

FWIW, the computer is rather old (but decent): 800 MHz Duron, 384 MB of RAM, 20 GB HDD, GF2 Nvidia video card, onboard AC97 sound card, NEC DVD/RW, Allied Telesyn network card.

The most "exotic" bit is a Promise Ultra66 IDE controller, which is somewhat of a must since one of the motherboard IDE slots died and I don't want to keep the DVD writer and HDD on the same slot, nor do I want to replace an otherwise good motherboard.

That's it for now, if anybody has any suggestions please speak up. I'm currently backing up his documents and stuff and I'll be back with details.

---

### Post by wirespot on 2006-05-12
First big problem (solved): migrating mail from The Bat to Linux. TB can export to Unix mbox format one folder at a time, but that will NOT work with 3 accounts with 20k email and a myriad of subfolders.

Solution: [tb2kmail](http://msquadrat.de/projects/tb2kmail/), which is a Perl script that will run under ActiveState's Perl kit, on Windows, and export a TB account (recursively, with all the attachments) into a KMail format. Or you can use a patched version that produces Thunderbird format, which is very similar to plain mbox.

Gotcha: run it as administrator. It needs to create a file in TB's Program dir, and you can't do that as plain user, and you get no feedback to indicate why it doesn't do anything.

---

### Post by wirespot on 2006-05-13
I went with Thunderbird as the new email client. The folders produced by tb2kmail (the Thunderbird variant) can simply be dropped over a Thunderbird account and they'll be seen perfectly.

The browser is Opera, since that's what he used before and I was able to import the bookmarks over too.

I'll add more applications tomorrow. So far, the best thing I've seen is the priviledge separation in Ubuntu, I've heard of it but haven't experienced it first hand. And the worst is the way the gnome-panel and its applets randomly crash sometimes. I'll look around for a fix, it's rather annoying.

---

### Post by Sef on 2006-05-14
> FWIW, the computer is rather old (but decent): 800 MHz Duron, 384 MB of RAM, 20 GB HDD, GF2 Nvidia video card, onboard AC97 sound card, NEC DVD/RW, Allied Telesyn network card.


Gnome should be ok, maybe a bit slow, but no problems.  The sound card may need some tweaking, but the later versions of Dapper seem to have lessened the problems with it.

> he needs other common stuff: multimedia player, Cd/DVD burner, HP printing drivers


CD/DVD burner: GNOME comes with gnomebaker, but I prefer to use K3b.

HP drivers: Should just go into system > administration > printing and be able to get it running.  What is the model?

---

### Post by wirespot on 2006-05-14
[QUOTE=Sef]Gnome should be ok, maybe a bit slow, but no problems.  The sound card may need some tweaking, but the later versions of Dapper seem to have lessened the problems with it.[/quote]

I'm sure any integrated desktop environment will seem at least slightly piggish to me, since I usually run Blackbox. But it wouldn't do to subject the old man to that. :)

The sound card gave me no trouble whatsoever. The only thing I had to adjust was to move the preferences from EsounD to ALSA. Haven't tested multiplexing, now that I think of it, but it wasn't a priority.

[QUOTE=Sef]CD/DVD burner: GNOME comes with gnomebaker, but I prefer to use K3b.[/quote]

I settled on K3B too. GnomeBaker would've been great since it's much simpler, but it has that nasty problem of not being able to do multisession unless you unmount the cdrom device thus removing the automounting feature. K3B is very slow importing old disc sessions, but it works.

[QUOTE=Sef]HP drivers: Should just go into system > administration > printing and be able to get it running.  What is the model?[/QUOTE]

It's a Deskjet 3120. I don't expect much trouble from it either, but it's currently out of ink and couldn't test it. I did manage however to print over network to a LaserJet 4 shared by another Linux computer via Samba.

Here's a rundown of other apps I settled on:

* Opera runs as well as can be expected. The new 9 beta has some unpleasant quirks so I've gone back to 8.54 for now.

* Thunderbird recognized the exported mailboxes from The Bat flawlessly. The junk filter is a god send (dad was getting weary of "filtering" stuff by hand.)

* He uses Gaim as **instant messenger**, like he used to on Windows too (I forced him to).

* Nautilus seems to be to my dad's liking for a **file browser**. I've mapped a Samba share as well. He didn't seem to mind the loss of C: and D: and took well to the "Places" menu and the new way of handling CD and DVD discs.

* The **photo camera** (Canon A85) works well with gtkam. But I had to adjust for some trouble (it wouldn't extract pictures) using [this trick](http://xlife.zuavra.net/curse/0011/) regarding default rights on /proc/bus/usb.

* **OpenOffice** seems to be quite adequate for all his old Excel, PowerPoint and Word files. It recognized any file without problems. Unfortunately, both version 2 and 1.1.5 crash almost immediately when used. I think one of the 3 DIMM's is bad, since I've tried a compilation and it breakes randomly with "internal compiler error" and segfaults. memtest didn't catch anything but I don't trust it. The best test is to use one DIMM at a time and attempt a compilation.

* I've settled on gThumb for **image browsing**. EOG is too simple, F-Spot too complicated. He doesn't want the program to organize stuff for him, he just wants to browse and an occasional slideshow. GQview would've been fine too, but gThumb has a more user-friendly interface. Now, if only gThumb would have file altering abilities like IrfanView has... I'm starting to consider letting him browse pictures with Nautilus and setting display (from ImageMagick) as the associated image handler, this way when he clicks on a picture he gets the full view and a context menu where he can do a lot of alterations to it. Anybody know a good and simple photo alteration tool? Stuff like rotate, crop, brightness and contrast, perhaps some batch conversion... perhaps I'll look into Digikam.

* The video player is still an unsolved matter. I'd like to offer him just one player that plays everything. Perhaps GMplayer is it, if I can get a binary version up to par. I myself compile my own, maybe I'll do that for him too. The thing with MPlayer is that you compile it once and if you do it well you can forget about it, short of another completely new format or codec coming out (like it happened with H.264 and MP4). For now VLC seems to work well and I've also tried Totem-Xine but it stopped short of recognizing WMV files. Seem unfortunate that packages such as libxine-extracodecs are only available for Dapper.

* The only real challenge is getting access to his Nokia 6230 phone over a MA-620 USB/infrared cable. I've talked about that in [another thread](http://ubuntuforums.org/showthread.php?t=117928).

---

### Post by wirespot on 2006-05-15
Just to put everybody's mind at ease, the crashes have stopped now. It seems the positions of the RAM sticks wasn't ideal. Faulty behaviour varied from random application crashes to segfaults, compilation errors and even kernel panics. I've managed to find a stick/slot combination that made everything better. So it had nothing to do with Ubuntu.

In retrospective, this may have accounted for some of the recent bad behaviour of Win2k as well. :roll: But it's not like that was the only reason for the switch, so that's that.

---

### Post by drpepper on 2006-05-15
Hi, have you looked into automatix? Its an automated installer for after u install ubuntu. It installs players, burners and alot more, makin the transition from windows to unbuntu easier for beginners. It installs a number of codecs, free and non-free if ur not in the USA. SO much stuff I cant remember. But it helped me when i first started. Just search automatix in the forums or synaptic. (you can select what u want to install, it doesnt install everything if you dont want it to)

Nick

---

### Post by wirespot on 2006-05-18
Thanks, I will look into it.

For the time being, I went with MPlayer, compiled from source. It was a rather simple (well, for me) issue of installing some packages from extra-repositories, patching the source for GTK2 support, and installing (unpacking, really) skins and codecs.

I've associated gmplayer with the most common video extensions. Since gmplayer also has a playlist, with the right skin, it may even replace XMMS for my dad.

One annoyance: the properties dialogue for video files insists on using Totem for info about the file, and gives an error message every time, now that Totem is off the system.

---

