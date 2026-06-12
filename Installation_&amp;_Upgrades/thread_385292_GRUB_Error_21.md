---
title: "GRUB Error 21"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by bt86bt on 2007-03-15
EDIT: PROBLEM SOLVED, SCROLL DOWN FOR SOLUTION.

Hi

I am setting upp an old computer to be a ubuntu-server. The server has one (1) 250gig hdd on ATA (no raid) and very little RAM.

Finally got through the whole installation with the Alternative CD (command-line-system) but was for some reason unable to install GRUB (got an error that did not specify what the error was).

I set up the system like this:
P#1 primary "/" ext2 B F (250gig)
P#2 logical swap  (100mb) 

After that there was no MBR and I used UBCD (ultimate boot cd) to install GRUB. I think I have done the manual installtion correctly (the automatic did not work) but now I get **Error 21** when booting the system.

I would like to edit my conf files in grub but don't know how, the Live CD does not work on this system.

Either help me set up the disks correctly so that GRUB gets installed during installation or help me get the current GRUB to work please!

Help will be grately appreciated.

Oh, and I dont know how to read what is in the conf files atm either :(

---

### Post by zvacet on 2007-03-15
> Boot up your CD and pick &#733;Restore broken system&#733; option.Continue with dialogues until you have to choose your root device.It is probably second,cose you are dual-booting.If that is O.K. dialogue will continue and you will see more options.Select&#733;Reinstall GRUB boot loader&#733;.You will be asked where you would like to install grub.type hd0 and continue.GRUB will be reinstalled and you will be back in &#733;Rescue operations&#733;.Select &#733;Reboot the System&#733;.

I hope it helps.

---

### Post by nazg on 2007-03-15
So, i have to install it not in hd0 right?

Another question, since grub will be installed on my sda drive, what will happen if i turn the laptop on and don't have the external hd (sda) connected?

---

### Post by bt86bt on 2007-03-17
> **zvacet said:**
> 
"Boot up your CD and pick &#733;Restore broken system&#733; option.Continue with dialogues until you have to choose your root device.It is probably second,cose you are dual-booting.If that is O.K. dialogue will continue and you will see more options.Select&#733;Reinstall GRUB boot loader&#733;.You will be asked where you would like to install grub.type hd0 and continue.GRUB will be reinstalled and you will be back in &#733;Rescue operations&#733;.Select &#733;Reboot the System&#733;."

I hope it helps.

No it didn't. There is no option for "Reinstall GRUB boot loader" when I get that far.

So I have still no clue how to fix this....

Is it possible to try to install boot loader on other system to my hdd?

---

### Post by confused57 on 2007-03-17
Maybe there something in this howto that can help:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by bt86bt on 2007-03-17
[IMG]http://users.bigpond.net.au/hermanzone/p15/re_grub_10.png[/IMG]

That is so strange, I don't have that option...

Edit: Problem solved, solution:

First got "Ultimate Boot CD" then picked GRUB untill I got to the grub> promt and wrote the following:

  find /vmlinuz

This will give you what system you have installed linux, mine was (hd0,0) next step you use that:

  root (hd0,0)

Load the kernel:

  kernel /vmlinuz root=/dev/hda1

  initrd /boot/ini

After this press TAB and the grub will complete the line, mine was like this: initrd /boot/initrd.img-2.6.15-23-server or something like that.
Bext just press:

  boot

and everything should start! Solved!

---

