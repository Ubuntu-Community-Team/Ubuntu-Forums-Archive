---
title: "Hanging during boot at &quot;Starting hotplug subsystem...&quot;"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by Thomas Barregren on 2005-07-28
Ubuntu hangs on startup. The last message is "Starting hotplug subsystem..." I understand that the problem comes from Ubuntu missing support from some of the hardware in my brand new laptop. I have a LG LM70 Express laptop with following components which I believe may cause my problem:
[list]
[*]Marvell Yukon 88E8053 PCI-E Gigabit Ethernet
[*]Intel PRO/Wireless 2200BG wireless card
[*]ATI Mobility Radeon X600 graphics card
[*]Intel's Azalia High Definition Audio
[*]Agere softmodem
[/list]
I have found [an instruction](http://www.progsoc.uts.edu.au/~rheise/LW60/) on how to solve this on a similar machine (LG LW60) using Debian. But to apply this solution, I must first get Ubuntu to boot, which it can't. A moment 22.  ](*,)  So what can I do?

Since I have Windows XP also installed on my machine, I downloade [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)  and looked for error messages in /var/log/, but didn't find anything usable.

I would very much aprechiate any hint on how to solve this problem. For instance, how can I boot a mininal Ubuntu so I can make the fixes described above?

BTW, to install Ubuntu at all, it was necessary to give following boot parameters: linux pci=bios,biosirq acpi=off.

Regards,
Thomas

---

### Post by guizzzmo on 2005-07-28
i have same problem with a toshiba satellite m40 laptop. First try ctrl+c while you get the message, so it will ignore hotplug. I have to wait one second more or less before pressing ctrl+c so the usb mouse configures propperly, otherwise it wont work (the built-in mouse does not work in any case).

The problem is that when i press ctrl+c my net config has errors and i have no internet access. When i type ifconfig -a i get a strange hardware address 00:00:00:1C or something like that. I also changed manually the ip-address but it's still not working.

I've read in another post that somebody fixed it typing "/etc/init.d/hotplug restart" but my computer hangs.

what can i try?

---

### Post by guizzzmo on 2005-07-28
My LAN device is
Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller

---

### Post by Thomas Barregren on 2005-07-29
[QUOTE=guizzzmo]First try ctrl+c while you get the message, so it will ignore hotplug.[/QUOTE]

Thanks for your answer. Unfortunately, CTRL + C have no effect. :( What can I do about that? Is there some boot parameter I can give to prevent the hotplug subsystem to start at all?

I should have said in my orignal post that I have tried CTRL +C without the expected result. That is the reason I can't start Ubuntu and apply the [fix](http://www.progsoc.uts.edu.au/~rheise/LW60/). I should also mention that I have tried to press CTRL + C many times and after various length of time without result.

---

### Post by Mika3107 on 2005-08-03
I have the same problem: Ubuntu stops booting in 'Starting hotplug system'.

Ive been using ubuntu for one week and everything worked fine until yesterday: the problem suddenly arrived.

I tryed to install ubuntu all from the beginning, but still system stops booting when 'Starting hotplug system' is on the screen. How this can be possible? ](*,) 

I also tryed that ctrl-c -thing, and then ubuntu continues booting, but after that nothing really works.

I do not know what to do, maybe I'ts better just install Windows again :sad: 



Sorry for bad english, but this is best I can do.

---

### Post by Meqif on 2005-08-03
I also had this problem but I found the solution in a post here. Hope it works for you. :)

[QUOTE="[http://www.ubuntuforums.org/showpost.php?p=270083&postcount=7](http://www.ubuntuforums.org/showpost.php?p=270083&postcount=7)"]We have to boot with as parameter "irqpoll"[/QUOTE]

---

### Post by Mika3107 on 2005-08-04
Thanks for the help.

Unfortunatelly 'irqpoll' didn't work for me.

But at least I learned how to get access to internet again!
When I waited a few seconds and pressed ctrl-c, my mouse will work, but ethernet card doesn't. Solution is that you have to boot again, and this time use the ctrl-c immediatily when hotplugging starts. Now internet and the mouse will magically work. 

It is so much easier to get solution for hotplugging issue when you can get to the internet  :) .


But, does anyone know something alternative solution that might help? Still I'm wondering how it is possible that my first install went well, and now it is that hard. #-o 


And again, sorry for my poor english. Hope you can understund it.

---

