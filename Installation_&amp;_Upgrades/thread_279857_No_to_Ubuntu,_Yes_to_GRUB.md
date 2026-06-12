---
title: "No to Ubuntu, Yes to GRUB"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by Shockz on 2006-10-18
Okay, my request has two parts.

Firstly, I've sadly decided that Ubuntu isn't for me. I could go into the myriad reasons why this is the case, but I'll spare you the time. So I need to get rid of it, but I can't find a way to do so. (If it requires a Windows setup disk, I unfortunately lack an XP one, but I do have a Vista RC1 disk--will that work?)

Secondly, though I don't like Ubuntu, I do like the simplicity of the GRUB interface, and I was wondering if I could keep it after getting rid of Ubuntu in order to simplify the process of dual-booting Windows XP and Vista.

Thanks!

---

### Post by Crooksey on 2006-10-18
No, because you need to have a small boot partition with grub on etc, why not a 600MB one, with a base ubuntu install?

---

### Post by K.Mandla on 2006-10-18
Sorry to hear Ubuntu wasn't for you. All the same, thanks for checking it out.

> **Shockz said:**
> So I need to get rid of it, but I can't find a way to do so. (If it requires a Windows setup disk, I unfortunately lack an XP one, but I do have a Vista RC1 disk--will that work?)
I ... think so, but then you're installing Vista, not XP. Does it matter to you which one you use?

If you're keen on blanking the hard drive altogether (which I would recommend, if you're going to a dual XP/Vista system), try [Killdisk]("http://www.killdisk.com"). After that, you'll need the Windows installation disc of your choice. Just boot to it, and the rest is up to you.

> **Shockz said:**
> Secondly, though I don't like Ubuntu, I do like the simplicity of the GRUB interface, and I was wondering if I could keep it after getting rid of Ubuntu in order to simplify the process of dual-booting Windows XP and Vista.
I've never heard of anyone doing that, but I don't see why it couldn't be done. You'll have to scratch around for tips on installing Grub overtop those two systems. Unless I'm mistaken, you'll have to install one but leave space for the other, reboot, install the other, then work out the mysteries of Grub. 

Have fun! ;)

---

### Post by bulldog on 2006-10-18
> **K.Mandla said:**
> Sorry to hear Ubuntu wasn't for you. All the same, thanks for checking it out.


I ... think so, but then you're installing Vista, not XP. Does it matter to you which one you use?

If you're keen on blanking the hard drive altogether (which I would recommend, if you're going to a dual XP/Vista system), try [Killdisk]("http://www.killdisk.com"). After that, you'll need the Windows installation disc of your choice. Just boot to it, and the rest is up to you.


I've never heard of anyone doing that, but I don't see why it couldn't be done. You'll have to scratch around for tips on installing Grub overtop those two systems. Unless I'm mistaken, you'll have to install one but leave space for the other, reboot, install the other, then work out the mysteries of Grub. 

Have fun! ;)

If the two windows are installed you could simply install Grub from the live cd.

But I'm not so sure if Vista will boot from Grub,you have to investigate on that one.
There are some threads over it if I'm not mistaken on the Ubuntu forums.

To reinstall GRUB from the live cd do the following,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by K.Mandla on 2006-10-18
Just for my own edification, does there need to be a special partition for that /boot/grub/menu.lst, or does it stash it anywhere?

---

### Post by bulldog on 2006-10-18
Well it's needed to boot so it should be somewhere :D 

I don't know however if you can place it anywhere and redirect grub to it.
Never tried such a thing so can't give a reliable answer.

---

### Post by gn2 on 2006-10-18
> **Shockz said:**
> Okay, my request has two parts.

Firstly, I've sadly decided that Ubuntu isn't for me. I could go into the myriad reasons why this is the case, but I'll spare you the time. So I need to get rid of it, but I can't find a way to do so. (If it requires a Windows setup disk, I unfortunately lack an XP one, but I do have a Vista RC1 disk--will that work?)

Secondly, though I don't like Ubuntu, I do like the simplicity of the GRUB interface, and I was wondering if I could keep it after getting rid of Ubuntu in order to simplify the process of dual-booting Windows XP and Vista.

Thanks!

Just delete the Ubuntu partition and it will be very gone indeed.

You can use Super Grub Disc for all your booting needs.
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

I have read elsewhere that fixmbr can be run from any windows boot floppy..

---

