---
title: "Xserver Error"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by robcarr2 on 2007-02-13
Hello,

Well I used Ubuntu for quite a long time, however I got rid of it for a while and now I am trying to install again and I am constantly getting an Xserver error saying that No screens were found.

I am using the same graphics card I was with my previous installation, same monitor, the only thing different in my entire setup is my mouse!

Anyway I am going insane trying to fix this, I have tried my old Ubuntu distro that I have on disk, I have downloaded Edgy but I have no luck, I constantly get this error.

Could it be the slot that my graphics card is in?

I am using an ATI Radeon X300 SE 128mb PCI-E card

I have tried reconfiguring xserver with the default settings for every option but it had no effect.

Please if anyone has any ideas what could be wrong then put them forward as I am desperate now :)

---

### Post by taurus on 2007-02-13
Log in to a console and run

```
sudo dpkg-reconfigure xserver-xorg
startx
```
Use **vesa** as your driver for your graphic card.

---

### Post by robcarr2 on 2007-02-13
I cant believe it, a problem I have spent a month trying to fix you have solved in 5 minutes :p

For reference though, why does that driver work as apposed to the ATi one, I would have imagined I should use the ATi one as it is an ATi card...

Thanks, Rob

---

### Post by taurus on 2007-02-13
Vesa is a generic driver so it should work for almost every graphic card out there.  Did you use ATi or did you use ati in your previous /etc/X11/xorg.conf?

---

### Post by robcarr2 on 2007-02-13
As far as I know I used the ATI drivers, but last time I didnt manually configure it like this time as I didnt get an error. The only problem is I am getting really choppy performance at the moment, do you have any suggestions?

Edit: I mean **really** choppy, when I scroll down in this thread it takes ages and doesnt scroll smoothly at all.

---

### Post by taurus on 2007-02-13
Maybe this helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by robcarr2 on 2007-02-13
I had thought of updating the ATI driver, but if I am using the vesa driver will it make a difference? And if it sets my default driver back to ATI wont I continue getting the error I was previously getting?


Edit: I installed the latest new legacy driver and it seems to have fixed the problem! Thanks again for all the help :)

---

