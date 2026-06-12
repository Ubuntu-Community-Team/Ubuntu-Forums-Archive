---
title: "Getting windows to work again"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by Groth on 2006-02-20
I used to have windows and ubuntu installed to two partitions of the same HD. I ran into some problems which required me to reinstall windows (Although I dont have an actual windows CD, only a "System recovery" CD which the manufacturer included). Apparently though, this CD doesn't fix the MBR, so I got an error when GRUB started to load. I'm on a laptop with no floppy drive, so I cant use a boot floppy. I've looked at some similiar posts here but people said either to use the windows CD or a boot floppy to fix my MBR. Is there a way I can do it without these? (Ie from linux, or with a boot CD if those exist). 
Thanks for the help

---

### Post by Coelocanth on 2006-02-21
If you know anyone with a Windows install CD, you could use theirs to fix your MBR.

---

### Post by dineth on 2006-02-22
i beleive the command is: fdisk /mbr

or use a windows installer cd, go to the installation menu and press R, for repair... then put ur admin password and u can type: fixmbr

all these can be seen in the console wif a type of "help" once u get to the console... this lists down all the commands available and if u need further instructions, use: help "command" for more info.

this is if u wanna play god wif everything else... but fixmbr should do. :) tc.

i installed ubuntu alpha n grub screwed my windows... i dunno how... but i had to reformat.

---

