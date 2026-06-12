---
title: "just done an update. it's bust."
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by andyni on 2008-08-27
Last night i allowed 3 updates to be applied. I think the name of the first was of the form "linux (something) headers (version number)." and I think the other two followed on logically. Complacent I know, but I've just about started to trust Ubuntu, so I barely even read the list.

now it takes over 3 times as long to boot, 4 minutes to open firefox, and I can ALWAYS type faster than characters appear on the screen, even when I'm eating with one hand.

What on earth were the last 3 updates, and how do I get shot of them?

I've read in the forum that there's no way of undoing the last update through update manager.

I've also read it's possible to save package state with synaptic before doing an upgrade (please tell me how so that I can prevent this happening again).

Is there a way of finding packages by the date they were installed so that I can remove the last 3?

Did they replace any previous versions of linux-headers, that I will need to put back, and if so what are they?

---

### Post by Partyboi2 on 2008-08-27
>  Is there a way of finding packages by the date they were installed so that I can remove the last 3?You can open up synaptic and go to File>History Then you can view the history of apt.

> I've also read it's possible to save package state with synaptic before doing an upgrade (please tell me how so that I can prevent this happening again).
You  could use the "Save markings as.." feature in synaptic (File>Save Markings as..), making sure you select "Save full state, not only changes"

---

### Post by irishbreakfast on 2008-08-27
Yes, I installed those updates and have now lost my wireless. 

I too would like to get rid of them!!

---

### Post by Pumalite on 2008-08-27
> **andyni said:**
> Last night i allowed 3 updates to be applied. I think the name of the first was of the form "linux (something) headers (version number)." and I think the other two followed on logically. Complacent I know, but I've just about started to trust Ubuntu, so I barely even read the list.

now it takes over 3 times as long to boot, 4 minutes to open firefox, and I can ALWAYS type faster than characters appear on the screen, even when I'm eating with one hand.

What on earth were the last 3 updates, and how do I get shot of them?

I've read in the forum that there's no way of undoing the last update through update manager.

I've also read it's possible to save package state with synaptic before doing an upgrade (please tell me how so that I can prevent this happening again).

Is there a way of finding packages by the date they were installed so that I can remove the last 3?

Did they replace any previous versions of linux-headers, that I will need to put back, and if so what are they?

Nothing is replaced. You can boot with previous kernel.
This might be worth reading:
[http://ubuntuforums.org/showthread.php?t=601485](http://ubuntuforums.org/showthread.php?t=601485)

---

### Post by de0xyrib0se on 2008-08-27
Yeah things like this happen with Ubuntu every so often, a few months ago an update to X got pushed that didnt play well with nVidia cards that caused my Gnome to bomb out.

I have to say QA has to somehow be improved.

---

### Post by andyni on 2008-08-30
I have discovered what the update manager did.
it upgraded

linux-headers-2.6.24-19 from 2.6.24-19.36 to  2.6.24-19.41
linux-headers-2.6.24-19-generic from 2.6.24-19.36 to  2.6.24-19.41
linux-image-2.6.24-19-generic from 2.6.24-19.36 to  2.6.24-19.41

how can this be undone?

synaptic won't allow me to force the version of these packages back. it seems only to know about 2.6.24-19.41.

I think i've booted into previous kernels successfully, but none of them perform well, proably because everything else installed on this laptop is geared to a late kernel.

---

### Post by gatenby_jp on 2008-08-30
You should on your boot menu have the previous version of the linux kernel ... simply boot with that and if everything is fine purge 2.6.24-19.36 or delete it from your grub startup menu

Apologies this only applies if you have upgraded from an earlier distro

---

### Post by andyni on 2008-09-01
As I said in my previous post, booting to one of the previous kernels in the grub menu does not improve performance. 

I got as far as thinking about a complete reinstall, then I remembered that the CD drive in the laptop is broken, so I'd really like to know if possible where to download the 2.6.24-19.36 of the packages if possible.

---

