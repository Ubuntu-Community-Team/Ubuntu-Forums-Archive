---
title: "Partitions for Household Server, /var?"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by moon2js on 2007-04-16
Hi, folks.

I'm fixin' to set up an old P3 as a home server for web development stuff (now) with "media services" (in the future). I want to set up the for-work essentials right away with the on-board ~12-gig hard drive and to expand later when I get the hardware/time.

Essentially, I need a web production/practice environment:
[LIST]
[*]Feisty server install (plus Xubuntu or Fluxbox)
[*]2 http servers (lighttpd and probably Apache, keeping them separate)
[*]mysql, php, rails, etc
[*]www/ftp mapped to /home
[/LIST]

So my idea for the ~12-gig hard drive are these partitions:
[LIST]
[*]/boot
[*]/swap (512-mb or so, current RAM 2x)
[*]/ (~6-gig)
[*]/home (~6-gig)
[*]other parts /var? /tmp?
[/LIST]

Eventually, I want to...
[LIST]
[*]migrate /home to another (much larger) physical disk or RAID;
[*]in the former /home partition, put another *nix for experimentation by duel boot -- this way I can get knee deep in Gentoo or try another OS every once in a while without risking the working 'buntu (sharing /home but probably with different usernames);
[*]and once the new bigger /home is available, set up network-accessible music/video in the vein of mythtv, democracyplayer, iTunes-compatible/DAAP service, etc.
[/LIST]

I'm no *nix partition expert, so my concerns are:
[LIST=1]
[*]Is there anything I'm describing or scheming horribly wrong or just plain silly? Anything I'm missing or better ways to achieve what I want?
[*]I don't usually bother segregating the filesystem (except /home) on my Ubuntu desktops, but for a household server as described how necessary/beneficial is it to give /var (or  /tmp or others) a dedicated partition and can it be 'shared' too?
[/LIST]

Please critique my partition schemes.

Feel free to suggest/link to related threads or advise me better search terms because I can't seem to find the kind of partition talk I'm looking for. Any other partition performance tips I should be aware of?

---

### Post by louieb on 2007-04-16
I'm no expert. But I do have a P3 40 gig drive, with Dapper server on it. Since the web content go in /var I made it a separate partition. and /home is also separate. 
With only 12 gig to play with I'd probably just have one partition for Ubuntu and one partition for the other distro.
Saw  a post by a guy that sets up servers for a living and he wrote for home machines he keep it simple and puts everything in one partition. For  commercial machines he puts everything on separate partitions. But thats a real head scratcher trying to figure out how much space to give to each.  I guess in that case Logical Volume Management (LVM) is the way to go.  :D

---

### Post by moon2js on 2007-04-18
Yeah, two systems on a ~13-gig hard drive would be tight, but I'd really want  the option to have one experimental system and one stable  (while also keeping future drives/RAID exclusively for /home). And I need a temporary /home. My desktop system has Gnome, Kubuntu, Xubuntu, Apache2, and various applications and it takes up 4.4-gig. So I kinda think that a home server without Gnome/KDE could fit on less that 6-gig. But maybe I'm wildly mistaken?

I'm leaning toward not bothering with a separate /var partition (because space is so tight), but maybe I might do a small partition for /var/logs or something.

---

### Post by louieb on 2007-04-18
Just checked the space used by my home server's / partition (/var and /home are seperate) it uses less than 600 mb   for LAMP, openssh-server, proftpd, htop, and midnight commaner (mc),  

BTW: I suggest you install **htop** its a nice command  line version of the top command.

And midnight commander (in the repositories as **mc** )   its a file manager for the cli.

---

