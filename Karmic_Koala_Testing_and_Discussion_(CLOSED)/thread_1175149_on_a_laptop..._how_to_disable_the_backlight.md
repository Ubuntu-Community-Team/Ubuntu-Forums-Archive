---
title: "on a laptop... how to disable the backlight?"
date: 2009-05-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by inportb on 2009-05-31
Sometimes I want to save some power and just disable the backlight altogether. I've seen somebody else do it, so thought that it might be possible with my laptop too. Here's my video chipset:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Can this be done?
Thanks.

---

### Post by psyke83 on 2009-05-31
> **inportb said:**
> Sometimes I want to save some power and just disable the backlight altogether. I've seen somebody else do it, so thought that it might be possible with my laptop too. Here's my video chipset:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Can this be done?
Thanks.

See: [http://www.thinkwiki.org/wiki/LCD_Brightness](http://www.thinkwiki.org/wiki/LCD_Brightness)

---

### Post by syko21 on 2009-05-31
```
sleep 1; xset dpms force off
```

---

### Post by inportb on 2009-06-01
does this just turn off the backlight or does this turn off the lcd too?

@psyke83: yeah... my brightness seems to have a minimum that's way above zero =/

---

### Post by phenest on 2009-06-01
> **inportb said:**
> does this just turn off the backlight or does this turn off the lcd too?

Isn't that the same thing? Surely when the LCD goes off, so does the backlight?

---

### Post by syko21 on 2009-06-01
Turns off both

---

### Post by inportb on 2009-06-02
> **phenest said:**
> Isn't that the same thing? Surely when the LCD goes off, so does the backlight?

Yeah well... how is one supposed to read the screen? Does passive lighting work?

---

### Post by diebels on 2009-06-02
> **inportb said:**
> Sometimes I want to save some power and just disable the backlight altogether. I've seen somebody else do it, so thought that it might be possible with my laptop too. Here's my video chipset:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Can this be done?
Thanks.

Sure you don't mean turning it all the way down? That is usually down with shortcut keys on laptops.

---

### Post by elleke on 2009-06-02
i'm not sure if this is the thing you are looking for, but i was struggling lately with this kind of problem in the console mode (i've installed ubuntu on an old laptop to use it as an internal server).

if the command
```
sudo vbetool off (or "on" afterwards)
```
works, but 
```
setterm –powersave powerdown
setterm –powerdown 1
setterm –blank 1
```
leaves the backlight after 1 minute still on, it means there is a problem with framebuffer driver.
after comparing the source code of **vbetool** with the framebuffer drivers source you can find out, that only the **uvesafb** driver works the same way. 
it is assumed, that a frame buffer based virtual console is used. you can check that by typing ```
lsmod
``` and looking for **fbcon**.
to use **uvesafb** you have to install **v86d** first: ```
sudo apt-get install v86d
```. then try to load the kernel module:```
sudo modprobe uvesafb option_mode=640x480-8 mtrr=0 scroll=redraw
```
**option_mode** should be sometimes replaced with **mode**. if there are any problems, check the ```
dmesg | grep vesa
```.
if everything is ok, **lsmod** should show **uvesafb** as used. now the **setterm**-sequence should work.
the **uvesafb** options i suggested are good for testing. if it works, you can start experimenting with other screen resolutions and **mtrr=3 scroll=ywrap** (on my old laptop the **ywrap** option was causing a segmentation fault...). a lot of additional information you can find on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269")

i've tested it on an ibm t60 laptop (ubuntu 8.10) and on the old CTX 700e EzBool (ubuntu 9.04) - in both cases it works very well and safes a lot of energy!

greets,
elleke

---

### Post by inportb on 2009-06-02
Thanks for the tips. Yeah, I do mean turning it all the way down... except mine doesn't go all the way down =/

---

### Post by phenest on 2009-06-03
> **inportb said:**
> Yeah well... how is one supposed to read the screen? Does passive lighting work?

Can the screen still be "read" without the backlight?

---

### Post by inportb on 2009-06-03
> **phenest said:**
> Can the screen still be "read" without the backlight?

I believe so... the LCD itself simply modulates the opacities of the tricolors at specific positions, which results in pixels of varying color when the white backlight shines through.

Naively, one might imagine that without a backlight, no pixels would be visible... but wait! There's always ambient light, which could reflect off the back of the LCD, acting as the light source. This is how your pocket calculator works, anyway.

---

### Post by psyke83 on 2009-06-03
> **inportb said:**
> I believe so... the LCD itself simply modulates the opacities of the tricolors at specific positions, which results in pixels of varying color when the white backlight shines through.

Naively, one might imagine that without a backlight, no pixels would be visible... but wait! There's always ambient light, which could reflect off the back of the LCD, acting as the light source. This is how your pocket calculator works, anyway.

A calculator's LCD screen is monochrome, though. A laptop LCD panel without a functioning backlight is almost impossible to read (and "ambient light" will probably increase the reflectivity, making the screen even harder to see). Trust me - I've got a laptop with a busted backlight, and another laptop with a backlight that's dying (it has a pinkish hue).

---

### Post by jfernyhough on 2009-06-03
I've found my previous (5685) and current (5930) Acers to have (what I assumed to be) a transflective screen, i.e. it takes in and reflects sunlight. A Vostro with Truelife also seems to do the same, but not to quite the same extent. This means that using the laptop in direct sunlight is actually doable, which is nice. In this case, the backlight is rendered completely useless and as such is sucking up power for no reason.

My Acer has a backlight-off function key, but it comes back on again as soon as I press a key or move the mouse.

---

### Post by inportb on 2009-06-04
Hmm... idk if my LCD is transflective; but I'd love to *try*...

> **psyke83 said:**
> A calculator's LCD screen is monochrome, though.

Yeah, and a laptop's LCD is 3x monochrome.

---

### Post by danf_1979 on 2009-06-07
Try:
```

$ xset dpms force off

```

---

### Post by inportb on 2009-06-07
> **danf_1979 said:**
> Try:```
$ xset dpms force off
```

Uh, yeah that disabled the backlight alright, but it sorta kinda also turned off the LCD; are you sure about this method?

I know the LCD was turned off (not just that I could not read it due to low lighting) because it promptly turned back on when I touched the touchpad.

---

