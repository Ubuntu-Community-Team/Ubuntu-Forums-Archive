---
title: "Removing Boot Options, how?"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by pjsmetana on 2009-12-03
1st, a little background, 

I recently installed UNR 9.10 on an HP Mini 110-1030nr 6cell. Fantastic Distro btw. 
I'm going to be giving this netbook to my wife, and to make things simple for her I set it up as a Dual Boot, thus giving her OS options. She is quite used to the desktop I put Mint 5 on a while back. 

Now for the fun part... when I start the computer and it gets to the boot option screen I have a lot more options than just Ubuntu and Windows. So, how do I make it so the other options, such as memory test, do not show up? If thats not possible, then can I at the very least move Windows up to the 2nd option, while keeping Ubuntu as 1st?

I'm still a bit new to Linux versions. Even though I have had them for years I don't get to use them much due to Military Deployments and such. 

Thanks everyone!

---

### Post by darkod on 2009-12-03
To disable memtest in terminal execute:
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

If you ever want to enable it use the same command just with +x instead of -x. Moving windows up is slightly complicated so I would leave it at that. But if you insist on moving it, it can be done of course. :)

---

### Post by wojox on 2009-12-03
[Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by samigina on 2009-12-03
Install the StartupManager (is in synaptic), is a GUI for all that things.

---

### Post by darkod on 2009-12-03
> **samigina said:**
> Install the StartupManager (is in synaptic), is a GUI for all that things.

But have in mind some people have reported problems if using it to change boot options. For occasional change it seems it's better without it.

---

### Post by pjsmetana on 2009-12-04
> **darkod said:**
> To disable memtest in terminal execute:
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

If you ever want to enable it use the same command just with +x instead of -x. Moving windows up is slightly complicated so I would leave it at that. But if you insist on moving it, it can be done of course. :)

Ah hah! Fantastic! Thank you so much!

---

### Post by audiomick on 2009-12-04
This just turned up in the forum.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by darkod on 2009-12-04
Actually, if you are interested in "tweaking" around and you still want to move windows, it's not very complicated as it may have sounded in my post. My point was that if you are really new to dual booting and linux, it's probably not the first step you want to take.
Otherwise the logic of grub2 is this:
If you look in /etc/grub.d folder you will see the files starting with numbers. The entries in the menu are created in that order. Because 10_linux starts with 10, then memtest with 20, and os-prober (searching for other OSs, eg windows) with 30, that's how they are ordered.

So, if you would change the number of os-prober to for example 06, it will be before linux (ubuntu) entries. I haven't tried it, but that's how it works.

Make a copy of 30_os-prober. Then rename the copy to 06_os-prober. Run update-grub and you should end up with:
windows
ubuntu
windows

Try the first windows entry and if you are happy with it, disable the original os-prober with
sudo chmod -x /etc/grub.d/30_os-prober

And that's it. In case the 06_os-prober doesn't execute you might need to make it executable with:
sudo chmod +x /etc/grub.d/06_os-prober

---

### Post by presence1960 on 2009-12-04
> **samigina said:**
> Install the StartupManager (is in synaptic), is a GUI for all that things.

startup manager for GRUB 2 is somewhat limited in what it is able to do compared to using it with legacy GRUB

---

### Post by radnor on 2009-12-04
Personally what I did at home last night was...

chmod -x 10_linux, 20_memtest, 30_other os

Went to grub.cfg and copied out the several menuitems I wanted and put them in 40_X.

Then did an update_grub.  It removed all of the other "stuff".  I realize at sometime I may have to re-enable them and do a update-grub to get new updates and copy them to 40_X.  But this worked for me.

---

