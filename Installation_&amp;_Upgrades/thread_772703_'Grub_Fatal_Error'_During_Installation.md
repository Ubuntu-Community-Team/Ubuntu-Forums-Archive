---
title: "'Grub Fatal Error' During Installation"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Tkolini on 2008-04-28
Hey
This is my hard drive set up(i suspect this might be the problem :? )

Raid 0 (ICH8R (i think)) 2x250gb
- 50gb vista
- 20gb xp
- ~380gb stuff

500gb drive
- 60gb ubuntu parition (made using Acronis Disk Director)
- ~405gb stuff

I realise i havent got a swap parition but i didnt think i needed it since i have 3gb of RAM...

I tried to install Hardy Heron onto the 60gb parition, however when it reaches 94% on the progress bar it gives me a fatal error when trying to install the grub bootloader.
I tried to fix this by changing the parition to which it installs to by default (hd0) to the Vista bootloader but that also failed, i also tried to other paritions but to no avail
As a last attempt i used the ubuntu live cd parition tool to change the boot flags of the 500gb drive to see if this solved the problem but unfortunately it didnt.

Any help would be greatly appreciated since id love to try out Ubuntu properly on my main machine, instead of using it for my web server. :)

---

### Post by Tkolini on 2008-04-29
bumples?

---

### Post by Tkolini on 2008-04-30
extra bumples?

---

### Post by Tkolini on 2008-05-01
triple bump? please id really like to solve this...

---

### Post by El King on 2008-05-01
i had this problem before using the RC live CD
u cud try disconnecting the internet while installing, that worked for me, there were also another workaround but i dun seem to remember it now, i will look for it till u try that internet thing.

EDIT: the other workaround is to make the filesystem EXT2 instead of EXT3, u can later upgrade it noworries
lemme knw wat happens

---

### Post by Tkolini on 2008-05-05
thanks:) it successfully finished the installation albeit with a minor problem with the bootloader

thanks again :biggrin:

---

