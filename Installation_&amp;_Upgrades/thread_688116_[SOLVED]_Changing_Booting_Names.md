---
title: "[SOLVED] Changing Booting Names?"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by tom_the_drummer on 2008-02-05
Is there anyway I can change the names of what the OS's aooear as when I select an OS to boot? Ideally, I would like the one "Ubuntu 7.10" or whatever it is to say "Ubuntu Studio" as that is what it is :)

(Please not there is more to it than just ubuntu 7.10 but can't remember off top of my head, and there is also another one labelled ubuntu 7.10 which is the real ubuntu)

Thanks a lot



Tom

---

### Post by Scavok on 2008-02-05
Perhaps you can edit the GRUB menu.lst file in /boot/grub

E.g.:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea5ba30-1774-458a-a9ad-44c3a1641280 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
(Note: not really CODE--it's a QUOTE--however CODE makes it easier to read.)

Edit the 'title' to be whatever you want.

---

### Post by forestpixie on 2008-02-05
yep that'll do it

```
gksudo gedit /boot/grub/menu.lst
```

back it up if you're not sure

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.050208
```

---

### Post by tom_the_drummer on 2008-02-05
Hi guys,

Have found the file and changed it to what I want. However when I click save I get a message at the top next to a no entry sign saying "Could not save the file /boot/grub/menu.lst because I don't have the permissions to save the file?

I am the systsem admin and have got all the options enabled in the user accounts section.


Cheers

Tom

---

### Post by Borbus on 2008-02-05
Use sudo. You need to be root. Being an "admin" on a linux box is different to that on a doze box. On linux there is (should be) only one all powerful account and that is root.

To clarfiy, sudo gives you root permissions (in ubuntu it does anyway), you don't actually need to log in as root (nor should you ever).

---

### Post by smartboyathome on 2008-02-05
Use gksudo, using sudo with graphical apps can ruin them.

---

### Post by forestpixie on 2008-02-05
almost exactly the same as my post earlier then ;)

---

### Post by tom_the_drummer on 2008-02-06
> **forestpixie said:**
> almost exactly the same as my post earlier then ;)

What do I have to search for in the synaptic package manager?

---

### Post by forestpixie on 2008-02-06
you don't have to search for anything?

I gave you 2 commands - second one will back up the file justin case 

second gives command to open file as root so you can edit the titles you want to edit

if you're using kubuntu or xubuntu the commands are different but it appears you're using ubuntu or studio

---

