---
title: "GRUB Boot menu overwritten"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by lagerratrobe on 2006-06-16
Quck complaint about the upgrade process.  I've used the upgrade tool on the Applications bar to upgrade from V. 5.10 to V. 6.06, and also to install upgrades when the system has notified me that they are available.  The fact that the utility exists is fantastic, HOWEVER...  In each case the upgrade has overwritten my /boot/grub/menu.lst.  The net effect of this is that I get 6 bazillion Ubuntu boot options, and the line for booting Windows has been deleted.

Can you please make it stop doing this?
--

---

### Post by chenel on 2006-06-16
[QUOTE=lagerratrobe]Quck complaint about the upgrade process.  I've used the upgrade tool on the Applications bar to upgrade from V. 5.10 to V. 6.06, and also to install upgrades when the system has notified me that they are available.  The fact that the utility exists is fantastic, HOWEVER...  In each case the upgrade has overwritten my /boot/grub/menu.lst.  The net effect of this is that I get 6 bazillion Ubuntu boot options, and the line for booting Windows has been deleted.

Can you please make it stop doing this?
--[/QUOTE]

I concur.  My monitor can't handle the default boot-screen resolution, so I have to go edit the menu.lst every time to put a vga=xxx line in, run update-grub, and reboot.  Silly.

---

### Post by jchau on 2006-06-16
[QUOTE=lagerratrobe]The net effect of this is that I get 6 bazillion Ubuntu boot options
...
Can you please make it stop doing this?
[/QUOTE]
Well, I'd rather have the many Ubuntu boot options.  In case the the new kernel doesn't work, I'd like to be able to easily fall back to a working one.

---

### Post by chenel on 2006-06-16
[QUOTE=lagerratrobe]Quck complaint about the upgrade process.  I've used the upgrade tool on the Applications bar to upgrade from V. 5.10 to V. 6.06, and also to install upgrades when the system has notified me that they are available.  The fact that the utility exists is fantastic, HOWEVER...  In each case the upgrade has overwritten my /boot/grub/menu.lst.  The net effect of this is that I get 6 bazillion Ubuntu boot options, and the line for booting Windows has been deleted.

Can you please make it stop doing this?
--[/QUOTE]

It just occurred to me though that you can fix that somewhat if you don't need all those old kernels by just uninstalling them through synaptic.  That will remove their entries from the menu.lst

-Jeremy

---

### Post by lagerratrobe on 2006-06-16
How about if the upgrade process just added to the menu.lst, not rewrote the whole thing?  That way all of the new kernels would be there, the entries for other OS's would remain, as would the custom VGA settings.  Isn't that known as an "incremental update"?

---

### Post by captain.kipper on 2007-04-16
Here Here ! :KS 

I am sure this would be a very simple bit of coding to fix. For anyone using a dual-boot system (and that must be thousands)  this is a very annoying issue. If you are a newbie this can be a daunting thing to negotiate, and many people migrating want to retain their windows OS. 

Please :) update-manager and/or synaptic devs - can you sort this out????

---

### Post by bulldog on 2007-04-16
Hmmm,rather old topic,don't you think?
But the windows entry in GRUB is VERY easily to obtain.
There's an example included in the menu.lst,so this shouldn't be too hard to do.

---

### Post by blamecanada on 2007-04-16
I always just go and comment out any entries in GRUB that are older kernels, otherwise I'd have 30 ubuntu entries by now.

---

### Post by bulldog on 2007-04-16
> **blamecanada said:**
> I always just go and comment out any entries in GRUB that are older kernels, otherwise I'd have 30 ubuntu entries by now.

You can uninstall them with synaptic,so you gain some free space back.
I should keep two working kernels,and remove the rest of them.

After that ```
sudo update-grub
``` and your menu.lst will be freshed up.

---

### Post by blamecanada on 2007-04-16
Thats a good idea, I didn't know you could do that, so I'll have to give that a try.

---

### Post by bulldog on 2007-04-16
Just look at the kernel you're using right now```
uname -a
```
Keep this one and the previous one and delete  the rest, search in synaptic for linux-image and select all the kernels you don't want to use anymore

---

