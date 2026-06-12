---
title: "Dell XPS 400 e1000 problems"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by EBFoxbat on 2006-05-05
I'm having two problems installing Ubuntu.

1) I can't configure X with my GeForce 6800 PCIe. I just get pink lines all over the screen during install.

I was going to download and install new drivers but my eth0 isn't configured because it needs e1000.

2)I can't figure out how to install my network driver.

I ran apt-get install binutils and apt-get install build-essentials. then I dpg the 3 deb packages.

How do I unzip me e1000 driver and cd to it? I downloaded them through Windows (on this ubuntu computer on a different partition). I then burned them to a CD. But I get permision errors when I try to copy them from /dev/cdrom to someplace else.

I'm very frustrated and can't find simple enough help online. I'm computer savy but very very new to Linux. Thanks.

-Joe

---

### Post by RavenOfOdin on 2006-05-06
If I were you, I wouldn't have bought a Dell.  Their tech support is horrible nowadays.
Anyway, from the tone of your post and what I can gather, it seems that you've already got installing down pat. You just need to configure it right.

To this end:

1) Have you tried downloading the nvidia-glx and restricted-modules-nvidia utilities?

2) Are you in the "cdrom" usergroup? (This should be accessible from /etc/group with text editor if you aren't able to start either DE)

---

### Post by EBFoxbat on 2006-05-06
I bought a Dell because I was broke and they approved me for financing it. I would have built it.

1) I'm pretty sure I can fix the nVidia problem once I have the network driver working.

> 2) Are you in the "cdrom" usergroup? (This should be accessible from /etc/group with text editor if you aren't able to start either DE)

I don't know what that means. :confused: 

I have the e1000 driver zipped on a CD. How do I unzip and install it? I think that's all I need to do.

---

### Post by RavenOfOdin on 2006-05-06
[QUOTE=EBFoxbat]
I don't know what that means. :confused: 

I have the e1000 driver zipped on a CD. How do I unzip and install it? I think that's all I need to do.[/QUOTE]

Whatever user group you're in denotes what action you have permission to do.

For example, a user added to the "floppy" group is able to manage floppy disks.

The /etc/group file, accessible from terminal via "pico /etc/group" will give you an interface to add yourself to whatever group you need if your desktop environment isn't working.

Just look for the line that says "cdrom" and after the ":" put your user name. Then save and quit.

Your mention of permission problems leads me to believe you might need to do this.

Try this before anything else, though:

tar -xvf /path/to/archive (for a TAR file)

dpkg -c /path/to/archive
dpkg -i /path/to/archive (for a DEB file)

That will put your driver files into a separate folder which you can then use accordingly with the ./configure command and so forth. The latter will do a full install.

---

### Post by EBFoxbat on 2006-05-07
Grrr!!!!

I have e1000.tar.gz  (that's not the real file name but it is a .tar.gz file) on a CD in /dev/cdrom.

I run: ```
tar -xvf /dev/cdrom/e1000.tar.gz 
```

and I get an error that it can't extract it. Oh, ok, I thought. Maybe I need to uncompress it first. so I run:

```
gunzip /dev/cdrom/e1000.tar.gz 
```

Well it yells at me that /cdrom is read-only. Grrrr! So now what? I guess I should extract e1000.tar.gz to a different location then tar -xvf it from there. How do I do that. every time I tried to specify a new location it just said "/new/location is a directory.

This is so frustrating... not knowing that to do.

---

### Post by blackgecko on 2006-05-07
first change to your home dir 

#>  cd

then do 

#> tar xvzf /media/cdrom/e1000.tar.gz

use your own path

it complains of being a read only filesystem if youre extrating on it.

---

### Post by RavenOfOdin on 2006-05-07
>.<

I wonder why I didn't take that into account. . .Rofl.

---

