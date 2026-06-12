---
title: "Lucid Alpha 3 - NVIDIA"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Couto on 2010-02-28
I'm having troubles with installing my NVIDIA drivers on Alpha 3 I have no idea what is wrong?

I tried to do it the Alpha 2 way (sudo apt-get install nvidia-current)
Doesn't work on here, is the Hardware Drivers working fine for everyone else?

Thanks.

---

### Post by Couto on 2010-02-28
Bump - Got pushed really far and it's kinda like a big deal :P

---

### Post by exploder on 2010-02-28
Hardware Drivers work here with NVIDEA but it causes a double log on issue and changing resolution on boot. At the moment, the open source driver is working better for me aside from no desktop effects.

---

### Post by Couto on 2010-02-28
> **exploder said:**
> Hardware Drivers work here with NVIDEA but it causes a double log on issue and changing resolution on boot. At the moment, the open source driver is working better for me aside from no desktop effects.

My problem is my computers too loud, I don't care for desktop effects anyways. :)
I don't understand this Open Source NVIDIA stuff, is it what is preactivated with Alpha 3? If so it may run nicely but my PC is just too loud without proper drivers. I suppose I'll stick to Arch for the time being.

---

### Post by exploder on 2010-02-28
You might be better off with the open source driver for the time being.

---

### Post by Couto on 2010-02-28
> **exploder said:**
> You might be better off with the open source driver for the time being.

Is this preactivated?

---

### Post by phenest on 2010-02-28
> **Couto said:**
> My problem is my computers too loud, I don't care for desktop effects anyways. :)
I don't understand this Open Source NVIDIA stuff, is it what is preactivated with Alpha 3? If so it may run nicely but my PC is just too loud without proper drivers. I suppose I'll stick to Arch for the time being.

"Too Loud"? What do you mean? Audio? You've lost me there.

---

### Post by Couto on 2010-02-28
> **phenest said:**
> "Too Loud"? What do you mean? Audio? You've lost me there.

The fan overdoes itself without the proper drivers.

---

### Post by phenest on 2010-02-28
> **Couto said:**
> Is this preactivated?

Yes, they are. You should be able to install the official nVidia driver using the Hardware Drivers applet. Ignore the error at the end of installing as it's a bug. Restart, and you're away. But I do recommend using the nVidia settings app to create a xorg.conf file, as it makes a better job of it than Xorg.

---

### Post by cariboo on 2010-02-28
I'm running alpha 3 on two different systems, one with an Nividia GT210 and the other with 8400GS, at the moment I'm using the restricted drivers on both systems. I installed the drivers using jockey-gtk (System->Administration->Hardware Drivers) on both systems, I dropped to a console (Ctrl-Alt-F1) and ran:

```
sudo nvidia-xconfig
```

The above command creates a new /etc/X11/xorg.conf, then I rebooted.

Just as an side, I plan on trying out the nouveau drivers a little later on today.

---

### Post by phenest on 2010-02-28
> **cariboo907 said:**
> I'm running alpha 3 on two different systems, one with an Nividia GT210 and the other with 8400GS, at the moment I'm using the restricted drivers on both systems. I installed the drivers using jockey-gtk (System->Administration->Hardware Drivers) on both systems, I dropped to a console (Ctrl-Alt-F1) and ran:

```
sudo nvidia-xconfig
```

The above command creates a new /etc/X11/xorg.conf, then I rebooted.

Just as an side, I plan on trying out the nouveau drivers a little later on today.

What he said, but I have a GeForce 7950GTX.

---

