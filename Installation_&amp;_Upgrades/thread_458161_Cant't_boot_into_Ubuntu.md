---
title: "Cant't boot into Ubuntu"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by JanErikHiim on 2007-05-29
I have a big problem,.
I've just installed windows after having ubuntu a wile. But now I cant choose between booting linux and windows. The linux files is in a disk called disk1 when I load the live ubuntu cd. I've tryed "linux rescue" but then it sais no kernel image: linux........
I did not formatted anything when I partitioned the disk...
Anyone plese help!!!!!

Urgeny.-)

---

### Post by happy-and-lost on 2007-05-29
Sounds like your MBR's been overwritten. No fear, boot into the liveCD, fire up a terminal and type:

*sudo grub*

It'll take you to the grub setup thingy. First type...
[I]
root (hdx,x)[/I]

where x,x is the location of Ubuntu. (for a one drive setup it'll be hd0,x), press tab when you've typed (hd0, and it'll come up with a list of available drives, you should be able to identify the one you want fairly easily from that. then...

*setup (hd0)*

exit grub by typing *quit*

Which will restore Grub to your MBR.

However, it won't have a menu entry for Windows, so when you've booted into Ubuntu, open up a terminal and type:

*sudo gedit /boot/grub/menu.lst*

and add to the bottom...
[I]
title           Windows
root            (hd0,x)
savedefault
makeactive
chainloader     +1[/I]

Where x is the location of your Windows installation.

Which should do the trick.

---

### Post by JanErikHiim on 2007-05-29
I will try...
Thank you for this great community..The help is quicker then microsoft callcenter....
I Love Ubuntu, and the forums:-) 
Needed windows just for one thing... The Microsoft Autoroute..... Can't say I'm happy...

Will write back and tell how this went....


Thanks..


Jan Erik
Norway

---

### Post by JanErikHiim on 2007-05-29
I\m not doing this right..... I think...

Here is what the terminal sais>>

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd2,2)

Error 21: Selected disk does not exist

grub> root (hd1,1)

Error 21: Selected disk does not exist

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub>

---

