---
title: "Ubuntu 11.04 purple grub background"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by kuramayoko10 on 2011-05-14
Hi, 

I've just upgraded my ubuntu to 11.04 64-bit version. I am happy with it but I have two things annoying me so far:

1) My grub background is horribly purple. It was black and white before the upgrade. How can I make it black/white again?
2) Is there a real (non-glitchy) way of putting the unity dock to the bottom of the screen instead the left side?

Thanks in advance,

---

### Post by jocefus on 2011-05-20
> **kuramayoko10 said:**
> 
1) My grub background is horribly purple. It was black and white before the upgrade. How can I make it black/white again?

I have always been partial to simple white (or green) on black console setups as well.

This has something to do with the new feature they implemented involving the improved grub background image handling. I haven't studied up on it completely, but I was able to remedy this by editing /lib/plymouth/themes/default.grub

Of course save the original (I copied the original to default.grub.old)
The original reads:
```

if background_color 44,0,30; then
  clear
fi

```I changed that too:
```

if background_color 00,00,00; then
  clear
fi

```Then run:
```

sudo update-grub

```Not sure if this is the correct way of accomplishing this, more research is needed, but it brought back the white on black background for my grub screen.

Hope this helps.

---

### Post by jaapdam on 2012-06-25
I found this thread when searching for 12.04 and the purple/magneta grub background. I fixed it by changing the parameters you gave. I also edited the /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script so that also the splash screen of Ubuntu itself is black, instead of purple. I changed this

```
# Previous background colour
# #300a24 --> 0.19, 0.04, 0.14
# New background colour
# #2c001e --> 0.17, 0.00, 0.12
Window.SetBackgroundTopColor (0.17, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.17, 0.00, 0.12);  # an equally nice colour on the bottom
```

to

```
# Previous background colour
# #300a24 --> 0.19, 0.04, 0.14
# New background colour
# #2c001e --> 0.17, 0.00, 0.12
# Personally ajusted color to black #000000 --> 0.00, 0.00, 0.00
Window.SetBackgroundTopColor (0.00, 0.00, 0.00);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);  # an equally nice colour on the bottom
```

After doing this i updated grub```
sudo update-grub
``` and all is black now! Yay!

---

