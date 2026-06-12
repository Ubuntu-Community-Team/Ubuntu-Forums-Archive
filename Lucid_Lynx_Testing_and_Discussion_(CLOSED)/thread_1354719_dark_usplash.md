---
title: "dark usplash"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-12-14
is there something wrong with usplash ?
Its so dark i can not tell what it is.
any way to make it brighter ?

---

### Post by jpeddicord on 2009-12-14
You shouldn't be able to; usplash has been removed from boot.

---

### Post by ranch hand on 2009-12-14
I have a "ghost" of usplash on 2 of my 4 installs.  It was 3 but installing plymouth cured that for 1.

With todays update of plymouth it even works great.  Seems faster boot up but I don't have bootchart on that one and am not sure.

---

### Post by jpeddicord on 2009-12-14
> **ranch hand said:**
> I have a "ghost" of usplash on 2 of my 4 installs.  It was 3 but installing plymouth cured that for 1.

With todays update of plymouth it even works great.  Seems faster boot up but I don't have bootchart on that one and am not sure.

That's funky. So you can still see a faint image of usplash? Do you have any usplash-related packages installed? Attempting to install anything related here causes a conflict with gdm.

---

### Post by ranch hand on 2009-12-14
Don't seem too.  It is strange but doesn't seem to hurt anything.  I had the update that removed usplash and I use synaptic with the details output in terminal so I know everything went well.

If, after this kernel and xorg update today, this goes on I will be installing plymouth on all of my installs.  I bet that cures it.

---

### Post by MacUntu on 2009-12-14
I had this too. :)

---

### Post by cariboo on 2009-12-14
I saw the same thing a couple of days ago, right after usplash was removed.

---

### Post by philinux on 2009-12-14
> **ranch hand said:**
> I have a "ghost" of usplash on 2 of my 4 installs.  It was 3 but installing plymouth cured that for 1.

With todays update of plymouth it even works great.  Seems faster boot up but I don't have bootchart on that one and am not sure.

All I get with Plymouth is a few error messages and a black screen before xsplash kicks in. :(

And the boot time gone up to 53 seconds.

---

### Post by Gina on 2009-12-14
I too have seen the ghost of usplash - do you think we're psychic?? :lolflag:

---

### Post by MacUntu on 2009-12-14
Collective hallucination. :D

---

### Post by philinux on 2009-12-14
It might be Casper :P

---

### Post by jpeddicord on 2009-12-14
To those who still have the ghost splash, give this a try:

```
sudo update-initramfs -u -k all
```

I'm wondering if bits of usplash were left over in initramfs and simply haven't been removed yet. This will happen automatically with the next kernel update, but I'm personally just curious if that's what it was. :P

---

### Post by autocrosser on 2009-12-14
Karmic Lynx????   :D:D

---

### Post by Gina on 2009-12-14
Well I don't think it's a Lucid Koala :D:D

---

### Post by VMC on 2009-12-14
> **autocrosser said:**
> Karmic Lynx????   :D:D

More like Karmic Jinx :>

---

### Post by cecilpierce on 2009-12-14
i installed plymouth, it took usplash out but now i just see a few line of text for a few seconds and then gdm. what do ya have to do to get plymouth to work ?

---

### Post by Reiger on 2009-12-14
You must have Kernel Mode Setting on. 

And for me the choice is KMS or a functional X... though I do get pink letters on black background with KMS. Decisions...

---

### Post by darco on 2009-12-15
> **jpeddicord said:**
> To those who still have the ghost splash, give this a try:

```
sudo update-initramfs -u -k all
```

I'm wondering if bits of usplash were left over in initramfs and simply haven't been removed yet. This will happen automatically with the next kernel update, but I'm personally just curious if that's what it was. :P

I just did a pretty large update since I hadnt done one in quite awhile. Updated the kernel as well. I still see the greyed out ubuntu guitar pick (thats what it looks like to me).
Ran the above command, still there.

Other than reinstalling my nvdia driver, no breakage!

darco

---

