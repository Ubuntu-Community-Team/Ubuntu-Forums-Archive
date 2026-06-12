---
title: "Kernel updates w/ instances on boot loader"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Harman Smith on 2006-07-04
I just installed Ubuntu today on my Presario 2500 after a couple days of fiddling with the Live CD. While *successfully* attempting to get my wireless card working, I let some 95 updates run. One was apparently the kernel, and now when I boot grub gives me a plethora of options. The one I chose is the (please excuse the inexact memory, I do not want to reboot to write down the numbers) 2.6.15.25(I believe it is .25) instance and then there is still the safe mode, but also a 2.6.15.23(once again the actual version isn't essential to my need) and it's recovery mode, another option I have no clue about, and my WinXP.

Basically I want to know if that older kernel is taking up space(my Ubuntu partition is <5gb), If I can get rid of it(why have it there if I'll never touch it), and if I did something incorrectly to make it show up after updating.

Any help for this Linux/Ubuntu newb would be appreciated:)

---

### Post by Henrythewound on 2006-07-04
I have a similar issue in which my GRUB boot screen becomes more and more cluttered with each ubuntu update. I have far too many kernels listed and they all seem similar. While I have a separate 40 gig HD for my ubuntu drive, I am annoyed by this clutter and would like to clean it up a bit. In the past I have edited my grub menu.lst file to exclude these kernels, but I am sure they are piling up on my computer memory nonetheless. Is there a way to get rid of old kernels? I dont know how much disk space they take up but I'm sure I dont need a Default, Default recovery mode, etc etc for the last 5 kernels I have used. Maybe Im wrong.

Thanks, Joe

---

### Post by John.Michael.Kane on 2006-07-04
Frist you have make sure the kernel you want to use on the machine is working with out errors. then under synaptic remove the un-needed kernels, and reboot the machine. after which if you want to check for residual kernel lines you can sudo gedit /boot/grub/menu.lst scroll to the bottom, and delete any lines that you don't need.

---

### Post by Henrythewound on 2006-07-04
thanks for the info, will try it out ASAP

Joe

---

### Post by Harman Smith on 2006-07-04
Worked great, thanks for the tip.

---

### Post by John.Michael.Kane on 2006-07-04
Harman Smith your welcome. gald it helped.

---

### Post by Henrythewound on 2006-07-05
Worked for me too, now my GRUB screen is much less cluttered, although I can't seem to get my choice for defaul OS boot working. I'm sure its some error I havent yet noticed in my edited menu.lst file. 

Thx,

-J

---

