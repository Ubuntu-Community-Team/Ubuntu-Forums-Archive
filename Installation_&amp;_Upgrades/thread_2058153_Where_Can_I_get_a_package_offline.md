---
title: "Where Can I get a package offline ?"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by DR AMD on 2012-09-15
[LIST]
[*]**Hello Ubuntu Team,**
[*]**I have 2 computer in two different areas .. one run Windows and the other run Ubuntu.**
[*]**the Windows PC have Internet connection yet the other one not **
[*][COLOR=Red]**I want to know a way to get source or .deb package for the Ubuntu and copy them to a flash drive and install them later to the Ubuntu Desktop without need to an Internet connection on the Ubuntu one**[/COLOR]
[*][COLOR=DarkGreen]**Any Ideas !!!!!**[/COLOR]
[*]**Thanks **
[/LIST]

---

### Post by Bucky Ball on 2012-09-15
Which apps are you after? Get a list then hunt down the .deb files.

---

### Post by DR AMD on 2012-09-15
> **Bucky Ball said:**
> Which apps are you after? Get a list then hunt down the .deb files.

thanks for your replay

I just want to know a way to know a general or major way to hunt .deb packages for any program already on the software center

for example ...
Adobe flash Player
Multimedia Program codes

---

### Post by Bucky Ball on 2012-09-15
[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8IvOlRQDGkARHoK5gt.;_ylc=X1MDMjExNDcwOTAwMgRfcgMyBGFvA2FvBGNzcmNwdmlkA3lHaS5PN2V4VTdlVVBmMWh4OHpLc1JtVGNzWkk2RkJVT2k0QUI5ak4EZnIDYWx0YXZpc3RhBGZyMgNzYnRuBG5fZ3BzAzEEb3JpZ2luA3N5YwRwcXN0cgNhZG9iZSBmbGFzaCBwbGF5ZXIgb2ZmbGluZSBpbnN0YWxsBHF1ZXJ5A2Fkb2JlIGZsYXNoIHBsYXllciBvZmZsaW5lIGluc3RhbGwEc2FvAzE-?p=adobe%20flash%20player%20offline%20install&fr=altavista&fr2=sfp&pqstr=adobe%20flash%20player%20offline%20install]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8IvOlRQDGkARHoK5gt.;_ylc=X1MDMjExNDcwOTAwMgRfcgMyBGFvA2FvBGNzcmNwdmlkA3lHaS5PN2V4VTdlVVBmMWh4OHpLc1JtVGNzWkk2RkJVT2k0QUI5ak4EZnIDYWx0YXZpc3RhBGZyMgNzYnRuBG5fZ3BzAzEEb3JpZ2luA3N5YwRwcXN0cgNhZG9iZSBmbGFzaCBwbGF5ZXIgb2ZmbGluZSBpbnN0YWxsBHF1ZXJ5A2Fkb2JlIGZsYXNoIHBsYXllciBvZmZsaW5lIGluc3RhbGwEc2FvAzE-?p=adobe%20flash%20player%20offline%20install&fr=altavista&fr2=sfp&pqstr=adobe%20flash%20player%20offline%20install")

Just wondering, though. Flash Player is a browser plug in and as your Ubuntu machine is not online ...

I don't know what 'Multimedia Program Codes' are, sorry. Do you mean codecs?

Are you really using 9.04? It has been unsupported for nearly two years. ;)

There are other options: Could you install Ubuntu to a USB stick, boot from that, install the .debs you want to it then look in:

/var/cache/apt/archives/

Any old .debs should be in there I think ... someone correct me if I'm wrong. I would also suggest a wireless dongle for the Ubuntu machine but this would require a wireless router also. If you have a regular router, how far away is that? I use a 15 metre ethernet cable and I believe longer is possible. Could you put the router halfway? 

Of course, none of this may be possible, but just throwing in some ideas ...

---

### Post by DR AMD on 2012-09-15
> **Bucky Ball said:**
> [http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8IvOlRQDGkARHoK5gt.;_ylc=X1MDMjExNDcwOTAwMgRfcgMyBGFvA2FvBGNzcmNwdmlkA3lHaS5PN2V4VTdlVVBmMWh4OHpLc1JtVGNzWkk2RkJVT2k0QUI5ak4EZnIDYWx0YXZpc3RhBGZyMgNzYnRuBG5fZ3BzAzEEb3JpZ2luA3N5YwRwcXN0cgNhZG9iZSBmbGFzaCBwbGF5ZXIgb2ZmbGluZSBpbnN0YWxsBHF1ZXJ5A2Fkb2JlIGZsYXNoIHBsYXllciBvZmZsaW5lIGluc3RhbGwEc2FvAzE-?p=adobe%20flash%20player%20offline%20install&fr=altavista&fr2=sfp&pqstr=adobe%20flash%20player%20offline%20install](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8IvOlRQDGkARHoK5gt.;_ylc=X1MDMjExNDcwOTAwMgRfcgMyBGFvA2FvBGNzcmNwdmlkA3lHaS5PN2V4VTdlVVBmMWh4OHpLc1JtVGNzWkk2RkJVT2k0QUI5ak4EZnIDYWx0YXZpc3RhBGZyMgNzYnRuBG5fZ3BzAzEEb3JpZ2luA3N5YwRwcXN0cgNhZG9iZSBmbGFzaCBwbGF5ZXIgb2ZmbGluZSBpbnN0YWxsBHF1ZXJ5A2Fkb2JlIGZsYXNoIHBsYXllciBvZmZsaW5lIGluc3RhbGwEc2FvAzE-?p=adobe%20flash%20player%20offline%20install&fr=altavista&fr2=sfp&pqstr=adobe%20flash%20player%20offline%20install)

Just wondering, though. Flash Player is a browser plug in and as your Ubuntu machine is not online ...

I don't know what 'Multimedia Program Codes' are, sorry. Do you mean codecs?

Are you really using 9.04? It has been unsupported for nearly two years. ;)

There are other options: Could you install Ubuntu to a USB stick, boot from that, install the .debs you want to it then look in:

/var/cache/apt/archives/

Any old .debs should be in there I think ... someone correct me if I'm wrong. I would also suggest a wireless dongle for the Ubuntu machine but this would require a wireless router also. If you have a regular router, how far away is that? I use a 15 metre ethernet cable and I believe longer is possible. Could you put the router halfway? 

Of course, none of this may be possible, but just throwing in some ideas ...

Thanks
but
I am using Ubuntu 12.04 but cannot change the profile

the link you given to me is .exe not .deb 
I am using programs that relay on the browsers .. off-line of course

---

### Post by Neoracu on 2012-09-15
Do you have Ubuntu One?

What you want seems like kinda difficult.

I'd suggest you to share the internet conexion from your Windows Computer to your Ubuntu machine, through ethernet, if you can get them close enough.

Or I offer you a deal... :lolflag:

If you don't have Ubuntu One, sign up using [THIS]("https://one.ubuntu.com/referrals/referee/1315024/") link and I'm willing to upload all my debs(and the ones you request), after that you can download them in your Windows machine
- Pass it to your Ubuntu Machine with a memory stick or Portable Hard Drive.
- Once in your Ubuntu machine you install APTOnCD.
- Using APTOnCD you can create an image with the packages you've downloaded, burn it to CD's or a DVD(I suggest a rewritable one, so you can reuse it in the future).
- Then you can install whatever you want(available) using synaptic, as APTOnCD adds your APTOnCD as a sourcelist in synaptic.

Thing is that for some packages like *flash-plugin-installer* and *mscorefonts* you need internet conexion, or use the method stated by **Bucky Ball**.

Best Regards

---

