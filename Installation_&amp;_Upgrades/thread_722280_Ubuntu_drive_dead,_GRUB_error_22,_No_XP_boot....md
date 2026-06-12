---
title: "Ubuntu drive dead, GRUB error 22, No XP boot..."
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by fyl2u on 2008-03-12
Hi all,

Quickly, my drive layout was along the lines of:

HDD 1: C:\ System (Win XP)
HDD 2: System (Ubuntu), E:\ User Data(!), F:\ Work Resources (sample library!), G:\ & H:\ _Everything _else I've downloaded to or stored on my PC in the last 7 years(!)
HDD 3: D:\ Program Files (Win XP), I:\ New Stuff 

...until yesterday, when HDD2 (IBM Deskstar) decided to die.

(AAAAAAAAAAAAAAAAAAAAAAARRRRRRRRRGGGGGGHHHHHH!!!!!!)

So, while mourning the loss of my entire freelance songwriting, production and mix-engineering portfolio, songs in progress, and VAST painstakingly-sorted sample library (all of which I last backed up over 6 months ago and was thinking the day before yesterday "I must do a backup tomorrow, it's been ages!"), I can't even boot my machine up, because GRUB is giving me Error 22 - presumably due to the sudden disappearance of HDD2 and therefore the Ubuntu system partitions.

I've got no floppies, can't find my windows XP CD, and am failing to use a USB flashdrive as a boot disk at the moment.

What I DO have is my Ubuntu FF installation CD, so I *can *boot into a live Ubuntu environment.

Now, I haven't used my Ubuntu installation for a long time now (since the IT management at the company I _used _to work for decided that since *they* knew nothing about Ubuntu, they couldn't trust it, so they went for a windows server for their FTP site instead), so for the time being I don't need to reinstall Ubuntu, and I'd like to get into my XP installation so I can assess the damage and find out exactly what I'm going to lose if I don't spend £700 GBP on having the HDD data recovered.

So my question is this...

Is there a way of "uninstalling" or removing GRUB from my system, giving boot control back to the default Windows XP boot sequence, or a way of altering the GRUB config so that it no longer looks for Ubuntu?

...or does a part of GRUB live on the Ubuntu drive, therefore meaning it will never work unless replaced?  (Spot the noob :)  )

Thanks in advance, I'm tearing my hair out, here.

Phil.

---

### Post by fyl2u on 2008-03-12
Ah, panic over!

I used The Ultimate Boot CD, which contains (amongst loads of other things) a couple of MBR tools, and now it's all working fine.

Thanks anyway guys.

---

### Post by LeoSolaris on 2008-03-12
I was thinking Ultimate Boot till I scrolled down. Glad ya got it under control. I need to remember to go download and burn a UB Disc too. Thanks for the reminder!

Leo

---

### Post by LeoKnight on 2008-04-24
how do you install that mbrtool on  ubuntu tho please?

---

### Post by lorin_93 on 2008-05-23
ok... i have the same problem .... i tried to delete ubuntu from my system and from disk management in xp i deleted ubuntu's swap partition and itself's partion
than it gave me error 22 i tried to boot with ubuntu's live cd for trying to make something..
but before the appearance of ubuntu's desktop.. the monitor turned black ... like it is when the computer is stoped.
i reseted it .. but the monitor is black .. it is not working. 
i tried with other graphic card but the same problem .. the monitor is black. 
Can somebody help me please? 
Thanks for any reply.

---

