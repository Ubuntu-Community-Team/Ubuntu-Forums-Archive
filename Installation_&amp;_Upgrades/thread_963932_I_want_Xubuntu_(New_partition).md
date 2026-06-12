---
title: "I want Xubuntu (New partition)"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by JakeWatkins on 2008-10-30
I want to be able to boot Xubuntu with Ubuntu (not at the same time)

And Kubuntu, for that matter.

Honestly, though, I'm scared to mess with Partitions.. I have one partition.. I think. But it was a Windows PC -- Bought from Wal-Mart and I wrote over everything and used Ubuntu, instead.

[img]http://img523.imageshack.us/img523/9731/98224414zv1.png[/img]

I don't really need much space (like 7-10GB of space each(including OS))

How can I do this, but insure that I won't delete any necessities?

(I'm going to back up my pictures, but things like World of Warcraft, that are about 10GB download, and a lot of work to install/get it to run on Wine)

Any help?

---

### Post by DGortze380 on 2008-10-30
They're all the same operating system, just with different desktop environments. For xubuntu open a terminal and type:

```

sudo aptitude install xubuntu-desktop

```

then selected it from the sessions menu at the log in screen

for kubuntu install kubuntu-desktop and select it at login.

---

### Post by JakeWatkins on 2008-10-30
So.. will it write over GNOME and make it XFCE? But all my files and everything will be OK?

---

### Post by DGortze380 on 2008-10-30
> **JakeWatkins said:**
> So.. will it write over GNOME and make it XFCE? But all my files and everything will be OK?

no, it will install XFCE along side GNOME. You choose which one you want at the login screen.

To 'overwrite' GNOME:
```

sudo aptitude install xubuntu-desktop && sudo aptitude remove ubuntu-desktop

```

Your files should be fine. Back up anyways, especially your home directory. iIf anything goes wrong you can uninstall all desktops, reinstall gnome and restore your home directory from the backup to reset all your current settings.

---

### Post by JakeWatkins on 2008-10-30
What are the other things I can install besides Kubuntu/Xubuntu like that, and what are their benifits?

Can I install another distro like this? I really like Ubuntu, and I probably won't ever leave it, but part of the whole "linux" thing, is that it's free, and there are so many things to try = D

(This pertains to my original question about partitions)

---

### Post by lisati on 2008-10-30
> **JakeWatkins said:**
> What are the other things I can install besides Kubuntu/Xubuntu like that, and what are their benifits?

Can I install another distro like this? I really like Ubuntu, and I probably won't ever leave it, but part of the whole "linux" thing, is that it's free, and there are so many things to try = D

(This pertains to my original question about partitions)

I've been using Ubuntu for 18 months now and I'm still learning.... I can relate to a nervousness about messing with partitions as well.

There are a variety of flavours of Ubuntu available. The main differences between them are the applications that come prepackaged and the user interface (sometimes referred to as the "desktop"). Some are good for smaller machines with not much RAM or disk space, and some are better for larger machines. Kubuntu is the one most like Windows in its appearance that I've used (and I've seen discussions in the forums on making it look more like Windows)

You might also want to check out what programs are available through the "add/remove programs" menu, there's a variety of different things you can add to your ubuntu installation. Which (if any) you choose to install is up to you.

---

### Post by JakeWatkins on 2008-10-30
Yeah, I've used it for about 2 months now.. and I'm somewhat familiar with Ubuntu. Not nearly what I'd hope for, though.

I'm installing the Xubuntu/Kubuntu right now -- What about open SuSE, my friend said it was a good distro, but I'm skeptical

---

### Post by JakeWatkins on 2008-11-05
Does anyone have a good guide to make a new partition in Ubuntu, do I have to boot up using my Live CD to make the new partition? How will I know for sure I won't write over all my settings/files/programs?

---

### Post by DGortze380 on 2008-11-06
> **JakeWatkins said:**
> Does anyone have a good guide to make a new partition in Ubuntu, do I have to boot up using my Live CD to make the new partition? How will I know for sure I won't write over all my settings/files/programs?

What are you partitioning? I thought you just wanted to run xubuntu. It's the same OS, the only difference is the desktop. Don't partition anything, just open a terminal, and type:

```

sudo aptitude install xubuntu-desktop

```

Then you choose either GNOME or XFCE at the log-in screen.

If you're talking about another OS, another version of Linux or Windows, etc.

Boot the live cd, open a terminal and type:

```

sudo gparted

```

Resize your ubuntu partition, format the new free space, then shut down and boot the install media for your new OS. You can't be guaranteed that no files will be lost or damaged, that's why it's important to back up all important data first.

---

