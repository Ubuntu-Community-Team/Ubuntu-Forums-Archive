---
title: "Frozen out - can't log in after upgrade"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Scotsgait on 2008-10-30
I upgraded tonight and everything ***seemed***to being going well until the reboot at the end when my machine froze at the login screen.

I've rebooted again and again and again......with the same thing happening. Has anyone got any suggestions what to do from a command prompt (which I can access through GRUB !!!)

Many thanks

---

### Post by martrn on 2008-10-30
```
sudo apt-get install bastet
bastet
sudo apt-get install ninvaders
ninvaders
sudo apt-get install moon-buggy
moon-buggy

ping google.com
// if you get 64 bytes from google.com etc......
sudo apt-get install lynx
lynx
// PRESS   <G>   and type   :  www.google.com

```
and search for using basic linux commands.....

etc....
etc....

---

### Post by jerrylamos on 2008-10-30
Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

### Post by Scotsgait on 2008-10-31
> **jerrylamos said:**
> 
If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

Thanks, Jerry.

Unfortunately, it didn't sort the problem - but I'll not reinstall compiz just in case it makes things worse.

---

### Post by martrn on 2008-10-31
You could try installing kde, or even xfe.  I have heard just a few people who can install these two but not gnome.
```

sudo apt-get install kdm
sudo apt-get install kubuntu-desktop

sudo apt-get install xfe

```
If you need to undo :-

```
sudo apt-get remove --purge kdm
sudo apt-get remove --purge kubuntu-desktop
sudo apt-get remove --purge xfe

```

If you can boot x via a log in prompt, I don't understand if you login prompt was graphical or text, you could try reconfiguring X11.

```
sudo dpkg-reconfigure xserver-xorg
```

Or else you could try changing your kernel
Visit [http://packages.ubuntu.com/intrepid/base/]("http://packages.ubuntu.com/intrepid/base/") and :

```
sudo apt-get install linux-image-2.6.27-7-generic
```

or install a diffrent kernel image from the one you are using.

---

### Post by Scotsgait on 2008-10-31
> **martrn said:**
> You could try installing kde, or even xfe.  I have heard just a few people who can install these two but not gnome.
```

sudo apt-get install kdm
sudo apt-get install kubuntu-desktop

sudo apt-get install xfe

```
If you need to undo :-

```
sudo apt-get remove --purge kdm
sudo apt-get remove --purge kubuntu-desktop
sudo apt-get remove --purge xfe

```

If you can boot x via a log in prompt, I don't understand if you login prompt was graphical or text, you could try reconfiguring X11.

```
sudo dpkg-reconfigure xserver-xorg
```

Or else you could try changing your kernel
Visit [http://packages.ubuntu.com/intrepid/base/]("http://packages.ubuntu.com/intrepid/base/") and :

```
sudo apt-get install linux-image-2.6.27-7-generic
```

or install a diffrent kernel image from the one you are using.


Well, I seem to be getting somewhere as the cursor is now the arrow but it's still frozen.....

Any more ideas ?

---

### Post by mikerobinson on 2008-10-31
> **Scotsgait said:**
> Well, I seem to be getting somewhere as the cursor is now the arrow but it's still frozen.....

Any more ideas ?

Have you tried using kdm instead of gdm? At a terminal run **sudo dpkg-reconfigure kdm** and select kdm instead and see if that works.

---

### Post by Scotsgait on 2008-10-31
> **mikerobinson said:**
> Have you tried using kdm instead of gdm? At a terminal run **sudo dpkg-reconfigure kdm** and select kdm instead and see if that works.

No progress, I'm afraid.

(I've lost the arrow again, BTW, but that was before I tried your suggest from the root command prompt.

---

### Post by martrn on 2008-10-31
Look at your log files that should be available from
/var/log/kdm.log   or
/var/log/gdm.log

depending on which desktop manager you are using.

It should give you a clue (and just a clue) as to what is happening.

try :
```
sudo nano /var/log/kdm.log    // -or-
sudo nano /var/log/gdm.log
```

for clues.

---

### Post by Scotsgait on 2008-10-31
> **martrn said:**
> Look at your log files that should be available from
/var/log/kdm.log   or
/var/log/gdm.log

depending on which desktop manager you are using.

It should give you a clue (and just a clue) as to what is happening.

try :
```
sudo nano /var/log/kdm.log    // -or-
sudo nano /var/log/gdm.log
```

for clues.

Under kdm, I get two  messages

mieqEnequeue: out of order valuator event; dropping

and

EQ overflowing. The server is probably stuck in an infinite loop.


There's no entry in a gdm log as far as I can see. I do get further - I can log in and it starts loading up the desktop but then cycles back to the login screen. Compiz has been uninstalled so that potential solution described elsewhere is ruled out.

---

### Post by martrn on 2008-10-31
Wicked you have just found bug number Bug #259808
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/259808]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/259808")

---

### Post by Scotsgait on 2008-11-01
> **martrn said:**
> Wicked you have just found bug number Bug #259808
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/259808]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/259808")

Am I right in thinking that there's not a workaround for this yet ? Is there anything I can do to get my desktop machine working again ? (Thank goodness for my Linpus-driven Aspire One !)

---

### Post by Scotsgait on 2008-11-05
YEE HAAA
[URL="http://ubuntuforums.org/showpost.php?p=6113944&postcount=16"]
This worked ![/URL]!

---

