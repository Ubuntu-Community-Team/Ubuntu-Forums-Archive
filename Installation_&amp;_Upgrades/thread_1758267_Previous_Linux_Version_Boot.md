---
title: "Previous Linux Version Boot"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by skatona on 2011-05-14
I upgraded from 10.10 to 11.04. on boot up I sometimes get only the purple screen freeze and sometimes I actually get to the grub menu. I select the generic kernel and get the black screen freeze.  same if I do the recovery mode.  but if I get lucky on a reboot and can get the grub menu up again, I select previous linux version and then select 2.6.35 generic and it will boot into 11.04 with Unity. 

So, how can I get this thing to boot normal with the correct kernel version?  I am fairly new to this linux world and don't want to have to go back to windows if I can help it.  Thanks

---

### Post by MAFoElffen on 2011-05-14
> **skatona said:**
> I upgraded from 10.10 to 11.04. on boot up I sometimes get only the purple screen freeze and sometimes I actually get to the grub menu. I select the generic kernel and get the black screen freeze.  same if I do the recovery mode.  but if I get lucky on a reboot and can get the grub menu up again, I select previous linux version and then select 2.6.35 generic and it will boot into 11.04 with Unity. 

So, how can I get this thing to boot normal with the correct kernel version?  I am fairly new to this linux world and don't want to have to go back to windows if I can help it.  Thanks
Welcome,

Please add info about:
1. What kind of PC you have.
2. What kinf of Graphics card if you known.

Please refer to this sticky:
[http://ubuntuforums.org/showthread.php?p=10811436#post10811436](http://ubuntuforums.org/showthread.php?p=10811436#post10811436)
And review the first 3 posts.  It will give a summary of info on how to get to a text console
and diagnose you problem.

Post post the results of 
```

hwinfo --framebuffer
hwinfo --monitor

```
and remeber to press the ' # " button and paste the info between the code tags.

---

### Post by skatona on 2011-05-15
I gave up.  I went back to 10.10.  11.04 IMO, was not ready to be released.  I will wait for the next release before trying again.

As for the computer .. ThinkPad W500.  Not sure what the graphics card is, but what ever is the standard in the W500.  Also running with 8GB of RAM.  Running vmware with WIN 7 as a guest.  11.04 just did not work. I tried a clean install as well, from a CD.  Then just went back to 10.10 and have not had 1 glitch.  

Thanks...  Steve

---

### Post by MAFoElffen on 2011-05-15
> **skatona said:**
> I gave up.  I went back to 10.10.  11.04 IMO, was not ready to be released.  I will wait for the next release before trying again.

As for the computer .. ThinkPad W500.  Not sure what the graphics card is, but what ever is the standard in the W500.  Also running with 8GB of RAM.  Running vmware with WIN 7 as a guest.  11.04 just did not work. I tried a clean install as well, from a CD.  Then just went back to 10.10 and have not had 1 glitch.  

Thanks...  Steve
Congrats. If you ever decide to  try again...
> Model 300
14.1" 16M color TFT 1024x768
12.1" 16M color TFT 800x600         
Video = NeoMagic MagicMedia 256AV (NM2200) 2.5M
You might have gotten by, by editing /etc/default/grub, looking for line 
```

# GRUB_GFXMODE=640x480

```and changing it to 
```

GRUB_GFXMODE=640x480x24

```then adding 
```

GRUB_GFXPAYLOAD=text

```Saving, exiting, then running 
```

sudo update-grub

```
to pick up the changes in Grub.

Those are the graphics changes between running 10.10 and 11.04 for "your" IBM Thinkpad/Lenovo laptop.

---

### Post by skatona on 2011-05-15
thanks.  I have an extra hard drive so I may give that a try some time this week.

---

### Post by skatona on 2011-05-17
I gave it a try last night and no luck.  the line you mentioned:
# GRUB_GFXMODE=640x480
actually was:
#GRUB_GFXMODE=640x480
and I changed it to:
#GRUB_GFXMODE=640x480x24
and added another line right afterwards:
#GRUB_GFXPAYLOAD=text
upgraded grub
no change.  then tried:
#GRUB_GFXMODE=640x480x24
GRUB_GFXPAYLOAD=text
and no luck again.

---

