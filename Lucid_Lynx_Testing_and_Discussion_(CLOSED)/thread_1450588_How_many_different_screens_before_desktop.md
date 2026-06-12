---
title: "How many different screens before desktop?"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2010-04-09
I would like to know how many different screens should be displayed before reaching the desktop and what is each one?

Currently I have this order:

1 - All the BIOS screens
2 - Grub
3 - Monitor goes dark like when turned off
4 - Black screen with a blinking cursor on the top-left corner
5 - Monitor goes dark like when turned off
6 - The purple splash screen with Ubuntu logo, which I suspect is Plymouth
7 - Flicker once, displaying distorted green/purple bands ( I guess nvidia kicking in)
8 - Black screen with a blinking cursor on the top-left corner
9 - KDM

Just for comparison, Windows 7 goes like this:

1 - All the BIOS screens
2 - Grub
3 - Starting Windows
4 - Monitor goes dark like when turned off
5 - Black screen with a blinking cursor on the top-left corner
6 - Monitor goes dark like when turned off
7 - Login

---

### Post by Chromagnum on 2010-04-09
I have almost excatly like yours. I guess we both don't use GDM (automatically login)

1 - All the BIOS screens
2 - Grub
3 - Monitor goes dark like when turned off
4 - Black screen with a blinking cursor on the top-left corner
5 - Monitor goes dark like when turned off
6 - The purple splash screen with Ubuntu logo, which I suspect is Plymouth (and there were some text at the bottom of the ubuntu logo blinking)
7 - Flicker once, displaying distorted green/purple bands (also nvidia - fx 5500)
8 - Black screen with a blinking cursor on the top-left corner
9 - Gnome

---

### Post by lovinglinux on 2010-04-09
> **Chromagnum said:**
> I have almost excatly like yours. I guess we both don't use GDM (automatically login)

1 - All the BIOS screens
2 - Grub
3 - Monitor goes dark like when turned off
4 - Black screen with a blinking cursor on the top-left corner
5 - Monitor goes dark like when turned off
6 - The purple splash screen with Ubuntu logo, which I suspect is Plymouth (and there were some text at the bottom of the ubuntu logo blinking)
7 - Flicker once, displaying distorted green/purple bands (also nvidia - fx 5500)
8 - Black screen with a blinking cursor on the top-left corner
9 - Gnome

I don't use automatic login, I use KDM.

I usually get some text below the Ubuntu logo, but it's too fast to read it. Additionally, the size of the text is kind of big and alignment is pretty much screwed.

---

### Post by Chromagnum on 2010-04-09
> **lovinglinux said:**
> I don't use automatic login, I use KDM.

I usually get some text below the Ubuntu logo, but it's too fast to read it. Additionally, the size of the text is kind of big and alignment is pretty much screwed.

Yeah, I guess how big the text are depends on the plymouth resolution. I suppose it is 640x480. If you use Nouveau (deactivating jockey) and boot to terminal, it is so pretty. I'm in the middle of updating, and I noticed the Unable to load x server display page is fix. I can now see X server display configuration. 

Hope is fix the plymouth on booting - not finish updating yet. (fingers cross)

---

### Post by lovinglinux on 2010-04-09
> **Chromagnum said:**
> Yeah, I guess how big the text are depends on the plymouth resolution. I suppose it is 640x480. If you use Nouveau (deactivating jockey) and boot to terminal, it is so pretty. I'm in the middle of updating, and I noticed the Unable to load x server display page is fix. I can now see X server display configuration. 

Hope is fix the plymouth on booting - not finish updating yet. (fingers cross)

I did an update a couple of hours ago and it didn't change anything.

---

### Post by Chromagnum on 2010-04-09
> **lovinglinux said:**
> I did an update a couple of hours ago and it didn't change anything.

Yeap, just reeboted and you were right. It didn't change anything. At least now I can see X server display configuration. Perhaps when official LTS release it wouldn't be a problem anymore. Hope so.

Oh I forgot - the boot order screens, still the same.

---

