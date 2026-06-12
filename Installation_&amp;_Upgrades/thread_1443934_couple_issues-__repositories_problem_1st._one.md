---
title: "couple issues-  repositories problem 1st. one"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by jmarz on 2010-03-31
I think it has  a typo??
 'armic'


[['E:Type 'armic-security' is not known on line 38 in source list /etc/apt/sources.list, E:The list of sources could not be read.']]


I have no clue how to fix this. how would I get into the place to fix this - is it just  aweird typo ?
-- it was fine until the last time I did some updates and got new stuff downloaded.


pretty much a rookie  - so if any terminal suggestions for me to do ...
 if you can post stuff I can copy/ paste that would be great cause I have hand rsi injuries.
:)

*****************

dual boot sys with XP --  xp on one drive & the Linux OS and storage on the other drive {partitioned}-
**************************

Another prob is I can't get any other OS or Live CD  to install from CD -  another OS or even the 9.10 again . 
CD drives are enabled - lights up but system always goes to the grub and boot list.
??

Is it the Ubuntu start up manager causing this?

the kubuntu 9.10 did the same thing to me so had to nix it and reinstall the xp boot stuff and then tried the Ub 9.10 and still can't add any other Linux OS. Or even boot a live CD.

Any help on one problem or the other would be appreciated...

---

### Post by ajgreeny on 2010-03-31
In a terminal type gksudo ```
gedit /etc/apt/sources.list
``` hit enter and then enter your password in the prompt.  The text editor will open with that file in it, that you can edit and change **armic** on line 38 to **karmic**.

Save the file, then close gedit and try to run ```
sudo apt-get update
``` in terminal.

For the other problem of not being able to boot from a CD to install another OS, go into your BIOS and set the CD drive to be the first boot disk in the list.

---

### Post by jmarz on 2010-03-31
thanks so much - i didn't work at first but then I noticed the whole first part of the loc was missing so added that and saved then followed the rest of your post and so far so good.


 CD drive is set as first boot dev in BIOS, just double checked to make sure nothing has changed it.

So I'm still confused as to why i can't boot any other Live Cd OS.

I put the boot stuff @ the MBR is that the usual way to go and not in the root? I think that was the other option??.

the other times I installed Linux OSs - U, K, mepis, and some others - I did it that way and all was fine I could still load up other Live cd & install them too.

I guess I haven't found the best ONE for me yet- but U & Mepis are favs so far.
 Love the 9.10 import of my pics & docs from XP that is a biggy improvement in my eyes.

---

