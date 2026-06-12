---
title: "Keyboard and mouse not working"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jstalin on 2008-10-10
Ran the latest updates, rebooted. Keyboard and mouse do not work (mostly) when trying to log in. I can ctl-alt-delete and alt-f1 works (I can type just fine in shell mode). Can't type anything to log in to X (or gnome or whatever).

I've run recovery console and that didn't help.

Any thoughts on how to fix this?

---

### Post by dro0g on 2008-10-10
> **jstalin said:**
> Ran the latest updates, rebooted. Keyboard and mouse do not work (mostly) when trying to log in. I can ctl-alt-delete and alt-f1 works (I can type just fine in shell mode). Can't type anything to log in to X (or gnome or whatever).

I've run recovery console and that didn't help.

Any thoughts on how to fix this?

I think you've been hit with this:
[http://ubuntuforums.org/showthread.php?t=943370](http://ubuntuforums.org/showthread.php?t=943370)

---

### Post by jstalin on 2008-10-10
Splendid. Thanks for the info. Good to know I'm not alone and it's being worked on.

---

### Post by carolinason on 2008-10-10
same here and good to know. booted into single mode from grub and chose root. very windowzy the single mode is. had to get networking running in bash. 

tried to go here (this thread) using lynks and elinks, but gave up. i followed the link to 'upgrade wants to remove...' and it suggests apt as a noble art, not sure what that means. if apt where gone, so would i. 

lynx is a noble art... elinks is great, except moving around the page isn't obvious or maybe even possibe, idunno. also don't go around changing the frame buffer in grub to get a terminal that's usable, you'll york it. i had an older kernel to boot into, so i could fix my vga setting. also install vim, tiny vi is too tiny.

i'm using windows to post, NOT FUN!

---

### Post by inportb on 2008-10-10
Yeah, I fixed my touchpad, mouse, etc by installing the **xserver-xorg-input-all** package (got lazy and didn't go for the individual input drivers).

I didn't look online for this stuff... I vaguely remembered an update removing my synaptics driver last night, but I thought that it was expected behavior. =p

---

### Post by go7Ul1ai on 2008-10-10
I thought I was done for, I couldn't log in, so I couldn't back up (I only just realised I could have used my Live USB), So I resorted to formatting and putting Hardy back on. That's my 16Gbs of Music gone (good job my Documents and Pictures were backed up on a Memory Stick (old backup though :()).

Serves me right though,

Lee

---

### Post by carolinason on 2008-10-10
And yes this is in the context of keyboard and mouse not working.

Well Ibex is a testing release. To avoid losing stuff I just partition my drive to make a /, swap and /mnt/xtra (well that's what i call it) and I store my music in /mnt/xtra. Then when I york my system or beta software yorks out, i can reload (insert your fav distro) and just add that partition without formatting during the install.

I wonder when the fix is coming for this? I'm tired of windows. This would be a good time to play with something like dsl or puppy. How small can you go. I'm thinking you can install debian and install the packages puppy does.

You know the thing about Ibex is that it finally started getting good, keep in mind I know it's beta. But at this point it is promoted on the Ubuntu Web Site for download. Probably leave a bad taste in the mouth of potentials with this nasty one. Flash had finally started working full screen and I had everything perfect. Then as Emeril say's BAM! GNU/Linux at first was a compromise, then it hit a sweet spot around 2002. Then it started to compromise again. You can have this, but not that, kind of thing. Now everything peaked again and bloomaloom. Well it's only temporary right.

You touchpad people need to send out christmas cards this year!

---

### Post by virtualsolutions002 on 2008-10-10
If your keyboard and mouse are not working I think that they are unplugged or may be not working properly. You better change both of them.


Albert 

[Crystal Meth](http://www.crystalrecovery.com)

---

