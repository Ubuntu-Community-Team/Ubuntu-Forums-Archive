---
title: "Upgrading ALSA driver to 1.0.17"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by avisa on 2008-07-24
Hi,

I'm trying to upgrade my ALSA drivers but with no luck.
I'm kinda new to Ubuntu.. Anyway I downloaded the source and extract it into a folder in my home directory.

I'm running the ./configure and it looks good to me (no errors what's so ever) but when I'm trying to "make install" it (with sudo) I keep getting error messages..

```

avisa@avisa-laptop:~/Downloads/alsa-driver-1.0.17$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/avisa/Downloads/alsa-driver-1.0.17/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

```

any ideas? Do I need to unload the current driver or something? I currently have the 1.0.16 on the 2.6.24-19-generic kernel version.

Btw
the reason that I'm trying to upgrade is because from some reason every time that I plug headphones to my laptop I kinda hear the surrounding too.. It's like the mic is on and I can hear myself typing and stuff..
When I'm using the laptop speakers I don't have this problem.

Can someone please advice?

---

### Post by mikewhatever on 2008-07-24
You definitely don't need the new alsa for that problem. Double click on the speaker icon next to the clock, move to Recording tab and mute the mic in Mic Bypass column.

---

### Post by avisa on 2008-07-24
I double checked and I don't have "Mic Bypass" column.
My mic is controled by the "Capture" column but I tried to mute it there and I still hear the background noices...

---

### Post by Pumalite on 2008-07-24
Type:
alsamixer
in the Terminal and play with the controls

---

### Post by mikewhatever on 2008-07-24
Double click on the speaker again, select Edit --> Preferences from the menu and check the Mic Bypass box.

---

### Post by avisa on 2008-07-24
> **mikewhatever said:**
> Double click on the speaker again, select Edit --> Preferences from the menu and check the Mic Bypass box.

I don't have it in the list..

---

### Post by mikewhatever on 2008-07-25
I don't know if that's the case, but perhaps there is a differently named option to allow you to mute the mic. What do you have under Preferences?

---

### Post by mocha on 2008-07-28
> **avisa said:**
> Hi,
any ideas? Do I need to unload the current driver or something? I currently have the 1.0.16 on the 2.6.24-19-generic kernel version.

Can someone please advice?

I think you need to install the kernel headers.  In Synaptic it's linux-headers or something like that.

---

