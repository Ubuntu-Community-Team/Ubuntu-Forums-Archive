---
title: "Can't start the Graphical Mode"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by Cornellius on 2005-06-19
Ok, so Ubuntu installed itself well, but now it stop where the graphical environnement is supposed to start and it tells me that it will start in text mode.

What can I do ?

---

### Post by Xian on 2005-06-19
Is there a small error box that offers the option of providing details about why it is going into 'text mode'? In short, more details if available would be helpful.

---

### Post by Cornellius on 2005-06-19
Yes, it's that box you're talking about. I read an earlier post in here and someone said he had to configure XORG to accept his Monitor. I tried to look on google but I don't find a lot of info.

I have a : Sony Multiscan E210

Thanks

---

### Post by Xian on 2005-06-19
You might want to try and do this in a more friendly way by logging in with your username at the command prompt and entering this command:

```
 $ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Cornellius on 2005-06-19
And what do I need to change ?
I begin with Linux and I've been told that UBUNTU was a good place to start.

---

### Post by Cornellius on 2005-06-19
Oh, I see. I looked at the XORG log and it seems that it's a problem with GLIDE. I have an ASUS GeForce FX 5200 128 Megs. Well, Ubuntu found that it was a GLIDE card (even if it say OPEN-GL on the box of the graphic card), but Ubuntu seems to be unable to find the drivers for it.

I KNOW I have to install GLIDE somehow, I just dunno how.

---

