---
title: "Dual Boot Ubuntu Grub Error 15"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by markbuntu on 2008-07-29
I have recently run into a problem with Grub. I am running Hardy i386 and amd64 on separate identical SATA hard drives. I have grub on both of them. The i386 is on sda and the amd64 on sdb.

I set up the grub on sda by copying the menu.lst entries from sdb to the menu.lst on sda and had no problem dual booting until today. 

I chose the sdb (amd64 kernel -19) from the grub menu and got 

error 15, file not found.

It thought "This is strange, maybe the amd64 install is screwed up." So, I changed the boot menu in the bios and rebooted. The sdb grub came up and I was able to boot into the amd64 install with no problem.

So, I copied the sda grub menu.lst entry for the i386 kernel into the sdb grub menu.lst and tried to boot into it. Again I got

error 15, file not found.

The weird thing is that this worked for months until I tried it today.

---

### Post by Sef on 2008-07-29
This is GRUB error 15:

>  File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

---

### Post by Pumalite on 2008-07-29
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by markbuntu on 2008-07-29
Well, I am not having a typo error since I copy and pasted the entries from one menu.lst to the other. 

As I said, it worked until today.

Something more sinister seems to be going on here.

---

### Post by Pumalite on 2008-07-29
Use Super Grub to boot it; if it's there:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by markbuntu on 2008-07-29
I know I can get supergrub to do this, I am just wondering why what I used for months decided to suddenly stop working.

---

### Post by louieb on 2008-07-29
> **markbuntu said:**
> I set up the grub on sda by copying the menu.lst entries from sdb to the menu.lst on sda and had no problem dual booting until today.
Is the copy to sda something new? 
Or are you saying it did not matter which hard drive booted 1st you could load either Ubuntu install? 
Does the file /boot/grub/device.map look the same in both installs?

---

### Post by markbuntu on 2008-07-29
No, the copy to sda was a few months ago and worked quite well until today. I copied to sdb today from the sda grub menu.lst and got a error 15 when I first tried to boot into sda. Same as with going the other way.

UPDATE:
I just got a bunch of updates to my amd64 install (sdb) and now, when I try to boot into sda from sdb grub it kind of half assed boots into low graphics mode. I tried this with both -20 and -19 kernels and it is the same. Sartup scripts seem to be all screwed up and give me the same messages like three times and then x comes up in low graphics mode and my mouse does not work. I know it is booting ito sda because I have different passwords and screen setups so I can tell the difference.

Rather than reconfigure things I thought I would change the bios back and try to boot straight into sda first. It boots with no problems at all from its own grub.

Weird huh?

Edit. Part of the update for sdb was the new -20 kernel which I suppose ran update-grub. btw, it works just fine.

But why would that make a difference for something way down the list. And why would it be so screwy?

And yes, the device.map files are identical.

---

### Post by DugDra on 2008-07-29
Hi
I had a simular problem some time ago. I am relitavely new to Linux.
This happened each time after a kurnel update.
I tried Super Grub.  This did not fix the problem but I discovered how to edit the boot entries in the grub menus during the boot.  I found that grub was looking for (hd0, 6) not (hd0,5) and that the UUIDs did not match what vol_id found.  (I had a copy of  fdisk -l output from before the problem)  The device name (/dev/hdaN) associated with three partitions had changed from the current fdisk output.  I edited the UUIDs in the grub menu and pressed 'b' and Ubuntu loaded normally.  Upon reboot grub was again looking for (hd0,6) not (hd0,5).  I edited /boot/grub/menu.lst to (hd0,5) and now Ubuntu boots from the hard drive. This happened again with the next kernel update.
I found a way to permently fix this but, I'm sorry I didn't take any notes and don't rember exactly what I did. I think I changed a refenence to hd0,6 some where else in the /boot/grub/menu.lst.

Hopefully someone with more Linux savy can help.
doug D

---

### Post by louieb on 2008-07-29
It kinda sounds like the kernel updates is somehow behind the boot problem. One of your installs gets a kernel update and the other installs grub menu isn't be updated.

I guess thats why you are copying entries from one menu to the other.

There is an easier way. Have Grub on sda load the the grub menu on sdb and vise versa. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") 
Take a look at the **configfile** option. an entry would look something like this.

```
title load grub menu  from another install
configfile (hd0,1)/boot/grub/menu.lst    
```

Another slick way to do the almost the same thing is to use the chainload option.  More on both ways can be found in link above. (Its a big page so just do a find on configfile).

---

### Post by markbuntu on 2008-07-30
Thanks for the handy link.

Well I tried the configfile option and got the same Error 15, file not found.

So I tried the chainload option and voila, Success!!
It seemed to get hung up for a bit but it worked.

We will see if this persists through the next kernel update....

I will mark this thread as solved, for now.

---

