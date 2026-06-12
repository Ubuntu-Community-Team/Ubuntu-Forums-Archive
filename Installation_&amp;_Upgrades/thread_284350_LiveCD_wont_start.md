---
title: "LiveCD wont start"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by hk_2999 on 2006-10-25
I've downloaded the 64bit version of the Edgy Eft RC LiveCD, and after burning it to a cd and rebooting my computer, selecting the install and run option just put a Loading... text on the upperleft portion of my screen and after waiting for a short time, it just stayed there and it doesnt seem to want to boot.

So I rebooted and thought I could ask you guys what could be wrong? P.S. This is the second CD I burned it to.

---

### Post by x64Jimbo on 2006-10-25
Did you check the iso file's MD5sum before you burned it? Did you try burning at low speed?

---

### Post by Kateikyoushi on 2006-10-25
Could try safe video mode just in case or to boot with these options.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by hk_2999 on 2006-10-25
Thanks x64jimbo.

I tried burning the thing at 24x and the cd now worked like a charm. :D

---

### Post by x64Jimbo on 2006-10-25
Yeah, who knows why those CDs say they can burn at 48x but need to be burned at half that to avoid errors? I think they should only advertise their non-error rate, but hey, that's just me.

---

### Post by Kateikyoushi on 2006-10-25
> **hk_2999 said:**
> Thanks x64jimbo.

I tried burning the thing at 24x and the cd now worked like a charm. :D

Did you try to check the cd at the boot menu ?

---

### Post by x64Jimbo on 2006-10-25
Yeah, that's a good way to know for sure if you have a bad burn. It checksums the whole CD, then compares it against the stored checksum for that disc. This method's been around for a while, but it sure works great!

---

### Post by hk_2999 on 2006-10-25
> **x64Jimbo said:**
> Yeah, that's a good way to know for sure if you have a bad burn. It checksums the whole CD, then compares it against the stored checksum for that disc. This method's been around for a while, but it sure works great!

Actually, my 2 bad disks stopped functioning ( with the loading... text again ) when I select Check CD for errors. ;)

---

