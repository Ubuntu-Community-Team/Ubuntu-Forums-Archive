---
title: "Intel Haswell integrated graphics"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by sam70 on 2014-08-17
I have searched for a while on these forums.. I've got Ubuntu 14.04 on a Sony Vaio Flip 14, and I've used ubuntu before, except now the laptop works great, love it so much better than windows, but the monitor flashes. I've read to disable R and R but i don't really know how? The monitor flashing doesnt bother me so much, but after using it for about an hour, the display completely shuts off. I was just wondering if anyone else has experienced this, and if its just some simple setting I need help with. Thank you very much!

---

### Post by user1397 on 2014-08-18
what exactly do you mean by "[COLOR=#000000]I've read to disable R and R" and where did you read that?[/COLOR]

---

### Post by sam70 on 2014-08-18
I can't find where I read it, it was a forum post somewhere said to go to system>preferences>disable randr. Obviously Ubuntu 14 does not have "System" anymore so I could not do this.

---

### Post by papibe on 2014-08-18
Hi sam70. Welcome to the forums ):P

Could you open a terminal, run this command, and post back its results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by sam70 on 2014-08-18
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)   
Subsystem: Sony Corporation Device [104d:90c3]
Kernel driver in use: i915

```

---

### Post by papibe on 2014-08-18
Thanks.

I see that you have a Intel Haswell integrated graphics. Intel graphics should be one the best supported graphic cards, however since yours seem to be fairly new, upgrading the driver could solve your problem.

Try this one first:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then restart and see how it goes.

Only if that doesn't work either, there's another ppa with bleeding-edge versions:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Same idea.

Let us know how it goes.
Regards.

---

### Post by sam70 on 2014-08-18
Thanks,
Let me be a little more clear on the flicker.. Just to be sure. It's not a continuous flicker. its like, every few seconds or even minutes, the screen will blink. It seems to be when there is a lot of motion on the screen it happens more frequent, but I cannot verify that.This would not bother me so much, except after maybe 30 min - 1 hour of use, the screen just dies. I know the computer is still on because music is still playing, I can save whats on my desktop with ctrl+s, etc.
Now I tried both of those, the first one seemed not to upgrade anything...so I wasn't very hopeful and sure enough it blinked the same.
The second one, a lot more was upgraded and I was getting excited and I rebooted my machine, started watching a youtube video, and it was blinking every couple of seconds. Except, now that I'm typing this, I haven't noticed any blinks. Whether I'm used to it, or I've been staring at my keyboard I'm not really sure.

---

### Post by sam70 on 2014-08-26
I just wanted to mention, a week later my vaio has been working great. The screen still blinks every once in a while, its clear when I'm watching videos and such. The touchscreen now hangs up after using it for a while, but that's no where near important to me, as long as the mouse works(which has nothing to do with video) I'm happy. Thank you very much! I appreciate the help greatly!

---

### Post by mörgæs on 2014-08-26
Good, please mark the thread 'solved'.

---

### Post by sam70 on 2014-09-03
Well it's still blinking constantly, watching videos, doing any intense work, constant blinking. The display no longer shuts off completely, but the blinking is more frequent. Do I just have to live with it?

EDIT:

After the latest update, my laptop screen will shutoff after about 2 hours of use. Does being a touchscreen have anything to do with this?

---

