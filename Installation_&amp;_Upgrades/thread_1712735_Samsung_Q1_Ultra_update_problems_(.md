---
title: "Samsung Q1 Ultra update problems :("
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by Marcia-y on 2011-03-23
Hi,

I've been loving the Maverick install up until now on my tablet but at the moment weird issues have developed from trying to upgrade the Linux Image/Headers from 2.6.35-25.

2.6.35-27 and 2.6.35-28 updates will refuse to engage graphics after bootup, blank screen flashes 2-3 times then nothing but black deadness on the screen.

The second weird thing that has happened is when reverting back to 2.6.35-25, when I rotate the screen through the grandr applet 90 degrees or more my LCD brightness falls to minimum, I'm unable to adjust it to any setting above that afterwards and a logout-login or reboot is required to sort the problem but then I'm back on normal screen setting in grandr when I do :(

My unit is a NP-Q1U with the quirky keyboard.

I would be so grateful If somebody could help me :)

Thanks...

---

### Post by Dutch70 on 2011-03-23
What graphics card do you have in your computer?

---

### Post by Marcia-y on 2011-03-23
Hi Dutch70,

I have a Integrated Intel® 945GMS 3D graphics with 128MB shared memory.

The unit is the same model as in the link below:

[http://www.saveonlaptops.co.uk/Samsung_Q1_Ultra_412098.html](http://www.saveonlaptops.co.uk/Samsung_Q1_Ultra_412098.html)

But I've replaced the old HDD with a 64GB SSD one and added 2GB memory too.

---

### Post by Dutch70 on 2011-03-23
This is something I haven't had to deal with yet, but have you checked to see if there are drivers available. 
You can check by going to system > admin > additional drivers.

---

### Post by Marcia-y on 2011-03-24
I have freshly reinstalled Maverick last night and on my previous install I did update the graphics driver via xorg to the very latest. This time I didn't, my LCD back-light is ok now but still the same problem with graphics not starting up, blinking blank screen for a short while and no desktop etc on updating past 2.6.35-25 again :(

It doesn't ask anything through "system > admin > additional drivers" 

It's very strange... Dutch70 :-k

---

### Post by Dutch70 on 2011-03-24
Check this thread, see if you can find anything useful there, otherwise you may want to log-in to an older kernel & remove the latest kernel.
[[COLOR="Blue"]http://www.linuxforums.org/forum/ubuntu-linux/123126-white-screen-after-kernel-update.html[/COLOR]]("http://www.linuxforums.org/forum/ubuntu-linux/123126-white-screen-after-kernel-update.html")
.

---

### Post by Marcia-y on 2011-03-24
Unfortunately the reinstall of the intel driver didn't work, after a fluke on managing to make 2.6.35-28 to work once I found wireless, touch screen and mouse buttons didn't work so if the graphics did work I think other drivers would have had to have been fixed too :(

I hope the next new distribution will work ok, I do love using Ubuntu on this little machine :)

Thankyou so much for your help Dutch70 :D

---

### Post by Dutch70 on 2011-03-24
You're quite welcome. 

 Don't give up too soon, I may know someone that knows more about this. I'll see if they care to take a look.

---

### Post by oldfred on 2011-03-24
I am afraid I know nothing about tablets.

I did find this for Hardy (8.04).
[http://packages.ubuntu.com/hardy/ume-config-samsung-q1-ultra](http://packages.ubuntu.com/hardy/ume-config-samsung-q1-ultra)

I checked in synaptic and it is not currently available, so I do not know if it is obsolete or only designed to work with Hardy?

Update:
It was replace with moblin. Have you added in the moblin packages. Not sure what is best for your system. There seem to be a lot in synaptic.

---

### Post by Marcia-y on 2011-05-06
Hi oldfred, thankyou for your advice but the the document was too old for 10.10. I've reverted back to a the working 2.6.35-25 instead. 

I did try to install the new 11.04 version with hope but without luck. When I install it on a external hard drive and boot from there the touch screen works great but if I install on the machines internal drive the touch screen fails very badly. They have scrapped the evtouch driver and improved the evdev driver to compensate though it doesn't seem to work correctly :(

---

