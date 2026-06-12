---
title: "Operating System Not Found"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by jfwgourlay on 2007-05-28
I have installed Feisty on a Fujitsu S4546 Laptop.  I had to use the alternative CD as the Live CD doesn't show me anything after starting to load splashfs....  if I remove the quiet splash options on boot.

The alternative CD loads fine but when I reboot I get operating system not found.  I can boot from the alternative CD by selecting the boot from first hard disk option.  The installation seems fine and everything seems to run...

I have tried updating the MBR, I have blown away the MBR and reloaded Ubuntu, but still no joy.

This is the info from grub:
*****
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

*****

So it looks successful but still won't boot.

John

Update....

It is the little things that get you.  The option to boot from the H/D was switched off (small ! in front of it).  Duooh!

---

