---
title: "Grub after Windows XP instal"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by stackcheese on 2006-06-12
I had a fully functional Dapper/XP dual boot working, however, I got my hands on a copy of XP Pro and decided to install it over my copy of XP MCE.

I initially thought I'd be able to reload the Grub menu with the Live CD, however, when I get to the partition screen it shows one unallocated partition. I can click next to that screen with out setting up a new partition and I can see two of my three partitions (swap and / with home missing) however once it begins to install I get a pop up that says that root is not defined.

I'm assuming this is a MBR problem? or maybe a partition tables problem? Whatever it is does anyone know a fix or steps I can take next time to avoid a problem like this?

I know I was able to reload the Grub once before but I don't know why it doesn't detect my partition table now. The only thing i remember changing since then was the updated 686 kernal from the 386 prior (core duo laptop)

---

### Post by catlett on 2006-06-12
Are you trying to run the install without formatting to get gub installed? You can try it like this if you have a live cd and grub is installed to a partition.
Boot to the live cd. Get the terminal and enter ```
sudo grub
``` This will get you a grub< comand line. Next in the terminal at the grub> prompt enter ```
find /boot/grub/stage1
```
Next use whatever that output was, we'll use hdx,x but put in hd0,1 or hd1,3  Whatever the output from the find command was. Still at grub< ```
root (hdx,x)) 
``` and then enter```
 setup (hdx,x)
``` Finally exit the grub command line. grub<```
 quit
``` That is it. Barring a hard drive issue grub is installed.

This was found in 2 different places. The krazy penguin dapper guide and at the mepis  site (somewhere, I forgot the exact links. I copied over the commands and saved thenm to a text doc.) So I have the commands buy not the links.

---

