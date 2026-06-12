---
title: "XWindow says I have no monitor when I try to install Edgy."
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Pateros on 2007-02-03
I've downloaded the Edgy iso from the main Ubuntu site and burned it to a disc like I would any other. The disc loaded fine and I was at the main screen and I selected Start Ubuntu.

It looked like it was starting fine but then the screen bugged out and went to a blue screen with a dialogue prompt that said XWindow had messed up, It asked if I wanted to see the logs  and I checked them out. The logs said I had no monitor. How do I fix this? I even tried using a 6.06lts disc I got from ShipIt and that gave me the same error.

I have a nVidia GeForce 8800gts, would this have anything to do with it?

Thanks for any help.

---

### Post by taurus on 2007-02-03
Try using the alternate CD to install Edgy on your machine then.

---

### Post by Pateros on 2007-02-03
All installed well until I actually attempted to get into Ubuntu when the same error happens.

---

### Post by taurus on 2007-02-03
So you are currently logged in to a console!  Try running this command to reconfigure your X again.  And if you are not sure about a question, just use the default value and pick **vesa** as the driver for your graphic card for now.

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Pateros on 2007-02-06
> **taurus said:**
> So you are currently logged in to a console!  Try running this command to reconfigure your X again.  And if you are not sure about a question, just use the default value and pick **vesa** as the driver for your graphic card for now.

Still didn't work for me :( 

Is there anyone out here successfully using Ubuntu with a 8800gts?

---

