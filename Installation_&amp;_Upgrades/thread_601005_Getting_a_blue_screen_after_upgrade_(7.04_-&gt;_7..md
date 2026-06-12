---
title: "Getting a blue screen after upgrade (7.04 -&gt; 7.10)"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Guises on 2007-11-02
I upgraded thorugh the upgrade manager and it seemed to do its thing without any problems so I just let it run for a while. When I came back to the computer the upgrade manager had dissapeared and, while I could move the mouse around and click on things on such, nothing seemed to be working right so I rebooted. 

Since then, all I get when I boot into Ubuntu is a light blue / grey screen. The curser is there and it moves and I can get an error box when I type ctrl-shift-x (the shortcut that I had defined for popping up a terminal), but I can't do anything else.

I can get a command line when I boot in recovery mode, but I don't know what to do with it.

One more thing - when I rebooted after the upgrade I had a filesystem error. I did the fsck thing as normal and it fixed everything, as normal. However - there appeared to be a whole lot more problems this time than there is most of the time. Going through the fsck process took a while.

---

### Post by pay on 2007-11-02
In the command line try ```
sudo aptitude dist-upgrade
```

---

### Post by spenc083 on 2007-11-03
I have mouse movement but nothing else. No icons, nothing. I'm able to boot from the CD but not sure what to do after that.

Help! I'm using Windows......

---

### Post by Guises on 2007-11-03
> **pay said:**
> In the command line try ```
sudo aptitude dist-upgrade
```

Alright, I did this and it told me to run "dpkg --configure -a". So I did that and let it go overnight and it seems to have helped a whole lot. I can boot into the desktop now, and I'm posting this while running Ubuntu. However, dpkg did give an error message:

> dpkg: subprocess post-installation script returned error exit status 135

And the update manager isn't working. It gives errors of:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And when I run "dpkg --configure -a" in a terminal, as per it's suggestion, I get:

> Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not installed.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not installed.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135

So it's not flawless, but it's a big improvement. Thanks.

---

### Post by pay on 2007-11-04
What do your sources.list look like? Try installing util-linux then upgrading again and see if it still has that error.

---

### Post by Guises on 2007-11-04
Well, "sudo aptitude install util-linux" gives me the same error that apt-get and synaptic do. Downloading the deb file and trying to install via the GDebi installer gives me an error that explicitly says that my dependencies are screwed up.

Searching other threads for dpkg 135 errors suggests that it might be java that's doing something wrong, but I don't know how to reinstall that if the package managers aren't working.

Actually, Open Office isn't running properly either so it may well be a java problem. I tried to switch java implementations with:
> sudo update-java-alternatives -s java-6-sun
and 
sudo update-java-alternatives -s java-gcj
But either that didn't actually do anything, or it just didn't help. Is there a way for me to reinstall java without a package manager?

sources.list looks... normal, I think. I can post it if you like.

---

### Post by pay on 2007-11-06
You can install java by downloading it from sun's site and executing it with ```
chmod +x java.run #change the name of the filename
sudo ./java.run
```Sorry I can't really help you with the other problems because I'm not entirely sure whats going on.

---

### Post by Guises on 2007-11-10
I had been intending to get back to trying to do this when I had the time, (the Java install worked, but didn't fix anything right off. I may not have done everything there that I needed too.) but when I booted just now something has changed. Icons are different, Firefox is a different color, and, while the update manager gave me the same error as before, this time when I ran "dpkg --configure -a" it apparently worked. (Still gave errors, but not the same error.) I don't know what has caused this.

Anyway, not everything is fixed but with synaptic working again I think I can figure it out. Thanks.

---

