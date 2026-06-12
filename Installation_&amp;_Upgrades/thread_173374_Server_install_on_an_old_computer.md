---
title: "Server install on an old computer"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by strider1551 on 2006-05-10
For various reasons an old computer fell into my hands, so I figured I would install Ubuntu Breezy in server mode and have it do a few automated tasks for me.

At the "Loading additional components" step, it continually fails when trying to load "nic-firmware-2.6.12-9-386-di".  After some time it gives me a message that it failed to load it.

Here's what I know about the computer:
```

IBM Aptiva 2161
Pentium 166MHz
32 MB RAM
4 GB hard drive

```
I know, I know, it's really old... try DSL... etc.

- I did try burning a second disk and checked the md5sum of the iso.
- I can't figure out how to get into the menu on the low memory install mode.  The screen just gows black if I hit ESC.
- I have tried a few boot options (not sure what they do, but I gave them a try):
     no387
     no387 pci=noacpi hd=cylinders,heads,sectors

- I have yet to try out Dapper

---

### Post by Teroedni on 2006-05-10
Brezzy dosent like low memory


Dapper does
I have installed Dapper gnome with 64mb of ram;)



So for your usage (server Install) Dapper will work fine:)

---

### Post by NiceGuy on 2006-05-10
Ok now thats weird! I'm doing exactly the same thing at the moment! The pc I'm trying it on is a Celeron 333 with 32MB of ram and 2 hard drives, a 3GB and a 10GB. I'm afraid I can't really help with your problem but I'm downloading the dapper .iso from [here]("http://releases.ubuntu.com/ubuntu-server/dapper/") as I type this so I'll let you know how it goes.

My only suggestion for you (and me if dapper doesn't work) is to try another distro.

It wasn't a server (I was basically trying a 'lets see what we can get running on here' experiment) but I managed to get Vecor Linux (based on Slackware) working quite well (if a little slowly) - and that was using X!

---

### Post by strider1551 on 2006-05-10
Great.  I started downloading Dapper after posting as a last ditch effort, but it sounds like that's the solution.  I'll post how things go.

---

### Post by az on 2006-05-10
You really need more ram.  Is it a desktop?  More ram would be quite cheap.

As it is, you can always install Debian Woody (heh heh!) and then dist-upgrade to dapper.  (Yes, you can.)

---

### Post by strider1551 on 2006-05-10
Tried Dapper.  The install gives me a warning that the system needs at least 36 MB RAM to run, or else it might act unexpectedly.  After it detects hardware for the cd-rom, it just hangs.

Oh well.  I'm not really interested in investing 2 cents in this thing, so I'm just going to try out some other distros ([EuroNode]("http://euronode.org/") looks interesting).

---

### Post by NiceGuy on 2006-05-10
Ditto with that! My installer just hangs when I try to detect network hardware. It says simply 'killed' and then won't do anything else.

Azz, I think I'm probably going to take your advice and try to get some more ram, some compatible stuff is coming up on ebay in a few days. 

Till then I'll try some other distro's. Any suggestions would be great as I don't really want to chuck the machine (it works after all!). My initial idea was (and is) to use it as a n ftp/website server but then I got thinking that using it as a VNP endpoint would be cool! Does anyone know of a distro thats geared up to do that kind of thing (or even both!).

---

### Post by Teroedni on 2006-05-10
[QUOTE=strider1551]Tried Dapper.  The install gives me a warning that the system needs at least 36 MB RAM to run, or else it might act unexpectedly.  After it detects hardware for the cd-rom, it just hangs.

Oh well.  I'm not really interested in investing 2 cents in this thing, so I'm just going to try out some other distros ([EuroNode]("http://euronode.org/") looks interesting).[/QUOTE]



Was that on a Server install.? It should work .After what i know the minimum for the install is 32 mb ram so it should really work:P
Did you try with lower screnn solution and the other parameters like acpi= off?

---

### Post by strider1551 on 2006-05-10
Yes, it was a server install, and I'll admit that I didn't play with it for too long.  The first thing that popped up during the install was a message that the install process might not act as expected because of the low amount of memory, stating that it needs at least 36 MB.  After a message like that, I wasn't suprised when the install froze (and I did let it sit and "think" for over 20 minutes).

I don't think that the 36 MB limitation is for Dapper.  I think that minimum is actually for the install program.

Also, [this page]("http://doc.ubuntu.com/ubuntu/serverguide/C/preparing-to-install.html#id2558277") recommends at least 64 MB for a Dapper server install.  Granted, it is only a draft document and they suggest that it is possible to do it with less, but I don't think it would be worth solving my problem for what I'm doing.

I grabbed Debian, which installed just fine (24 MB min for them).

---

### Post by NiceGuy on 2006-05-11
I too have just installed debian (sarge) on my old pc. And although it started in 'low memory mode' it just said "please create a swap file as soon as possible" and that was the first thing it did (ie. it started the partitioner). All the non-essential drivers (ie the networking drivers etc.) were loaded AFTER doing this and so the fact I had low memory didn't really matter. Perhaps if the ubuntu installation program did the same thing it might work better (and not crash)? But then maybe I'm missing something...

---

