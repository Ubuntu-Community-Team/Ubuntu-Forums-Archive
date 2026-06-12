---
title: "Vista &amp; Ubuntu on 2 seperate drives"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by prickee on 2007-07-19
I will be as brief and detailed as possible.  

**_Hardware: _**
3Ghz Intel 478
                  1G Kingston memory
                  Nvidia GeForce 5900SE 128Mhz
                  2 WD HD's both 160G  
1600JS - Vista Ultimate
                               1600JD - Ubuntu Fiesty :)
Intel Pro 1000 NIC

Simply I've installed Vista for family and kids of course :rolleyes: and now I want to install Ubuntu on the clean/blank JD HD.  I reboot and boot from Ubuntu Live CD and get the install option screen.  Hit option 1 and after about 5-10 sec I get this error. _**[COLOR="Red"]73.828576 ata.301 failed to set xfermode (err_mask=0x4)[/COLOR]**_ I'm thinking it has something to do with both hard drive are SATA but I'm not sure.  Any and all help is needed and appreciated.  Thanks

---

### Post by beatbros on 2007-07-19
Hi,
you can try this solution.

[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)


Bye

---

### Post by prickee on 2007-07-20
Is this problem just with fiesty?  Do you think if I install 6.10 then update will solve the problem?  How can I update grub when I get this error as soon as I start install?

---

### Post by beatbros on 2007-07-20
Hi,
personally i would start directly with a fresh Feisty.
When booting Grub shows up a screen and you have to press 'E' to edit the options and add the word 'irqpoll' at the end of the line.

As a sample look here:
[http://appuntiubuntu.files.wordpress.com/2007/06/grub_dopo.jpg](http://appuntiubuntu.files.wordpress.com/2007/06/grub_dopo.jpg)

If you succesfully boot in ubuntu you can verify your options by editing  this file


```

#make a backup first (just in case)
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
#edit the file
sudo gedit /boot/grub/menu.lst

```



this is a sample relevant section:

title	Ubuntu, kernel 2.6.20-15-generic
root	(hd0,1)
kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=74409af6-abaa-4245-b943-ba45eaa3b6f1 ro quiet splash
initrd	/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

this is a sample **modified** section

title	Ubuntu, kernel 2.6.20-15-generic
root	(hd0,1)
kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=74409af6-abaa-4245-b943-ba45eaa3b6f1 ro quiet splash **irqpoll**
initrd	/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


bye

---

