---
title: "Installation freezes near the end at package install.. please help me &gt;_&lt;"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by fujie on 2005-09-15
Hello,

I just bought a new mobo, cpu, ram, and video card.

Mobo: Asus A8N-SLI Premium (BIOS Version 1007)
CPU: AMD Athlon 64 3500
RAM: OCZ Dual Channel Kit 1 GB
Video Card: Gigabyte Nvidia Geforce 6600GT PCI-E 128 MB

My main problem is installing linux. I tried to install Ubuntu Hoary Hedgehog 5.04 and my system freezes upon setting up packages during the final stages of installation. The install gets past installing the base system and grub, reboots, then boots the kernel, and starts to setup packages then freezes. I tried installing Debian Sarge 3.1 and the exact same thing happens, my system freezes upon setting up the packages.

When I reboot after a "freeze", my system usually hangs on the Mobo/BIOS splash screen. I have to power down and then power on to get my system going again.

I had a working install of Windows XP at first, it seemed to work fine for a bit and then crapped out after trying the Debian install.

I am able to boot up with Knoppix just fine, everything seems to work with no freezes. I'm no expert, but my best guesses are:

1) Mobo problem? - either my mobo is too new for linux stock kernel support, OR a manufacturing defect
2) Hard drive issue??? - I'm using a Maxtor 40 GB (about 4 years old), again, I dunno...

Should I try another distro? I dunno, Ubuntu is my favourite and I would really like to get it working on my brand new system. Any help, suggestions, comments are greatly appreciated.  i have only until tomorrow to return my system.. i dont know if its the hardware or the software.

Many Thanks,

Fuji

PS: all my computer specs are at [http://img307.imageshack.us/my.php?image=help9sy.jpg](http://img307.imageshack.us/my.php?image=help9sy.jpg)

---

### Post by elpresidente on 2005-09-16
[QUOTE=fujie]Hello,

I just bought a new mobo, cpu, ram, and video card.

Mobo: Asus A8N-SLI Premium (BIOS Version 1007)
CPU: AMD Athlon 64 3500
RAM: OCZ Dual Channel Kit 1 GB
Video Card: Gigabyte Nvidia Geforce 6600GT PCI-E 128 MB

My main problem is installing linux. I tried to install Ubuntu Hoary Hedgehog 5.04 and my system freezes upon setting up packages during the final stages of installation. The install gets past installing the base system and grub, reboots, then boots the kernel, and starts to setup packages then freezes. I tried installing Debian Sarge 3.1 and the exact same thing happens, my system freezes upon setting up the packages.

When I reboot after a "freeze", my system usually hangs on the Mobo/BIOS splash screen. I have to power down and then power on to get my system going again.

I had a working install of Windows XP at first, it seemed to work fine for a bit and then crapped out after trying the Debian install.

I am able to boot up with Knoppix just fine, everything seems to work with no freezes. I'm no expert, but my best guesses are:

1) Mobo problem? - either my mobo is too new for linux stock kernel support, OR a manufacturing defect
2) Hard drive issue??? - I'm using a Maxtor 40 GB (about 4 years old), again, I dunno...

Should I try another distro? I dunno, Ubuntu is my favourite and I would really like to get it working on my brand new system. Any help, suggestions, comments are greatly appreciated.  i have only until tomorrow to return my system.. i dont know if its the hardware or the software.

Many Thanks,

Fuji

PS: all my computer specs are at [http://img307.imageshack.us/my.php?image=help9sy.jpg](http://img307.imageshack.us/my.php?image=help9sy.jpg)[/QUOTE]

When you say XP crapped out, what do you mean?

---

### Post by fujie on 2005-09-16
xp wont load anymore.. it says "machine check exception" (BSOD)

but after a while itll work again

---

### Post by spockboy on 2005-09-16
[QUOTE=fujie]xp wont load anymore.. it says "machine check exception" (BSOD)

but after a while itll work again[/QUOTE]

I'd say this is most definitely a hardware error.

Try resetting your BIOS to defaults, and see how the install then goes.

---

### Post by fujie on 2005-09-16
[QUOTE=spockboy]I'd say this is most definitely a hardware error.

Try resetting your BIOS to defaults, and see how the install then goes.[/QUOTE]
it is defaults
i havent touched the bios..
if i load with knoppix live cd 3.7 everything works fine..

i just cant install debian 3.1 or ubuntu

---

### Post by elpresidente on 2005-09-16
[QUOTE=fujie]xp wont load anymore.. it says "machine check exception" (BSOD)

but after a while itll work again[/QUOTE]

after a while? maybe after it cools down? check your fans, especially your cpu fan. also try troubleshooting your memory. if you have 2 sticks, try with just one, then the other (try ubuntu install that is).

the machine check exception is a hardware error. 
[http://support.microsoft.com/?kbid=329284](http://support.microsoft.com/?kbid=329284)

Are you overclocking?

best case senario is that it's just a fan failing and it's over heating. if so, fix it immediately and don't run it until that's done. you will fry your cpu. if it's memory, that's a simple fix as well. it may cost you money but most memory is warrantied for life.

---

### Post by fujie on 2005-09-16
[QUOTE=elpresidente]after a while? maybe after it cools down? check your fans, especially your cpu fan. also try troubleshooting your memory. if you have 2 sticks, try with just one, then the other (try ubuntu install that is).

the machine check exception is a hardware error. 
[http://support.microsoft.com/?kbid=329284](http://support.microsoft.com/?kbid=329284)

Are you overclocking?

best case senario is that it's just a fan failing and it's over heating. if so, fix it immediately and don't run it until that's done. you will fry your cpu. if it's memory, that's a simple fix as well. it may cost you money but most memory is warrantied for life.[/QUOTE]
i doubt its overheating.. 
cpu and mobo are both <35 degrees.  im not overclocking either.  also, it hangs at a specific point (when installing packages in stage 2).. if its overheating wont it be random?

---

### Post by spockboy on 2005-09-16
Memory is often a culprit for weird and random error messages and halt errors. According to this [Microsoft KB article](http://support.microsoft.com/?kbid=329284), and this [mailing list message](http://www.ussg.iu.edu/hypermail/linux/kernel/0201.3/0380.html), it may be worth testing your RAM.

---

### Post by elpresidente on 2005-09-16
[QUOTE=fujie]i doubt its overheating.. 
cpu and mobo are both <35 degrees.  im not overclocking either.  also, it hangs at a specific point (when installing packages in stage 2).. if its overheating wont it be random?[/QUOTE]

i would agree with that. just make sure you eyeball the fans. it worth double and triple checking.

i also agree that ram is worth checking. it is the most likely culprit. i've seen numerous windows install do similar things because of bad memory.

good luck.

---

