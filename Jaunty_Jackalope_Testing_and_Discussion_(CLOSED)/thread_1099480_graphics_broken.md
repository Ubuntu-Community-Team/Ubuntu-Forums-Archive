---
title: "graphics broken"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-03-18
I didn't really pay attention to what was being updated today - but it broke my graphics (probably fglrx-amdcccle or xserver-...).
Graphics card is an Ati Radeon mobility X700.

When I boot now the screen gets messed up before making it to the login screen.


ctrl + alt + backspace isn't working (it is enabled),
ctrl + alt + F# also isn't working.

I think I will try to boot with an USB stick and install the latest updates through chroot in a few days - or how would you go about it?

---

### Post by Jack Monaghan on 2009-03-18
this is what i did to make mine work
as it boots up and gets to grub hit esc then boot the recovery kernel which will give you a menu, scroll down to netboot and hit return then type in you user name  and password at the prompts after you are logged in type "apt-get remove xorg-driver-fglrx" when that is done type reboot this will give you a working computer just without the fancy 3d screens 
after they fix the driver you can install it with adapt or equivalent

Jack

---

### Post by excogitation on 2009-03-18
removing fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx fixed the login screen for me too.

I'm surprised that now Compiz is working without the fglrx driver.

---

### Post by Woody1987 on 2009-03-19
all future fglrx drivers wont support cards older than the 2000 series, for cards older than that i.e. x700 or x1600 the opensource radeonhd drivers work fine and give good performance.

---

### Post by excogitation on 2009-03-19
> **Woody1987 said:**
> all future fglrx drivers wont support cards older than the 2000 series, for cards older than that i.e. x700 or x1600 the opensource radeonhd drivers work fine and give good performance.

Afaik the X700 first appeared 2004, so it should be supported by the Ati proprietary drivers ... if not I will not get an Ati card in my next laptop (I was actually thinking about getting an Asus V2S sometime soon -> nVIDIA).

---

### Post by Woody1987 on 2009-03-19
> Afaik the X700 first appeared 2004, so it should be supported by the Ati proprietary drivers ... if not I will not get an Ati card in my next laptop (I was actually thinking about getting an Asus V2S sometime soon -> nVIDIA).

Afraid it is no longer supported on either windows or linux from 9.3 onwards.

---

### Post by brunolabs on 2009-04-07
I have a similar problem (also with an ATI X700). After those updates, video playback is pixelated. I had this problem before and I solved it with this command:

```
sudo aticonfig --ovt Xv
```

But now it doesn't work :( .
Can anyone help?

---

### Post by excogitation on 2009-04-07
Seems our card isn't supported anymore by the fglrx driver.

---

### Post by GF_Sobriquet on 2009-04-07
Thank you! I had this problem on my MacBook Pro 1,1 and I was ready to reinstall!

---

### Post by SigmaSanti on 2009-04-07
I had similar issues, but my graphics card (Nvidia 8200) had problems before this.
I booted up and compiz blew up in my face. All the graphics looked like a ram dump and would not refresh. The mouse was unresponsive, I switched to terminal and then back and was able to disable compiz. 
Another weird problem is certain windows don't refresh and/or crash my graphics - emerald menu, firefox save/quit menu and the run script menu.

Also, did not the release notes say something about problems with certain ati cards?

---

