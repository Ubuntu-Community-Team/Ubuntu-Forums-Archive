---
title: "&quot;Killed&quot;"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Megatog615 on 2005-11-12
Whenever it starts loading the partitioner, it goes to a black screen and fills the screen with the word, "Killed". Sort of like this:
> Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
Killed
What is this about? It never did this in Ubuntu 5.04, and I did an MD5 check of the iso, no problems. I've burned the cd twice and had the exact same problem. If you need computer statistics, I'll give them to you.

---

### Post by Megatog615 on 2005-11-13
*bump*

---

### Post by tseliot on 2005-11-13
If the installer doesn't work for you, try this method:

Install Ubuntu Hoary 5.04 ([COLOR="Red"]DO NOT INSTALL ANYTHING ELSE[/COLOR])

Type

```
sudo gedit /etc/apt/sources.list
```

Replace the word "Hoary" with the word "[COLOR="Blue"]Breezy[/COLOR]" in the whole document

Save and exit

then type:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And when it finishes, can restart your computer

---

### Post by Megatog615 on 2005-11-13
Only problem is, I get a "Segmentation Fault" when I try and use the partitioner in 5.04. I've installed before, but only by letting it erase the entire disk, which I do not want to do.

---

### Post by tseliot on 2005-11-13
You should look at [https://bugzilla.ubuntu.com/]("https://bugzilla.ubuntu.com/")

And see if your problem is listed (with a solution).

If it's not listed then you should file the bug and the developers will try to solve your problem (which might be affecting other people as well)

---

### Post by Megatog615 on 2005-11-13
Ok thank you! Is there a way to install Ubuntu by skipping the formatting?

---

### Post by tseliot on 2005-11-13
[QUOTE=Megatog615]Ok thank you! Is there a way to install Ubuntu by skipping the formatting?[/QUOTE]
You can't install it without formatting the harddisk.

You might want to try OpenSuse (Until Ubuntu Dapper Drake is released in April) because it has a newer kernel (2.6.13) which might support the chipset of your motherboard.

---

### Post by Megatog615 on 2005-11-13
Actually the laptop I'm trying to install it on is rather old.

With a stroke of luck, I have gotten the 5.04 version of the partitioner to work, and install Ubuntu on a free partition. It is the "server" version. I'll need help with NDISWrapper.

---

