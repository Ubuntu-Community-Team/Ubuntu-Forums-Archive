---
title: "Installing Netscape"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by CybaCowboy on 2006-06-05
I have Netscape 7.2 saved in my Home Folder, bearing the filename "*netscape-i686-pc-linux-gnu-sea.tar.gz*"...

How do I install it?

---

### Post by localzuk on 2006-06-05
Take a look at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

To put it in quick terms, open a teminal, and run 'tar zxf netscape-i686-pc-linux-gnu-sea.tar.gz'. This will decompress the file into a directory. Change into this directory (cd nameofdir) and take a look at any files called 'INSTALL' or 'README'.

---

### Post by CybaCowboy on 2006-06-05
I extracted the downloaded file ("*netscape-i686-pc-linux-gnu-sea.tar.gz*") by right-clicking the file and selecting "*Extract Here*", then ran the "*netscape-installer-bin*" file that was extracted as part of this process...

This launches a Windows-style installation wizard, however when I get to the installation type (*Recommended*/*Full*/*Custom*) step, which also asks *where* to install Netscape (the default of which is "*/usr/local/netscape*"), I am told:
*Error [-624]: Can't make destination directory. Please try another directory.*

With my limited Linux experience, I suspect that this may have something to do with it not being run through Terminal as Admin, but I'm not exactly clear on the specific command to do this...

Anyone?

---

### Post by localzuk on 2006-06-05
How are you trying to run the .bin file? Try running it with sudo instead as it may be that you don't have permissions to create the directories you need.

Also, if you don't mind me asking, why do you want Netscape? Why not use one of the free mozilla browsers such as seamonkey or firefox?

---

### Post by CybaCowboy on 2006-06-05
[QUOTE=localzuk]How are you trying to run the .bin file?[/QUOTE]

By double-clicking the icon, which is in "*/home/cowboy/netscape-installer/netscape-installer-bin*"...


[QUOTE=localzuk]Try running it with sudo instead as it may be that you don't have permissions to create the directories you need.[/QUOTE]

As I stated above, this is what *I* suspect the problem is *also*, however I do not know *how* to run it as Sudo!


[QUOTE=localzuk]Also, if you don't mind me asking, why do you want Netscape? Why not use one of the free mozilla browsers such as seamonkey or firefox?[/QUOTE]

I use Opera as my primary browser, however in some (very) rare cases, a page will not display or otherwise work correctly with Opera...

Which is when a "mainstream" browser must be used.


Why not Firefox?

I hate it.

The main reason is because it is so slow to load pages (especially in comparison to Opera ("the fastest browser on earth!"), however there are lots of other little things I don't like, such as the overly colorful interface and the way in which tabbed browsing operates, etc...


I've been using Netscape since it first came out *wwwaaayyy* back when and while it may be a memory-hog these days, it's still a great browser.

It is my backup browser in Windows and soon it will be my backup browser in Linux also...

---

### Post by localzuk on 2006-06-05
To run an application as sudo, simply open a terminal (press alt+f2 and enter gnome-terminal) and type sudo followed by the file you wish to run.

Netscape is based on the gecko engine which powers firefox. It should be comparibly fast/slow. You may wish to take a look at seamonkey which is the old mozilla suite (which netscape is based on).

---

### Post by CybaCowboy on 2006-06-05
> **localzuk]To run an application as sudo, simply open a terminal (press alt+f2 and enter gnome-terminal) and type sudo followed by the file you wish to run.[/QUOTE]

So I should type "*sudo netscape-installer-bin*"?


[QUOTE=localzuk]Netscape is based on the gecko engine which powers firefox. It should be comparibly fast/slow.[/QUOTE]

Speed is only *one* reason why I don't like Firefox said:**
> You may wish to take a look at seamonkey which is the old mozilla suite (which netscape is based on).

Maybe after I've got Netscape running...


[QUOTE=localzuk]mozilla suite (which netscape is based on).[/QUOTE]

Correct me if I'm wrong, but it is my understanding that Netscape (Navigator) was around before Mozilla, which would lead me to believe that Mozilla is *technically* based on Netscape.

If I remember correctly, Mozilla is the open source version of Netscape and I'm 99% sure that it wasn't around in the early days of Netscape Navigator...

---

### Post by CybaCowboy on 2006-06-06
[QUOTE=CybaCowboy]So I should type "*sudo netscape-installer-bin*"?[/QUOTE]

[i]cowboy@ubuntu:~$ sudo netscape-installer-bin
Password:
sudo: netscape-installer-bin: command not found[/i]

Nope, doesn't work (which I already suspected would be the case)...


Anyone care to provide me with the *correct* command?

---

### Post by localzuk on 2006-06-06
Mozilla was open sourced from netscape, and since then greatly improved and IIRC completely rewritten. The 2 split off from each other and then netscape decided to use the work mozilla had done as the underlying functions of their browser. So netscape is based on mozilla.

To run the file you need to type sudo ./netscape-installer-bin

If that doesn't work, try giving it executable permissions  (run sudo chmod +x netscape-installer-bin) followed by the above command.

All I have been trying to point out is that the functionality provided by netscape is provided by an open source alternative (in the spirit of Ubuntu). Firefox and seamonkey both are customisable by plugins (the prior lots more than the latter) so you are likely to get the functionality you want, plus the interface, from an open source package...

---

### Post by mannheim on 2006-06-06
EDIT: Deleted my comment -- same answer above, 3 hours ago!

---

### Post by CybaCowboy on 2006-06-07
I just installed "mozilla-browser" using the Synaptic Package Manager instead.

It's open source and for obvious reasons, closely resembles the particular version of Netscape that I wanted installed...


Thanks for your help peoples!

---

