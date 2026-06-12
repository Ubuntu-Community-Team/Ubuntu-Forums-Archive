---
title: "Can't boot LiveCD/Install 8.10 on Trucrypt Drive on Dell Vostro 1000"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by ruhlmark on 2008-11-07
I have been trying to install 8.10 through wubi or any other means on my Dell Vostro 1000, which is currently running xp and is 100% encrypted through Truecrypt. Regardless if I try from the wubi install or booting from a live cd, I keep getting the  "MP-BIOS bug:8254" error, then if I try editing the command line with noapic/nolapic and irqpoll, it gets going but then starts hanging up "buffer I/O error on device sr0".  So is this because of it being a Vostro (which I have heard have had problems with Ubuntu), encrypted, or a combination of both?  

Thanks!

---

### Post by ruhlmark on 2008-11-10
trying to bump as no response yet.  any help would be appreciated!

---

### Post by oilchangeguy on 2008-11-10
google is your friend:
[http://www.google.com/search?q=MP-BIOS+bug%3A8254&rls=com.microsoft:en-us&ie=UTF-8&oe=UTF-8&startIndex=&startPage=1](http://www.google.com/search?q=MP-BIOS+bug%3A8254&rls=com.microsoft:en-us&ie=UTF-8&oe=UTF-8&startIndex=&startPage=1)

---

### Post by ruhlmark on 2008-11-10
Thanks, I looked into that and tried noapic at the end of the options line before the --, which got me past the MP-BIOS bug I was hitting.  But when it got to the boot screen where the orange line bounces back and forth, it just started to hang and then went to black screen that showed a bunch of "Buffer I/O error on Device SR0 block xxxxxx" 

I have updated the Broadcom drivers, as well as the dvd drivers in case that might be causing issues (I had read it might in other forums).  Also, tried booting with "irqpoll", and "all_generic_ide=1" as options but that still yielded the same buffer I/O errors.

Any help is VERY MUCH appreciated.  I have installed 8.4 on my other computer (a dell dimension), so I have some Ubuntu experience, but cannot for the life of me figure out why this isn't working on the Vostro!

---

### Post by ruhlmark on 2008-11-12
bump

---

### Post by BenRichards on 2008-11-15
Had the same problem. Ubuntu 8.10 installed on one computer but would not install on my other two.

The problemn is in the DVD/CD drive.

So I took out my DVD drive from the computer which did install and put it in one which did not.

This worked and Ubuntu installed with no problems.

My suggestions:

Install DVD/CD drive from computer which did install into one which did not (can be replaced after installation)

or change relevant BIOS settings for DVD/CD drive - no idea which these could be, but some people have talked about changing DMA settings.

or do a network install or install via USB drive

Hope this helps

---

### Post by ruhlmark on 2008-11-20
I checked bios for the dma option, but there was nothing there.  I checked and booted from this iso in Virtual Box, and managed to create a persistent USB to boot from that, but i would really like to have it set up through WUBI as the USB drive is only 2gb and i dont think i will be able to enjoy all the linux has to offer on that small a drive.  

So now i press esc to get to the boot menus, and then select the 2nd option that is supposed to boot when you are having ACPI problems, i edit the 2nd line there to say irqpoll as i read in another post, but am still getting busyboxed.  Any ideas on commands that i should be including in the boot command lines/ other boot options i should be checking at??
TJamls

---

