---
title: "permissions issue"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by indorian on 2010-01-22
I'm fairly new to Linux.  I've played around with it before (pretty much every distro) out of curiousity but my command of it is rather limited.  That said, I have so far enjoyed my experience with Ubuntu with a few exceptions.  The most notable right now is the issue I seem to be having installing the gtk/aurora theme on 9.10 Karmic.  I've run the apt-get, and extracted, and compiled, and now that I'm at the finish line with the make/make install commands, I'm stopped in the process by a permissions issue which appending the sudo command doesn't seem to change.  

Now run make.
make[1]: Entering directory `/home/corey/gtk2-engines-aurora-1.5.1'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/gtk-2.0/2.10.0/engines" || /bin/mkdir -p "/usr/lib/gtk-2.0/2.10.0/engines"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c  'libaurora.la' '/usr/lib/gtk-2.0/2.10.0/engines/libaurora.la'
/usr/bin/install -c .libs/libaurora.so /usr/lib/gtk-2.0/2.10.0/engines/libaurora.so
/usr/bin/install: cannot create regular file `/usr/lib/gtk-2.0/2.10.0/engines/libaurora.so': Permission denied
make[1]: *** [install-engineLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/corey/gtk2-engines-aurora-1.5.1'
make: *** [install-am] Error 2


the above is where it seems to hang, and I'm hoping that theres simply a command I'm not aware of to get past it.  As I said sudo doesn't seem to make a difference.

---

### Post by sisco311 on 2010-01-22
Hi and welcome to the forums!

Why don't you install it from the ppa repository?
[https://launchpad.net/~merlwiz79/+archive/aurora](https://launchpad.net/~merlwiz79/+archive/aurora)

---

### Post by warfacegod on 2010-01-22
Do you have the gtk2-engine installed? If aurora is a theme archive, the easiest way to install would be to go to: System> Preferences> Appearance> Themes tab and drag and drop the package into the window.

---

### Post by indorian on 2010-01-22
Sorry I should have mentioned I've tried that as well, and when I run the apt-get updates command and then look in the Ubuntu software manager I see nothing for aurora

---

### Post by indorian on 2010-01-22
aha...so many ways of skinning the same cat...

the drag and drop method worked, sort of...now I get a message saying that it won't look as it's supposed to because I need ubuntulooks...but in looking that up it seems an integral part of the themes which came with this distro so I'm a little confused.

is this going to be a graphical issue?  I'm one of the poor sods using an ati 9000 mobility card here and it seems we're somewhat screwed as to how the card is going to get seen and used by the OS

---

### Post by warfacegod on 2010-01-22
No it's not a graphics problem. Use Synaptic to search for ubuntulooks and install it. I should have mentioned that in my last post.

---

### Post by indorian on 2010-01-22
ok the package manager is definitely something I wasn't used to finding in linux - thanks :)  my last question involves the visual effects settings...since I'm using the ati 9000 card on the fglrx drivers which seem to be the ones that work best, I have to keep the visual effects at none as the system is unable to find drivers which will support either of the two other settings...is this going to severely limit the theme environment?

---

### Post by warfacegod on 2010-01-22
> **indorian said:**
> ok the package manager is definitely something I wasn't used to finding in linux - thanks :)  my last question involves the visual effects settings...since I'm using the ati 9000 card on the fglrx drivers which seem to be the ones that work best, I have to keep the visual effects at none as the system is unable to find drivers which will support either of the two other settings...is this going to severely limit the theme environment?

Not especially. The enhanced effects (Compiz is what it's called) have more to do with desktop behavior than the theme's look. Although you won't get to have translucent windows and things the actual impact, in most ways, is minor to the overall look.

---

### Post by indorian on 2010-01-22
it's sort of odd really - heck this laptop used to run wow years ago when I used it for gaming...the card is a mobility 9000 with 128mb ddr on it, but 9.10 won't run any effects on it.

anyway, thanks for the other help - I think I'll be having all sorts of fun with the package manager.  this is really a test run for me as although I'll have to keep at least one windows pc running I'd ultimately like to migrate the rest of them to a nice linux distro.

---

### Post by warfacegod on 2010-01-22
Here are a few shots of my desktop environment and my media player without Compiz and with. They aren't in order.

---

### Post by warfacegod on 2010-01-22
These two are from a 9.10 UNR install that I no longer have. They'll give a fair idea of what Compiz can do.

---

### Post by warfacegod on 2010-01-22
Forgot to attach them. (I do that all the time.)

---

### Post by indorian on 2010-01-22
Those look great, especially the last one, but sadly they're things I don't think I'll get to play with on this machine.

---

### Post by warfacegod on 2010-01-22
> **indorian said:**
> Those look great, especially the last one, but sadly they're things I don't think I'll get to play with on this machine.

I think it might be possible to put an nVidia graphics card in your machine. I did a quick search on your laptop and I saw some for sale. You might want to check into it.

You probably should mark this thread as solved under thread tools.

---

### Post by indorian on 2010-01-22
mine is the model just before the swappable video cards became available - I think the model you saw was a 766 or something (been a while I forget all the model numbers)  -  this one is a desktop socket 478 board crammed into a laptop chassis (clevo is the real manufacturer - same as the sager and hypersonic 5620's).

---

