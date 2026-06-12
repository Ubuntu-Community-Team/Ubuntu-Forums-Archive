---
title: "dual boot help"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by jars_u on 2005-11-24
Hello,

Let me start by saying I am new to Linux.  Was running a WinXP machine and after testing several live distros of Linux I decided I wanted to install and dual boot Kubuntu before I make the final jump away from Windows.

Partioned my HD went well enough, first install of Kubuntu hanged after the GRUB boot loader portion - would not continue with Kubuntu install or let me boot back to WinXP.  Tried another install this one went better - everything with Kubuntu install went fine and seems to be working ok - which brings me here.

But, still no option to load WinXP or Kubuntu which I assume is the purpose of GRUB at some point after POST you get a menu/selection?  I wisely backed up my key windows files before I did the new partitions but is there any solution to this either from the Linux or Windows side?  I hesitate to do anything with my WinXP CD at this point as at least my Linux system is working.

Any and all help and suggestions will be greatly appreciated - I suppose if I need to I can buy a second hard drive and do an complete new install of WinXP and probably get my files off the original HD that way but that still leaves me with the problem of how to dual boot?

Thanks,

James

---

### Post by jars_u on 2005-11-24
Hello,

Let me start by saying I am new to Linux.  Was running a WinXP machine and after testing several live distros of Linux I decided I wanted to install and dual boot Kubuntu before I make the final jump away from Windows.

Partioned my HD went well enough, first install of Kubuntu hanged after the GRUB boot loader portion - would not continue with Kubuntu install or let me boot back to WinXP.  Tried another install this one went better - everything with Kubuntu install went fine and seems to be working ok - which brings me here.

But, still no option to load WinXP or Kubuntu which I assume is the purpose of GRUB at some point after POST you get a menu/selection?  I wisely backed up my key windows files before I did the new partitions but is there any solution to this either from the Linux or Windows side?  I hesitate to do anything with my WinXP CD at this point as at least my Linux system is working.

Any and all help and suggestions will be greatly appreciated - I suppose if I need to I can buy a second hard drive and do an complete new install of WinXP and probably get my files off the original HD that way but that still leaves me with the problem of how to dual boot?

Thanks,

James

---

### Post by aysiu on 2005-11-24
Grub has to be installed to the MBR.
Look here for more details:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by carlos1 on 2005-11-24
I have run a couple of dual-boot machines and have run into the problem that you specified. 
In my case for some reason GRUB did not load correctly during the install, and afterward I had no option to choose the O/S. 
When you install Kubuntu, when it comes to installing GRUB on the master boot record, it should throw up a screen saying that it recognized Windows XP. Did you get this during the install? Then it asks to confirm that all your O/Ses are listed there, and that it would be safe to install GRUB to the master boot record. Did you get that option during install?

---

### Post by jars_u on 2005-11-24
[QUOTE=carlos1] Then it asks to confirm that all your O/Ses are listed there, and that it would be safe to install GRUB to the master boot record. Did you get that option during install?[/QUOTE]

I did get that confirmation during the install - WinXP being the only other OS present - the first time though as I said the install kind of hanged and had to start install again.  But each time it does ask if all my OS have been found.

Is there a means to just install GRUB again without going though an entire install of Kubuntu again?

---

### Post by aysiu on 2005-11-24
[QUOTE=jars_u]
Is there a means to just install GRUB again without going though an entire install of Kubuntu again?[/QUOTE] [Yes](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Alpha_toxic on 2005-11-24
I also run into sth similar once.
Suggestion:idea: : I'd try to manualy edit GRUB's menu. It is in

[COLOR="Red"]
/boot/grub/menu.lst
[/COLOR]

try adding this at the end of the file:


[COLOR="Red"]
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/COLOR]


here I suppose that you'r XP partition is the fist one on you'r first HD (this is what (hd0,0) means)
You'll also have to edit the timeout and the default boot partition,
for the timeout:
there should be a line 

[COLOR="RED"]
timeout         0
[/COLOR]

change the "0" to lets say "5"

for the default boot partition:
there should be a line

[COLOR="RED"]
default         0
[/COLOR]

if you want to make winXP the default boot, than instead of "0" there should be the number of the XP entry in the list. I suppose that you have 3 linux entrys in the list, so XP's entry would be 4-th,but as counting starts from 0 you sholud write 3.

Possible side effects:!: :!: :!: :
I had a similar problem (not with Kubuntu, but with Fedora Core 3), and I solved it in a similar way. But there are no guaranties that this will work. the worst thing that could happen is totally screwing GRUB, and not beeing able to boot neither partition, then you'll have to reinstall Kubuntu and pray that this time it sees XP by it selve[-o<

EDIT: I forgot to mention that you'd need super user privileges to edit [COLOR="RED"]menu.lst[/COLOR], so the best way to do that is typing this in the console

[COLOR="RED"]
sudo editor /boot/grub/menu.lst
[/COLOR]

this will give you the console editor, if you don't like the looks of it, you may try

[COLOR="RED"]
sudo kate /boot/grub/menu.lst
[/COLOR]

this should open the file in kate - KDE's/Kubuntu's text editior

---

