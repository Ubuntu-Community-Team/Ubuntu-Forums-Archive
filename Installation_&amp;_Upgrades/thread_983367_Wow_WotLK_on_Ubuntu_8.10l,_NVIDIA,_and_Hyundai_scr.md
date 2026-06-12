---
title: "Wow WotLK on Ubuntu 8.10l, NVIDIA, and Hyundai screen..."
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by anandria on 2008-11-15
Hi!
[U]
Background:[/U]
I tried to reformat my daughters 3yo pc, by reinstalling win xp, which turned out fatal...
Trying to run Wow failed, error message: Cant find display device.
We guessed that it was the monitor that the game didn't find, searched for a full day for the driver for Hyundai L90D+, but they don't even have a site anymore.... Too bad on a good monitor.... Seems from forums it's not compatible with vista either...

Found a driver, tried manual install, error: .inf file contains no hardware information.

**Ubuntu!**
So, I made a copy of Ubuntu 8.10, and made a clean install on the full disk.
And, this is where we are now. Installing WoW (start plus burning cruzade) worked nicely, using wine.
BUT:

(This is where I beg for help)

1. I need the **Direct Rendering Infrastructure **(DRI)
Without it, Just trying to scroll down the EULA is almost impossible!

It is not on:
glxinfo | grep rendering gives the answer "no"

Problem: It tells me I can find out why, but I don't know enough, beeing a noob. **Where do I alter the setting to verbose...?**

"getting DRI to work with recent hardware is usually just a configuration issue."

Yep, I kind of guessed, and googleing it, tells me it is pretty likely my NVIDIA nforce4 SLI (something) that messes things up (right?)

However, I need replies to be pretty specific. Please tell me in what script I need to make alterations, and, if necessary, how to open it! ;)

Anyone feel up to the challenge of rescueing my daughters WoW-life by assisting?

I have tried changing the WTF in WOW, adding SET gxApi "opengl" which ruined the graphics altogether. So I Reset it...

And, I did this addition to the registry:

HKEY_CURRENT_USER\Software\Wine\
OpenGL
DisabledExtensions 
GL_ARB_vertex_buffer_object

Apart from that, I need to wait for Burning C to patch before I get to open the game and see how terribly slow it will be without DRI!

Next step, if the Ubuntu will accept the fixes to enable DRI, will be to convince it to allow me to install the WotLK DVD, to which I currently do not have access according to Ubuntu.
Solution, again after googleing, seems to be manually mounting the disk. Again: I need a proper instruction on how to do that...

I'd be thrilled to hear from one of you!

---

### Post by mrblondeisback on 2008-11-17
I can't help you as much as I wish I could, but I'll at least give you the bump, lol.  I feel you, my WoW was iffy for a while but I've got WotLK up and running solidly.  The only thing I can think is to make sure you have the correct driver installed, the nvidia one, not the nv one.  Oh, and you're gonna want the gxApi OpenGL tag in they wtf, as wow won't run without it.  well, it will, but the difference for me is huge, 5fps before, 40fps after.  If you're having issues mounting the DVD, too, you can always use the installer on worldofwarcraft.com.  As long as your account is upgraded you can just download the client.

---

