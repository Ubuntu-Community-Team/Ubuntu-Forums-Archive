---
title: "upgrade from 7.04 to 8.04 and keeping the kernel"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by ikal on 2008-02-06
hi

as i had problems with the gutsy kernel, acpi and my laptop's bios (i have the infamous hp compaq nx6325), i'm running feisty (no problems) and wanna upgrade to hardy when it comes out and skip gutsy.

however, i'd like to keep my kernel as it seems that later versions don't work correctly with my laptop's bios and acpi doesn't work. i've removed the kernel meta package, so it shouldn't upgrade to the latest version.

now, my question is whether i'll be able to run hardy with the old kernel or will other packages force me (i do have the ubuntu-desktop meta package installed for upgrading) to move to the new kernel?

i know, hardy will not be out until april... i'm just wondering what to expect as i can't really afford (timewise) tinkering with my system for days if the upgrade doesn't work. thanks in advance for the feedback!

---

### Post by zvacet on 2008-02-06
> and wanna upgrade to hardy when it comes out and skip gutsy

You can not do that.You will have to reinstall if you want Hardy because upgrades goes like this** Feisty>Gutsy>Hardy**.I don´t understand why you want Hardy now when it is still work in progress.It will be stable in april.And yes I think you can boot old kernel,but why you wanna do that when you have good working OS.

---

### Post by ikal on 2008-02-06
> **zvacet said:**
> You can not do that.You will have to reinstall if you want Hardy because upgrades goes like this** Feisty>Gutsy>Hardy**.I don´t understand why you want Hardy now when it is still work in progress.It will be stable in april.And yes I think you can boot old kernel,but why you wanna do that when you have good working OS.

thanks for reading my post. i don't want to upgrade yet,  just wondering what to expect.

as far as i know, i should be able to skip releases. hence the 18 months (or more, in case of lts releases) support cycle. i'm just not sure if i kan ceep the kernel from feisty.

---

### Post by zvacet on 2008-02-06
> as far as i know, i should be able to skip releases. hence the 18 months (or more, in case of lts releases) support cycle.

Support cycle has nothing with upgrades.It just mean that you will get security updates during 18 (or 3-5 years if it is LTS)months.If you want to upgrade you have to do it like I told you.One step in time.Maybe something is changed and I´m nor aware of that.If that is the case I would like to know.

---

### Post by ikal on 2008-02-06
> **zvacet said:**
> Support cycle has nothing with upgrades.It just mean that you will get security updates during 18 (or 3-5 years if it is LTS)months.If you want to upgrade you have to do it like I told you.One step in time.Maybe something is changed and I´m nor aware of that.If that is the case I would like to know.

well, it was a logical assumption on my side. i thought that the ubuntu-desktop package is the allmighty metapackage that will move me to the latest release, wherever i start... i could be wrong.

but the question is whether i can use feisty's kernel under hardy :)
i would love to use my laptop for another 3-5 years without upgrading.

---

### Post by zvacet on 2008-02-07
Why didn´t you use Feisty kernel in Gutsy?Upgrade to Gutsy didn´t erase your previous kernel,so you should be able to boot from older kernel.Run this

```
sudo gedit /boot/grub/menu.lst
```

and see if you have this lines in it

## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

If you have this lines that means you will keep your old kernel after upgrade and you can select it to boot from it.Right now you can upgrade to Gutsy and you will have your Feisty kernel and be able to boot from it if you want to.

---

