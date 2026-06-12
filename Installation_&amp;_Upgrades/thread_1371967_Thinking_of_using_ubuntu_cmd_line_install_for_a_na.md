---
title: "Thinking of using ubuntu cmd line install for a nas - need help"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Captain_Glen on 2010-01-04
Hi,

I am sick of leaving my noise power hungry computer all night to do downloads.

I have dug out an old laptop with a PIII coppermine cpu and 228MB of ram.  I am thinking of using it as a nas.  I have bought a usb 2.0 to pcm card of ebay for $8 and a 1TB eternal hard drive.

At first I was thinking of using freenas but I read on the forums that it is very buggy and most people recommend using ubuntu instead.  Does anyone have any experience with freenas?

I tried Ubuntu but the CPU was maxed out at 100%.
I tried Xubuntu but the CPU was maxed out at 90%.
Surprisingly xubuntu was slower than vanilla ubuntu.

I have two more options to try: Damn small linux and ubuntu command line install.

If I do a command line install I want to be able to setup samba sharing and bittorrent and some sort of backup software (was thinking of using rsync).  In the future I may also want to setup ZoneMinder with some IP Cameras .  I want to be able to just download torrent files on my regular pc and drop them in a samba share on the nas and have it automatically start downloading them.

I am okay at using the terminal.  But I don't know how to setup transmission as a daemon and have it automatically start torrents from a folder in the command line.  I can do it in the gui though.  Also I don't know how to setup samba shares in the command line.  And I don't know how to setup rsync or ZoneMinder.

Can someone advise me on how to do this or point me to a tutorial?

Any help would be appreciated.

Thanks,
Glen.

---

### Post by Captain_Glen on 2010-01-04
I tried damn small linux but it just makes a high pitched squealing when I try to install it.  It gets part way though loading things and then just makes this horrible squeal.

So ubuntu cmd line install looks like my only option.

---

### Post by kerry_s on 2010-01-04
that sounds like a good idea. i got a old vaio laptop with 450mhz 256mb ram, i just put it away when i got my desktop built. :)

---

### Post by prshah on 2010-01-04
> **Captain_Glen said:**
> 
I have dug out an old laptop with a PIII coppermine cpu and 228MB of ram.  I am thinking of using it as a nas.  I have bought a usb 2.0 to pcm card of ebay for $8 and a 1TB [color=red]eternal[/color] hard drive.

ubuntu command line install.

If I do a command line install I want to be able to setup samba sharing and bittorrent and some sort of backup software (was thinking of using rsync).

This is a nice idea.

I recommend that you do an Ubuntu minimal install (command line, base system only) though your system should be able to handle gui as well.

You can then setup samba by apt-get ing the relevant packages, but I recommend you use NFS.

I recommend you use rtorrent (a command line, astonishingly capable) torrent client. With this setup, here's an example of what you can do: Drop your .torrent files to your samba share; rtorrent will automatically pick it up and start downloading it. When finished, it will automatically move it to your external (or any directory you specify), and seed it until a specified ratio as well. It can also control it's traffic based on timings you specify.

I do not recommend you place interim (downloading) torrents on your external.

You should also set it up as an (open)SSH server so that you can control / administer it remotely.

Unfortunately this whole setup cannot be condensed into a couple of commands, but it's a starting point.

Please post back if you have any questions, or as and when you run into problems with your setup.

... And hey, I'd like one of those "[color=red]eternal[/color] hard drive" as well. :D

---

