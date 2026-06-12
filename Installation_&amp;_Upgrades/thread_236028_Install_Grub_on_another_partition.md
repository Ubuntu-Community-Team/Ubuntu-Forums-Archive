---
title: "Install Grub on another partition ??"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by CHUCKYCHUCK on 2006-08-14
Hi !
I'm an ubuntu fan since Warty ^^, it's been several months since i've installed the dapper version, the version that brought in the graphical installation mode ( with the live-cd )
when my computer run breezy, i installed grub on the ubuntu partition ( which is not the 1st ), and i used another boot manager ( G.A.G. ) in the MBR, and this "gag" then redirects me either to windows either to grub

but when i installed the dapper version, with the graphical installation mode, i couldn't install grub elsewhere than in the Mbr, i don't know if it is the graphical installation mode which doesn't offer this option, or it is me who didn't notice it ....
if it doesn't offer it, it is possible to revert back to the text installation mode ??

( my previous boot config is more convenient, as when i reinstall windows i juste have to reinstall G.A.G. which is easier ( graphical ))

thanks

---

### Post by Herman on 2006-08-14
> but when i installed the dapper version, with the graphical installation mode, i couldn't install grub elsewhere than in the Mbr, i don't know if it is the graphical installation mode which doesn't offer this option, or it is me who didn't notice it ....
if it doesn't offer it, it is possible to revert back to the text installation mode  The Dapper Drake 'Alternate' CD is like the former Breezy, Hoary and Warty edition installers. 
The new Dapper Drake 'Desktop' CD does not let you choose different bootloader options.
You need to download the 'Alternate' Install CD.

I would not bother re-installing just because of that though, it is a trivial matter, and easy to correct. I would just install Grub or Lilo to the first sector of the Ubuntu partition and then re-install GAG to MBR or whatever you had on MBR.
   To install GRUB in the first sector of your Ubuntu partition at any time after Ubuntu is already installed, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition") 
How to install Lilo to a Ubuntu partition,  [Install Lilo from terminal.]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal")
Regards, Herman

---

### Post by CHUCKYCHUCK on 2006-08-14
thanks, i will take a look at this "alternate" cd

> I would not bother re-installing just because of that though, don't worry i was not planning to reinstall ubuntu :), i just wanted to revert back to my previous boot config the next time i install ubuntu ( when edgy is released ), as it is more convenient when reinstalling windows
my windows-xp doesn't need to be reinstalled right now, but maybe in a few months

thanks again, bye !

---

