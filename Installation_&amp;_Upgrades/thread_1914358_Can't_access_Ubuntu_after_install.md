---
title: "Can't access Ubuntu after install?"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by Funkymintbro on 2012-01-24
I used that Windows installer of Ubuntu so you could uninstall Ubuntu like any other windows app, BUT, on the Ubuntu website it showed that I should be able to see a boot loader on boot-up after I've installed Ubuntu. There is no boot-loader...Is there some way of accessing it?

---

### Post by bogan on 2012-01-24
Hi!, **funkymintbr**o,

Try holding down, or repeatedly pressing the Shift key, during the boot.

 It should show the Grub menu, with Boot options to select.

Chao!,** bogan**.

---

### Post by darkod on 2012-01-24
> **bogan said:**
> Hi!, **funkymintbr**o,

Try holding down, or repeatedly pressing the Shift key, during the boot.

 It should show the Grub menu, with Boot options to select.

Chao!,** bogan**.

That is used when using grub2 on the MBR, not with a wubi install inside windows.

It seems the entry for ubuntu was not added in the windows bootloader, don't know why. I don't use wubi myself and know little about it.

Using a proper dual boot is a better option. If you want to, you can get rid of it easy also, if that's the reason you decided to install wubi.

---

### Post by bogan on 2012-01-24
Hi!, **darkod**.

Thanks for the correction; I don't use Wubi either, and clearly, I know  even less about it than you do.

Chao!,  o HASTA LA PROXIMA, **bogan**

---

### Post by bcbc on 2012-01-24
Right click on Computer, Properties, Advanced system settings, Startup & recovery settings.

Make sure the timeout is 10 and there is an entry in the default os drop down box (don't set the default to Ubuntu).

For XP, it's similar, right click on My Computer, properties, advanced tab, startup & recovery settings.

---

### Post by Funkymintbro on 2012-01-25
Omg, I feel kinda stupid right now. All I had to do is press F8 on boot-up...

Sorry about that, rookie mistake.

---

### Post by bcbc on 2012-01-25
> **Funkymintbro said:**
> Omg, I feel kinda stupid right now. All I had to do is press F8 on boot-up...

Sorry about that, rookie mistake.

You shouldn't have to press F8. Probably the timeout is set 0. It should prompt you ever time you boot. I'd recommend setting it to a minimum of 10 (because some people have had problems if they set the default to Ubuntu with a timeout less than that; they can no longer boot windows).

---

