---
title: "Boot - Black screen with purple border"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by tiaborrelli on 2014-05-26
Hi, i have a problem when i boot the pc.
After the installation of Ubuntu a black screen with a purple box appeares without let me see the choice of GRUB, then the screen becomes black and Ubuntu starts booting.
Ubuntu is the only OS installed but it's quite annoying can't see the option of the bootloader.

Can anyone help me?

---

### Post by ben-schweitzer on 2014-05-26
The screen is most likely just processes starting. Try holding shift before the purple screen to see the GRUB menu.

---

### Post by tiaborrelli on 2014-05-26
I tried that this afternoon and it showed me the processes starting, but now holding shift seems not working.

---

### Post by jeremy31 on 2014-05-26
If it is a laptop, try using the FN shortcut to increase the display brightness or plug in an external monitor if you have one

---

### Post by tiaborrelli on 2014-05-26
Yes i have a laptop but it doesn't work FN + brightness, sadly now i can't plug in an external monitor. 
I'll try tomorrow. Any other suggestions?

---

### Post by MirkoCe on 2014-05-26
To show grub menu

```
gksu gedit /etc/default/grub
```

and edit the following like that (don't forget the #)

```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=4
```

You can change 4 with whatever you like.

then do
```

sudo update-grub
```

that should be all.

---

### Post by tiaborrelli on 2014-05-26
Thank you! That solved the problem!

---

### Post by KillEmAllx on 2014-06-20
> **MirkoCe said:**
> To show grub menu

```
gksu gedit /etc/default/grub
```

and edit the following like that (don't forget the #)

```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=4
```

You can change 4 with whatever you like.

then do
```

sudo update-grub
```

that should be all.

I have the same problem, black boot screen with purple frame. How do I fix it without turning grub on? Ubuntu is the only OS on my laptop, so I don't really need grub.
Also, anyway to make the purple stuff black?

---

### Post by MirkoCe on 2014-06-23
Hello,
I also changed my grub to black as I had the same problem. Just do

```
 
sudo -H gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.grub 

```

And change to 

```

if background_color 0,0,0 ; then
   clear
fi 
```

then 

```
 sudo update-grub 
```

Tell me if it worked!

---

