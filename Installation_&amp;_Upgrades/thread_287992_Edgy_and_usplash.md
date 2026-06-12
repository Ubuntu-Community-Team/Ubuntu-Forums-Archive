---
title: "Edgy and usplash"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by DrSkalpell on 2006-10-29
Hi,

After having upgraded to edgy I have lost my usplash image. Now there is only plain text. 

menu.lst:
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=9943ebe8-11dd-4a12-a912-346528ef7ac2 ro nosplash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

What do I have to write in menu.lst in order to enable upslash again? Previously (after kernel upgrades) I have managed to restore the image by replacing "ro nosplash" with "ro quiet splash vga=791".

---

### Post by frankelr on 2006-10-29
I think I can help you.  if you read your menu.lst line you will see kernel/boot/    .....ro nosplash . Usual line reads .. ro quiet 
splash

You will need to do a sudo update-grub after editing menu.lst.

The vga=791 is only necessary if the default setings won't work on your system.  You can test whether the change will work by editing the grup boot line (useesc to display the grup menu)

Bob

---

### Post by DrSkalpell on 2006-10-29
> **frankelr said:**
> I think I can help you.  if you read your menu.lst line you will see kernel/boot/    .....ro nosplash . Usual line reads .. ro quiet 
splash

You will need to do a sudo update-grub after editing menu.lst.

The vga=791 is only necessary if the default setings won't work on your system.  You can test whether the change will work by editing the grup boot line (useesc to display the grup menu)

Bob

Hi frankelr,

Thanks for your reply :) 

I tried what you said but it did not work. When I change to "ro splash" I get only text. "ro quiet splash" gives me a blank sqreen with no information. 

Does anybody else have some good tips?

---

### Post by khedron on 2006-10-29
Strange... I changed it to "ro splash". When I first boot there is pure text, but after about a second it changes to the loading screen, complete with scrolling text on what is being loaded at the time. With quiet enabled, there is just the loading screen, with no text below it.

---

### Post by DrSkalpell on 2006-10-29
Yes, it is strange :)

I have booted the computer several times now, but still there is only pure text.

---

### Post by soaro77 on 2006-10-29
I am getting the exact same thing. I have "ro quiet splash vga=791" and I get some text at the start and then blank screen until gdm starts.

---

### Post by KaosX on 2006-10-30
same deal here, no splash image, no boot text either.

---

### Post by traneHead on 2006-10-30
Me too :(
Dapper: all good and cool
Edgy: no usplash (with "quiet splash" as before)
Have reinstalled usplash

---

### Post by KaosX on 2006-10-30
I think, for me, it's an issue with the .17 kernel, if i use .15 itll boot (with no splash, but itll boot)

---

### Post by DrSkalpell on 2006-11-02
Reinstalled all the usplash packages using synaptic and did a 
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

Did not fix anything...

---

### Post by jpyanowski on 2006-11-12
This worked for my Edgy usplash, all these changes done to menu.lst: 
a. Uncomment the #Pretty colours line (line 26 in gedit)
b. Change no splash to splash vga=791

This gives me scrolling words (Verbose) and a progress bar. Remember to redo this if you reconfigure Grub.

Hope this helps. :D

---

