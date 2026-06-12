---
title: "How can I move where grub is loaded..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by zacinator on 2007-04-20
Here is my problem...
I wanted to try Kubuntu and I didn't see until after I did this that you can just install kubuntu-desktop...

I have Ubuntu installed on HDA1.  So I installed Kubuntu on HDB1.  

After playing around for a bit I decided I prefer GNOME and want to use HDB1 for music and photos.  I know I can just format it and do what i want with it.  

My problem is how do I tell MBR to load HDA1 (Ubuntu)'s grub and not HDB1 (Kubuntu)'s.  In theory since there will only be 1 OS i don't need it, but i don't want to mess up my ubuntu.

Thanks!

---

### Post by MetalMusicAddict on 2007-04-20
Running **sudo grub-reinstall** and pointing it to the correct partition should give control back to the installation you want.

---

### Post by zacinator on 2007-04-20
Thanks... I'll try that when I get home.

p.s. Ubuntu Studio looks sweet!:guitar:

---

### Post by zacinator on 2007-04-20
In case anyone else has this problem in the future...
sudo grub-reinstall  is not valid...  

I solved this by doing this:

[PHP]grub
> root (hd0,0)
> setup (hd0)[/PHP]

I feel smarter now (until my next screw up)!

---

