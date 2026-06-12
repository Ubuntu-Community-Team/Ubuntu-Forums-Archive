---
title: "ATI card in Jaunty"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snkngshps on 2009-03-31
When I first upgraded to Jaunty, my ATI graphics card apparently wasn't compatible and instead of being able to login to my desktop I was getting crazy distorted screens and wasn't able to do anything.

With the help of the people on [this thread]("http://ubuntuforums.org/showthread.php?t=1108351") I was able to work-around the problem, but I think it was done so by disabling the graphics card driver. My question is, is there a driver that is compatible with my graphics card (detailed in my signature) that will work in Jaunty? Here are the steps I took, with the advice of those in the thread.

I deleted the xorg.conf file by running:

```
sudo rm /etc/X11/xorg.conf
```

Then I removed the fglrx driver:

```
sudo apt-get purge xorg-driver-fglrx
```

Since then I've been able to log in but I still get occasionally distorted screens. They only last for a second or two, and normally only during login but this tells me that I'm probably not running my graphics card correctly.

---

### Post by comandrei on 2009-03-31
The ATI drivers are still incompatible with the X Server 1.6 . I think it's best to wait for the final release (hopefully things will be sorted out by then).

---

