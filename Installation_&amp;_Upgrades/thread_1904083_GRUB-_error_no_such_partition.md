---
title: "GRUB- error: no such partition"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by Ollecram on 2012-01-04
Hey guys, I'm having some bit of a problem trying to boot my computer :s I had my computer dual boot to Ubuntu and windows 7. I deleted all the Ubuntu files from my computer and uninstalled it. That was a while back. For a few weeks, everything worked fine and I could use my computer whenever I wanted and turn it off and on as I pleased. Today I get home from school and I try to turn on my. Imputed and it gives me the error GRUB- error: no such partition 
I've spent the better part of a few hours trying to figure out how to fix this. All the fixes I see require me to have a windows boot cd so I can repair my windows files. The problem is that my computer doesn't have a cd drive. I tried bottling from an Ubuntu USB but it didn't work. I set my bios to boot from USB and I plug in my USB and restart the computer. The Ubuntu page loads fine but I try to click on install Ubuntu or try Ubuntu without installing, but all that come up is the Ubuntu loading screen with the five horizontal dots. After two minutes or something at the loading screen, the screen goes black and lines and lines of code start coming up. The codes are several processes being killed and timing out. I really don't know how to fix this problem :( can somebody help me and guide me through the process of getting my windows 7 back to working order? I have access to a laptop running kubuntu at the moment. It's my mothers but I can still use it. Any help is greatly appreciated :)

---

### Post by fantab on 2012-01-04
> **Ollecram said:**
> ........... gives me the error GRUB- error: no such partition 
I've spent the better part of a few hours trying to figure out how to fix this. All the fixes I see require me to have a windows boot cd so I can repair my windows files. The problem is that my computer doesn't have a cd drive. 

If you don't have a CD Drive then **are you using a NetBook**? If you are, then if you have a windows recovery option you should use that to recover your Windows. 

If not reinstall Windows or install another boot loader. You will have a better resolution of your problem if you contact [**Windows7 forum**]("http://www.sevenforums.com/").

---

### Post by darkod on 2012-01-04
Did you have a proper dual boot or just wubi inside windows?

If you removed ubuntu correctly and were able to boot windows for a few weeks there is no way grub2 would return to your computer. Something doesn't sound right.

---

### Post by Ollecram on 2012-01-04
That's just it :s it's not wubi since I installed it from USB last time. Could maybe be because I was doing some cable management and I reordered my sata cables, but I don't see how this would make any difference as the boot drive is still set to my hard drive. 
@fantab: it's not a netbook, it's a desktop without a functioning cd drive :D

---

### Post by darkod on 2012-01-04
Ah, it could. Most modern boards these days have two types of settings for boot.
One is for device type, like HDD, CD-ROM, USB, etc.
But since many people have multiple HDDs these days, there is another setting which from the HDDs you want to be first to boot from. Or if there is no such setting I think bios tries them one by one, so changing sata ports makes a difference in the hdd boot order.

You probably have broken grub on one of the disks, and right now that disk is tried before the disk with the windows bootloader.

---

### Post by Ollecram on 2012-01-04
Doh! >_<  soon after I posted my last reply, that same solution came to my mind and I rearranged my sata cables once again and specified the preferred boot drive. How empty headed of me lol. I can't believe I spent hours yesterday night trying to figure this out until I passed out in bed in a puddle of my own tears and torn out hair xD thanks for all the help and all the quick replies. :) problem solved :D

---

