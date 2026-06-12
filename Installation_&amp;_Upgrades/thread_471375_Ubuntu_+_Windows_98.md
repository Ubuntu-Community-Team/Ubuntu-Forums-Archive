---
title: "Ubuntu + Windows 98"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by lemonwonder on 2007-06-11
Hey Guys.

My Computer:
~~~~~~~~~

Windows 98
256mb Ram
File System: 32-Bit
Defragmenting as I type



I want to install ubuntu from the live cd onto it. I dont want to loose any files and I am a COMPLETE NOOB to linux, windows, installing anything rly!

First of all: Should I let the defrag finish... its gonna take 4eva!!


I need a guide so easy that my block of cheese could do it. I am installing it on our families 2nd computer, better for it to be un-detectable or atleast have windows load up every time, unless I press F5 or whetav key it is which brings up the menu on startup.

Help Plz???

---

### Post by foxmulder881 on 2007-06-11
Yes, let defrag complete. Reboot into the LiveCD and then click on the install icon. The Ubuntu installer will guide you through the rest and also install the GRUB bootloader. Upon reboot, you will be given the option to boot either Ubuntu Linux or Windows.

Hope this brief info helps.

---

### Post by lemonwonder on 2007-06-11
Umm.. ive herd stories of ppl goin into it and having all data (including the windows OS!!!!) be deleted..... And whats the GRUB? I have no idea what so eva.... I can barely write an email... ok exadurating but... ya know!

---

### Post by Wim Sturkenboom on 2007-06-12
[COLOR="Red"]**[SIZE="5"]Make backups.[/SIZE]**[/COLOR]

People loose data because they don't make backups. Under normal circumstances, there is always a risk that you loose your data (so you should already have backups), but when you start partitioning you increase that risk (user mistake, power failure, ...).

You can reasonably safe resize (one of the) the Windows parition(s); I'm not sure if that functionality is in the Ubuntu Live CD. Else you can use the [gparted live-cd](http://gparted.sourceforge.net/livecd.php).
And yes, first finish the defrag (even if it takes a day)

At the end of the Ubuntu installation, Grub (a bootloader) will be installed. At that time, it will detect windows and add it as an option to GRUB's boot menu. By default, it will boot Ubuntu after approx 10 seconds, so you have to edit the GRUB configuration after the first boot so it will automatically boot windows. I think that you can reduce the time to 0, but you might run into a problem that you can not access Ubuntu because you're not fast enough.
Do some research how to modify the GRUB configuration before you start.

---

### Post by lemonwonder on 2007-06-12
Cant you tell me what to do. You guys are all saying just 1 or 2 things, I need to know whats going to happen, what i should expect, not just a few things. What to modify, how to re-install windows if I loose all the data!!!!!!!!!!!!!!

---

### Post by Wim Sturkenboom on 2007-06-12
I can't as I don't do it on a regular basis. But maybe this [ Installing a Dual-Boot with Windows and Ubuntu](http://www.psychocats.net/ubuntu/installing) gives you an idea and some confidence.

BTW google is your friend, sure that you can find some other tutorials / guides if you want to. Above one was foung through googling for [ubuntu installation guide](http://www.google.co.za/search?hl=en&q=ubuntu+installation+guide&btnG=Google+Search&meta=)

Re-installing windows is just a matter of popping the Windows CD in, boot from it and install.

---

### Post by lemonwonder on 2007-06-12
Thnx for that... windows rly that easy... and i fink we dont have cd anymore. LOL. Google my best frend... i tried him

They use windows XP, is it same for 98????

---

### Post by Wim Sturkenboom on 2007-06-12
I haven't read it, but if I compare (from my memory)  the dual boots with Win98 and the dual boot with WinXP, there is no obvious difference (again, recall from my memory).

---

### Post by lemonwonder on 2007-06-12
Ok, im just running an in depth scan-disk. PLEASE someone who has done is confirm this, ill try to find the win98 cd.

So.... anyone have better instructions for install win98 if everything diez??

---

### Post by foxmulder881 on 2007-06-12
> **lemonwonder said:**
> So.... anyone have better instructions for install win98 if everything diez??

If it comes to having to reinstall Windows, just pop in the CD, boot up and follow the Windows Installer prompts. It's not that hard...

---

### Post by arnicainthemembrane on 2007-06-12
So can I ijust put the Windows NT disc into my Ubuntu machine and then have Ubuntu automatically partition it?

I'm doing this 'cause if you add plugins to Mozilla Firefox on Ubuntu you get seg faults. Also as much as Windows sucks, it's a Windows world out there...

---

### Post by foxmulder881 on 2007-06-12
> **arnicainthemembrane said:**
> So can I ijust put the Windows NT disc into my Ubuntu machine and then have Ubuntu automatically partition it?

I'm doing this 'cause if you add plugins to Mozilla Firefox on Ubuntu you get seg faults. Also as much as Windows sucks, it's a Windows world out there...

No idea about what you are talking about, about errors with Firefox + Add-Ons with Ubuntu Linux?!?

And it's most certainly not a Windows world out there. Sure, they have 90% (or whatever the figure is) of the OS market, but that doesn't make it a Windows world at all.

---

### Post by lemonwonder on 2007-06-12
I JUST INSTALLED IT!

Grub pops up, and the first thing I click (its the normal ubuntu) it does graphical load, says somin about 5 seconds and shuts down. Win98 workz tho


HA! IT WORKED SECOND TIME! 


[COLOR="DarkRed"]How do I put windows98 as the first selection on the dual-bbot loader thing, ubuntu stuff is first, I want that under "other os" coz windows is still main one (coz only i use ubuntu)???? [/COLOR]

---

### Post by foxmulder881 on 2007-06-12
That's quite a hard thing to explain to a newbie over the forums.

Google "How to edit grub config" and see what you get. It may give you a better idea than what we can explain.

No offence to you, but editing the grub config when you're a Linux newbie isn't easy.

---

### Post by RRS on 2007-06-12
> on our families 2nd computer, better for it to be un-detectable or atleast have windows load up every time, unless [URL="http://users.bigpond.net.au/hermanzone/p15.htm"]I press F5 or whetav key it is which brings up the menu on startup.
Sounds like [these instructions]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu") might be just what you're looking for.

[Here's]("http://users.bigpond.net.au/hermanzone/p15.htm") is the complete Grub page from the above link. It explains the other way's to modify your settings, such as making Win98 the default boot choice.

Just read the instructions carefully till you understand them and are sure what you want to achieve and you'lll be fine. With tutorials like these I usually use copy/paste to avoid misspelling and other typo's.

[Herman's site]("http://users.bigpond.net.au/hermanzone/index.htm") has a lot of other usefull info and I also second the recommendation of [Aysiu's]("http://www.psychocats.net/ubuntu/index.php") given in a previous post.

Linux isn't "hard", just different. Take it slow and don't hesitate to ask questions, We were all new once and I still know a lot less then I once thought.

Welcome Aboard

---

