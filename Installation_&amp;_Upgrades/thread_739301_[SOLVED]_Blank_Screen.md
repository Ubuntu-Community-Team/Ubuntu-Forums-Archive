---
title: "[SOLVED] Blank Screen"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by goohman on 2008-03-29
I put in the live cd and selected install or start ubuntu but i got an IO-APIC error or something like that and it says boot with "apic=debug" and send log then boot with "noapic"

the debug didnt work i got the same error. so i did noapic and it worked but after the black bar turned all orange my monitor says "cannot display this video mode" but i was confused because the ubuntu install cd uses 800*600 or 1024*768 to install and I use 1024*768 in windows with no problem.

I reboot and try to install using safe graphics same result for both what can I do to get to install ubuntu?

---

### Post by JafaarNhh on 2008-03-29
Hi

My advice is to choose OEM manufacturing its more easy.
:)

---

### Post by LunatikOwl on 2008-03-29
Try to download the text-based install CD and after the install run 
```

sudo dpkg-reconfigure xserver-xorg

```
If you're new to linux you might want so google some guide/howto about installing ubuntu in text based.

Just my two cents...

---

### Post by goohman on 2008-03-29
Im downloading the x86 and the 64bit alt. images as i type hopefully install wont fail after I wipe my hd (im starting all over btw):wink::guitar:

---

### Post by goohman on 2008-03-29
ok, so i got ubuntu to install but now when I choose it to boot in grub the loader loads and then my screen goes blank then it says "cannot display this video mode" when i chose 1024*768 on the xserver(i think thats what it says) display mode.

Can someone help me?

---

### Post by goohman on 2008-03-29
this is [MY MOBO]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131183")<--clickable

---

