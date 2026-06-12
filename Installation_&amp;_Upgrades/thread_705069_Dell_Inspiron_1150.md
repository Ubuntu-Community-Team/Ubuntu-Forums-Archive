---
title: "Dell Inspiron 1150"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by linuxfault on 2008-02-23
Hey all,

I'm trying to install Ubuntu 7.10 on my old Dell Inspiron 1150 using the Live CD. It seems to boot normally until it plays the sound when the desktop loads and then it just stays there. Are the any known issues with the live cd? 

Thanks.

---

### Post by DarkWater on 2008-02-23
Use the alternate CD.  It works wonders for problems that you just can't figure out.

---

### Post by Threnners on 2008-03-18
Same problem here.  Used the alternate install, rebooted, got the Ubuntu launch screen, screen is black, hear the knocking login prompt, still nothing on screen.

---

### Post by marakie on 2008-05-24
Quick answer is to remove the word splash from the kernel boot parameters.
You can do this at start up by pressing the escape key at the beginning of the boot sequence (as the clock is counting down) and then following the on-screen instructions to remove the word from the end of the appropriate line.
To do this permanently edit /boot/grub/menu.lst and do the same.

I also like to remove the quiet option and add verbose to see what's happening at boot up.

---

### Post by ds77 on 2008-07-24
Anyone get Hardy to install on a 1150? I have one hanging around that I would like to install Ubuntu on. When trying to install I select install (or try Ubuntu without installing even), it comes up to the Heron background and the mouse cursor and it just sits there never loads.

I am going to flash the bios with the newest one and see what happens, but maybe someone has an answer?

Thanks!

---

### Post by ds77 on 2008-07-24
Well, flashing the BIOS didnt help.  Now looking into this thread..
[http://ubuntuforums.org/showthread.php?t=608481](http://ubuntuforums.org/showthread.php?t=608481)

---

### Post by PCessna on 2008-07-24
Yeah, I just replied on a Topic about my ThinkPad T20 with 128MB of ram, and how that would never of worked just looking at memory.

The Text Installer works great.

---

### Post by ds77 on 2008-07-24
> **PCessna said:**
> Yeah, I just replied on a Topic about my ThinkPad T20 with 128MB of ram, and how that would never of worked just looking at memory.

The Text Installer works great.

Looks like its going to be the text installer.  One question though, I have never done the text installation.  Can you point me in the right direction for instructions? 

thanks

---

### Post by snowpine on 2008-07-24
A ram upgrade will work wonders. I have a Dell Latitude Cpx that is even older than the 1150, and it ran Ubuntu (slowly) once I upgraded to 256mb of ram and used the Alternate CD.

Have you checked out Xubuntu yet? It is perfect for older machines.

ds77, here is a good guide to command line installation: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

