---
title: "VMware Server and Ibex"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by darco on 2008-08-02
Well I am now running Ibex in VMWare Server because I wanted the full screen effect and any other perks that VB doesnt have. I was able to install Ibex fine with the Alternate CD. Now the issue is no matter where I left click the mouse in the screen, it opens up the Trash. Even clicking the X to close brings up another Trash window! Right click brings up the panel menu.....Re installed, same issue. 
Back to VB and the small screen

darco

---

### Post by Kokopelli on 2008-08-03
This is actually quite simple to fix.  

login at a command prompt and type the following command:

```

sudo sed -i -e 's:vmmouse:mouse:g' /etc/X11/xorg.conf

```

or if you prefer go into /etc/X11/xorg.conf and replace the line
```

Driver "vmmouse"

```

with
```

Driver "mouse"

```

---

### Post by darco on 2008-08-03
Hey thanks...that worked fine....

darco

---

