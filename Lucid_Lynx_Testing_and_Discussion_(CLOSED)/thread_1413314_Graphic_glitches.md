---
title: "Graphic glitches"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cutler on 2010-02-22
Hello guys, I recently decided to give a try to new Ubuntu 10.04. Unfortunately I have a problem with my graphics as everything is messed up:-) take a look on the screen attached. It might be something with   the drivers, I have radeon X1200 and it is working ok only when using vesa driver. For the ati,radeon or radeonhd it's very bad. With 9.10 everything worked perfectly Thx.

---

### Post by diebels on 2010-02-22
How about fglrx?

---

### Post by Cutler on 2010-02-22
Well from what I know X1200 is not supported by fglrx anymore. I have this one.
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

---

### Post by diebels on 2010-02-22
You're probaly right.  Just saw the list of supported cards in recent fglrx releases, it's shockingly small :-)

I've seen similiar graphics corruption on intel cards several months ago when modesetting wasn't working properly.

You could try adding nomodeset to the kernel command line.  Assuming you have grub2, hold shift while booting up and press 'e' to edit the command line.

---

### Post by Cutler on 2010-02-22
Yep disabling kernel modesetting did the trick:-) . Thx a lot.

---

### Post by mattisking on 2010-02-22
Thanks for that bit of info. I have far less glitches than you but it's quite noticably bad comparably to before the upgrade. I'll try it as soon as I get home.

---

### Post by ranch hand on 2010-02-22
You may want to try the xorg.edgers ppa.  My Radeon HD2400 Pro seems to like their stuff real well.

---

### Post by Philip550c on 2010-02-27
> **ranch hand said:**
> You may want to try the xorg.edgers ppa.  My Radeon HD2400 Pro seems to like their stuff real well.

What's that?

---

### Post by Kazade on 2010-02-27
> **Cutler said:**
> Yep disabling kernel modesetting did the trick:-) . Thx a lot.

It's probably worth reporting this on launchpad with the screenshots. It could prevent a bunch of other people hitting it when 10.04 comes out.

---

### Post by Cutler on 2010-03-02
Ok, I'll do it.

---

