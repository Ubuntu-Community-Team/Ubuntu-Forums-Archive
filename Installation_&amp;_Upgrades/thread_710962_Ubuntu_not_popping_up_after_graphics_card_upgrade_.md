---
title: "Ubuntu not popping up after graphics card upgrade :("
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Tekee on 2008-02-29
I recently switched from an on-board GFX to an actual card, which seems to be conflicting with my xorg settings.

Is there any way to update it so that the xorg reads the new card?

I get a very "DOS"-looking error message when I try to boot Ubuntu. I can do commands and stuff, but I have no idea how to get to what I need.

---

### Post by forestpixie on 2008-02-29
you need to reconfigure x, run this from the command line

```
dpkg-reconfigure xserver-xorg
```

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by erginemr on 2008-02-29
Another command close to the above is
```
dpkg-reconfigure -phigh xserver-xorg
```
which automatically configures (or at least, tries to do that) your xorg.conf file.

---

### Post by Tekee on 2008-03-04
A belated post, but I need some help nevertheless...

I attempted the codes that were given to me above, but I was given the error 'must run from root.'

What now?

---

### Post by erginemr on 2008-03-05
You should run:
```
sudo <command>
```
to run a command with root permission. So, 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is what you need.

But please explain your problem in better words first, so that perhaps we can help with it.

---

### Post by Tekee on 2008-03-05
> **erginemr said:**
> You should run:
```
sudo <command>
```
to run a command with root permission. So, 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
is what you need.

But please explain your problem in better words first, so that perhaps we can help with it.

Better words?
I'm not sure how I'm being unclear, but in short, I try to boot Ubuntu and I get no GUI.

The command above worked, but now I'm running into a different problem.

I changed the GFX card to 'nv' for Nvidia and got to the step where it's having me choose my monitor's length/width refresh rates (or something of the sort). At this point the reconfiguration screen immediately switches to a command line at the bottom of the screen that tells me I'm overwriting a custom xorg configuration made in the past and leaves me with a line to type a command in.

---

### Post by steveneddy on 2008-03-05
You may need to blacklist any onboard graphics cards to get the xorg to see the new video card.

---

