---
title: "New kernel used on 10.10 incompatible with Toshiba L675d. Will this be fixed?"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by ClaudeFleming on 2011-02-24
Hello,

I am desperately in love with Linux and love writing Java programs on it and compiling them at the terminal. I love the terminal and practically everything about Linux. But I simply cannot boot into the newest kernel with my new laptop. Do you think the next Ubuntu release will address the current problem of my not being able to use the newest Linux kernel? This is a fundamental problem and cannot be worked around. I have to use an earlier version of the operating system that will eventually not be supported. What's funny is this: my 5+ year-old Toshiba Satellite laptop works wonderfully with Linux and can even connect to my mom's wireless network "out of the box."

I guess it's hard to keep up with all the different hardware configurations on the market, and I can understand that you can't expect every computer to work with Linux. I was just wondering if anyone else has had similar problems. i am not using any custom-build PC. I think the problem is just that my laptop is too new and Linux developers haven't had time to catch up with the hardware manufacturers. 

Anyway, thanks for looking at my post. :P

---

### Post by dino99 on 2011-02-24
which kernel are talking about ?

you may try the latest available: 2.6.38-5 (rc6)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
install first both headers (choose either 32 or 64 bits depend on your actual system, but for developpement 64 is recommended) then the image

which are the errors when you fail to boot ? Might be a driver issue. Try booting by:
- removing: quiet splash
- adding either: nomodeset, noacpi, nolapic, noapic, irqpoll

you can google around searching about your tosh model+linux/ubuntu

---

### Post by ClaudeFleming on 2011-02-24
Thanks for the reply! Usually I'm ignored like the neighborhood homeless guy. 

Could you explain what you mean in more detail for each step you're talking about? I'm still new to Linux.

Thanks, even if you don't reply!

Claude

PS: I'm talking about the kernel that comes with the distro. How can I manually install a kernel. I thought only programs could do that.

---

### Post by ClaudeFleming on 2011-02-24
I just tried booting from the Live CD and I get the ISO Linux screen and the purple screen with the little man with his hands raised to the sky, but immediately after that I get a flashing underscore character with no options to do anything.

If I hold down shift while booting up, I am taken to the boot: prompt, but that quickly disappears and does what I just discussed in paragraph one.

How could I install kernels and load to them if I'm using the Live CD. Am I just out of luck?
How do I keep the boot prompt from disappearing before I have time to enter commands?

---

### Post by admiraljkb on 2011-03-19
I just installed the current daily build of Kubuntu Natty (2011-03-19)  and it works wonderfully out of the box on the L675D-S7052.   In fact  better out of box than any previous builds on any of the previous  machines I've installed on (mostly AMD chipset/graphics).   A true joy.  The 2.6.38  kernel has several AMD updates/fixes in it.  I normally don't recommend "dailies" for obvious reasons, but in this one instance for the L675D's...   It installed very nicely and everything "just works".   I'm not sure about the regular Gnome Ubuntu since that's got a lot more experimentation going on than the KDE edition this time around, so someone else might be able to chime in there if it works OK currently for daily usage on a L675D.

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

(BTW - I couldn't get 10.10 LiveCD to come up without disabling ACPI, and a laptop without ACPI is a big problem.)

---

