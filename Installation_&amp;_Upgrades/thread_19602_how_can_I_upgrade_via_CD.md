---
title: "how can I upgrade via CD?"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by friendly_guy on 2005-03-12
Hi

I have just got a hoary disc with 'Linux magazine' & would like to use it to upgrade my warty install.  When I boot it I only get install options - no offer to upgrade.

Can anyone tell me how to upgrade with my disc? (Upgrading over the net is no good as I am on dial up).  

I think this is an important issue, or else I will have to do a clean install every 6 months!

Thanks

Guy

---

### Post by az on 2005-03-12
sudo apt-cdrom add
sudo apt-get dist-upgrade

I would check the md5sum first.

---

### Post by friendly_guy on 2005-03-13
Thank you for such a prompt & helpful response.  I will give it a try.

Guy

---

### Post by Martin Atkins on 2005-03-14
Please report back if this works OK, issues you experience, etc.

I, and I'm sure many others, are in the same situation!

Thanks

Martin

---

### Post by jrronimo on 2005-03-14
Alright, I'm giving this a whirl.

I've got Warty on my laptop.

I ran the commands you said, azz, and I'm getting a lot of connection errors to security.ubuntu.com. I'm using a CD I burned off the .iso I snagged last night via BT.

Is there a way to force it to just go to the CD? I've got most of the universe added in synaptic, if the two are intertwined.

Sorry, I'm quite the linux noob, but I'm learning, thanks to Ubuntu. :)

Edit://

Alright folkses, here's the easiest way to do it that I've found (but I've also only been looking for about 30 seconds, hah!)

Slap your Hoary disc in your appropriate media reader of choice (read: CD-ROM :) )

open up a terminal.

run 'sudo apt-cdrom add'

Go into Synaptic ('Computer' -> 'System Configuration' -> 'Synaptic Package Manager').

Open the Repositories ('Settings' -> 'Repositories')

uncheck everything except for 'cdrom:[Ubuntu 5.04_Hoary Hedgehog_ - Previewblahblablhablh]'

click 'ok'

back in the terminal, run 'sudo apt-get dist-upgrade'.

And you're off! It's basically the same thing that azz said if you see, but on my machine for whatever reason, it kept trying to hit the 'net for updates first. Which it is not allowed to do. Bad computer.

At the end, re-add your chosen repositories. :)

---

### Post by kagou on 2005-03-14
Ugh ....
I'm under hoary, and when i put a hoary cd (daily cd) on my notebook, a window appear and offer me to upgrade my system with this cd. Easy no ?!

---

### Post by jrronimo on 2005-03-14
Wow, what .iso did /you/ use and where can I get it?! Mine had no such option.

In fact, it looks as if upgrading from Warty to Hoary on my laptop didn't go so well. It happened, yes, but now X won't start, haha. They switched X servers for this release, though, no?

---

