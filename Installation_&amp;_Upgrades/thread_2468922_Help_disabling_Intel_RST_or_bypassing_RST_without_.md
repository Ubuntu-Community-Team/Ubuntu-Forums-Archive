---
title: "Help disabling Intel RST or bypassing RST without BIOS Password"
date: 2021-11-14
forum: Installation &amp; Upgrades
---

### Post by tripl3tim on 2021-11-14
_Quick Facts:_
Computer: **Dell XPS 15 9570** Laptop, 1050ti i7
Software: [B]Ubuntu 20.04.3
[/B]Error: **Intel** [B]RST Enabled, Disable RST before finishing Ubuntu installation

[/B]I don't have the BIOS Password, I cannot get it from Dell (I bought the computer from eBay, so I don't have the Dell invoice)
I need a way either to reset the BIOS Password or to disable/bypass RST to install Ubuntu. Doesn't matter if everything is cleared from the laptop or if Windows will not install again. 

I just want to install OpenBSD and get rid of all the Windows bloatware.

Can't open the laptop case, there are special screws and I will need tons of parts.

_What I have tried so far:_
[LIST]
[*]BIOS Crackers: bios-pw, De-CMOS (v1,v2,v3), PCCMOS Cleaner, etc. can't figure out how to use CMOSpwd
[*]3-attempt method: The computer doesn't give the "system locked" error after 3 wrong attempts. It gives me unlimited BIOS attempts, so the bios-pw method doesn't work.
[*]Disabling RST: Disabled it in device manager, still nothing, same error on trying the installation (it's because it only uninstalls the drivers, I suppose)
[/LIST]

Please help fellow ubuntu users!

---

### Post by ajgreeny on 2021-11-14
No idea if this works or not but if you can get to the CMOS battery on the motherboard and remove it, that might clear everything from the BIOS, including any set password.  According to the info at [https://www.dell.com/support/kbdoc/en-uk/000124377/how-to-perform-a-bios-or-cmos-reset-and-clear-the-nvram-on-dell-systems](https://www.dell.com/support/kbdoc/en-uk/000124377/how-to-perform-a-bios-or-cmos-reset-and-clear-the-nvram-on-dell-systems) this may not work on all models though the info at [https://www.parts-people.com/blog/2019/08/09/dell-xps-15-9570-p56f002-cmos-battery-removal-and-installation/](https://www.parts-people.com/blog/2019/08/09/dell-xps-15-9570-p56f002-cmos-battery-removal-and-installation/) suggests that it is possible.

If that still does not work I have no idea where you can go from there.

---

### Post by MAFoElffen on 2021-11-14
I am certified to do FRU repairs (warranty service repairs) on Dell, HP an Lenovo's..

What you and ajgreeny are right.

There are two ways to reset the BIOS password on the Dell XPS 15 1750.

The first is to take a picture of the error it throws when it comes up and you don't know it. You call Dell Support and give them the unique code. With that "unique code", they could give you an unlock code to reset it. 

BUT, anyone who calls for that has to be able to provide information that they are the legal owners of that laptop. This is a security thing, where they try to prevent unauthorized access (theft and such). If you "bought it"... Computers get resold all the time. This isn't a hard stop to calling Dell Support for this. You have documentation that you bought it from eBay... Just saying...

The only other way to do this is to take out the CMOS battery. This is an over-simplified statement for "this laptop". The screws are sort of special, but not really. All the screws except for the two under the badge door are T5 Torx screws. The two under the badge door are #1 Phillips... You will need other tools to get further to the CMOS battery.

Why? Because that is just the start... Most laptops, "after" you get the cover off, you can see the CMOS battery somewhere... This model is not one of those. 

The problem is that in that specific model, after you get the cover off, you won't see the CMOS battery at all. The CMOS battery on that is under the system board, as you have the laptop turned over and bottom lid off, under the left-upper corner of the system board. So you pretty much have to almost completely disassemble the laptop to get to it... And after you disconnect the battery, leave it disconnected for at least 5 minutes (and even then, after that, maybe short the two pins for another 10 seconds to a minute), before re-connecting the CMOS battery.

There is no shorting pins or reset switch on that system board... If you doubt you can do it on your own, even after watching many videos on YouTube... Yes, it is not for the faint hearted on that model.

If you watch a few videos and think you can do it on your own... You can get a cheap tool set for about $20 on Amazon that has all the tools you need. Not durable, but would do an average person fine for what they have. Mine was an investment, as I use mine every day, almost all day long. You don't need something like that just to do this.

At he least, you would need:
Torx size T5
Phillips #00, #0, #1
Spunge Stick
Alcohol Pad
Thermal Paste
(Take ESD static precautions, and disconnect the internal Battery first thing, after getting the cover off... And last, just before putting the cover back on.)

For someone new: A screw map... where you can mark and layout your screws and parts, so you can get them back into the same holes. There are about 5 different sizes/type in this laptop. It does matter where they go back in. Take lots of pictures on your phone, that you can use for reference, when taking apart. Because, besides the screws, there are very small cables and wires that go to specific connections.

---

### Post by ajgreeny on 2021-11-15
Sounds like another case of design over function!

They do make life difficult don't they.

---

### Post by tripl3tim on 2021-11-15
Thank you!

(to both of you)

---

### Post by Tadaen_Sylvermane on 2021-11-16
> **ajgreeny said:**
> Sounds like another case of design over function! One

They do make life difficult don't they.

Indeed. But what good would a security feature be if it was easily bypassed?

---

