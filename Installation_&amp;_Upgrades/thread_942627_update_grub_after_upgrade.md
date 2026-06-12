---
title: "update grub after upgrade?"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by AGSzabo on 2008-10-09
hi,

i just upgraded from 7.x to 8.x and wonder why the new kernel has not been added to my menu.lst

now what is the procedure to plug the new kernel into menu.lst ? i guess it is enough to edit menu.lst manually and insert the new kernel filenames.

after editing menu.lst is it required to update grub bootsector? if yes, what command?

regards,
AGS

---

### Post by mikewhatever on 2008-10-09
Can you post the outputs of the following commands:
ls /boot
uname -r

---

### Post by AGSzabo on 2008-10-09
sure...

here it is:
```

calla@dunwyn:~$ ls /boot
abi-2.6.22-15-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic             lost+found
config-2.6.22-15-generic          memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.22-15-generic
grub                              System.map-2.6.24-19-generic
initrd.img-2.6.22-15-generic      vmlinuz-2.6.22-15-generic
initrd.img-2.6.22-15-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic
calla@dunwyn:~$ 

calla@dunwyn:~$ uname -r
2.6.22-15-generic
calla@dunwyn:~$

```

the 2.6.22-15-generic is already in my menu.lst but instead of the 24-19 there is a 22-14!

---

### Post by Kevbert on 2008-10-09
If it's the only linux OS and the last OS installed, boot up Ubuntu and go into terminal and enter
```
sudo upgrade-grub
```
If not and you have multiple linux operating systems see my [COLOR="Red"][thread]("http://ubuntuforums.org/showthread.php?t=942375")[/COLOR].

---

### Post by AGSzabo on 2008-10-09
its weird:
```

calla@dunwyn:~$ sudo upgrade-grub
[sudo] password for calla: 
sudo: upgrade-grub: command not found
calla@dunwyn:~$ 

```

do you mean *update-grub*?

i have a windos 98 and a windos xp installation also on my hd.

---

### Post by AGSzabo on 2008-10-09
i just tried update-grub. it prints out some text which reads like the name of the new kernel, however when rebooting the menu was still the same (only 22-14 and 22-15), the 24-19 did not show up in the bootmenu.

---

### Post by Kevbert on 2008-10-09
Sorry, yes I meant update-grub.
It looks like you may have to edit /boot/grub/menu.lst manually:
```
title		[COLOR="Red"]Ubuntu 8.04.1, kernel 2.6.24-19-generic[/COLOR]
root		(hd1,6)
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.24-19[/COLOR]-generic root=UUID=ac4f091c-d379-475c-8f76-b6e9ca0b5865 ro quiet
initrd		/boot/initrd.img-[COLOR="Red"]2.6.24-19[/COLOR]-generic
quiet

```
The bits in red are what you need to change to/from the old kernel.  The title line can be anything you like. UUID won't change from what you already have.  You need to do this for recovery mode as well.

---

### Post by AGSzabo on 2008-10-09
now it works! thank you :)

```

calla@dunwyn:~$ uname -r
2.6.24-19-generic
calla@dunwyn:~$

```

---

### Post by Kevbert on 2008-10-09
No problem. I surprised that the grub wasn't upgraded when you did a distribution upgrade and that update-grub didn't work.

---

### Post by AGSzabo on 2008-10-10
i remeber there was a question durign the upgrade wether my menu.lst should be overwritten or not and i selected NO... because i did not know what would happen to my system...

---

### Post by Kevbert on 2008-10-10
It you had answered yes it would have worked. If you are in any doubt of things like this you can always make a backup of the file in question by using (example)
```
sudo cp menu.lst menu.old
```
Then if a problem occurs, all you need to do is get to a terminal prompt (normally > or #) to recover the file.

---

### Post by AGSzabo on 2008-10-10
ok, thats good. i just supposed any program would not work during the upgrade...

---

