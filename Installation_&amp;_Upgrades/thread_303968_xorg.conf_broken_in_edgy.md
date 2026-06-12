---
title: "xorg.conf broken in edgy?"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by obliv10n on 2006-11-21
I upgraded a completely working dapper to edgy using the recommended method, but now can't get a graphic interface for gnome. :( 

My xserver error log contains nothing helpful -- 

(EE) No devices detected

and

no screens found

I've tried various guesses at reconfiguring xserver-xorg, but nothing works. I'm still new enough at all this that I don't really know what I'm doing... :-? 

I have an ancient Dell Optiplex GX1 with onboard ati graphics, but dapper ran fine without any tweaking. So does my dual-boot to Win98, which is how I got here... ;)

Can anyone suggest anything?

---

### Post by Jimmey on 2006-11-21
Ehrm...

You might want to try this. 

Edgy might be complaining because you're tyring to use the wrong grpahics driver. So, if you try [again] "sudo dpkg-reconfigure xserver-xorg" and from the Driver selection menu, select "vesa" (A pretty failsafe option, I think...), then you might be able to get a desktop. 

Edgy's got a new kernel, so if installing ATI's graphics drivers is anything like installing nVidias, you'll need to get the updated kernel modules for your kernel aswell. Then just install the proper ATI drivers, and you'll probably be all set.

---

### Post by obliv10n on 2006-11-21
Hi, Jimmey:

Thanks for getting back to me... unfortunately, I don't get any option to select a driver when I run 

sudo dpkg-reconfigure xserver-xorg

I get a query about whether to try to autodetect graphics hardware, and then get taken through a series of questions, which are the same either way, although the answers are prefilled with -- apparently -- sensible answers if I choose the autodetect route. (If I autodetect, it prefills the video card identifier with "ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"; if I don't, it's "Generic video card" or somesuch.) If I'm reading the screen right, this text is just text, so changing it to VESA isn't likely to help -- or is it?

Anyway, it then asks for the BusID of the card. (It suggests the use of "lspci -X" to determine this, but that's not a valid argument. "lspci -x" is valid, but this makes me wonder if something's got out of sync somewhere...)

Or am I being very stupid about something? :-k 

-- 
Tim

---

### Post by taurus on 2006-11-21
Maybe try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by surfer57 on 2006-11-25
mine was saying that it was broken or not completely installed....so I typed in the following

sudo apt-get install xserver-xorg

xserver installed and I am now finishing my upgrade to edgy....


my kung fu is strong :cool:

I love this stuff....

*U cannot find the word freedom in microsoft*

---

