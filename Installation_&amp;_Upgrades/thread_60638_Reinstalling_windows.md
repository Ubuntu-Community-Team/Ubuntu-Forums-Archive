---
title: "Reinstalling windows"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by Abild on 2005-08-28
Hi all,

I'm sitting here with a totally screwed winblows installation which needs reinstalling. 

If it weren't for a couple of games that doesn't work with cedega i'd be able to get rid of winblows permanently :(

I suppose the winblows installer will replace gurb with it's own bootloader. So if i should be able to access both winblows and Ubuntu i'll need to get gurb back on the bootsector.

So my question is what the best way to this is?

Thanks in advice :)

---

### Post by ekravche on 2005-08-28
Is your windows partition and linux partion on seperate drives?

---

### Post by Abild on 2005-08-29
Yes they are,,,

---

### Post by grim42 on 2005-08-29
[QUOTE=Abild]Yes they are,,,[/QUOTE]
 Best is probably to unplug Linux hard drive while installing Windows. Then reconnect it as Primary Master and First Boot Device.

You shouldn't need to change any settings if Grub is already able to boot Windows.

EDIT: Don't do this if you're not comfortable with unplugging stuff inside your case.

---

### Post by Abild on 2005-08-29
I'm pretty much into hardware/overclocking/casemodding so being inside my case doesn't border me at all :)

I'll try unplugging my linux drive...
Thanks for your reply

---

