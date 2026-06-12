---
title: "how do i acpi=force? installing on ol gateway laptop"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by foso on 2007-06-17
hey all, title says it all, trying to install feisty on an old gateway and it says i need to acpi=force, but i dont know where to put that command to get it to open the live cd or install
thanks!

---

### Post by PaulFr on 2007-06-18
You need to add acpi=force in your /boot/grub/menu.lst file.

To do that, open a terminal (Application->Accessories->Terminal) and type the command **gksudo gedit /boot/grub/menu.lst**. Look for the **first** group of lines that reads something like the following:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
**kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=163b6467-7db3-4961-a361-cd8ab1dba97f ro quiet splash**
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

It will not be exactly the same, just similar - but it must be the first such group of lines. Click at the end of the line starting with **kernel** and add ** acpi=force**, i.e. after **ro quiet splash** in above example.

Save the file after you have checked it carefully, and then reboot your machine. Hope this helps.

---

### Post by foso on 2007-06-19
i dont think i can get to a terminal, i dont have it installed yet, when it tries to start loading from the live cd then it says i need to acpi=force, so i cant get that far yet, thanks

---

### Post by merlinus on 2007-06-19
Try F6 at the opening menu and add acpi=force to the end of the bootup line.

-merlin

---

### Post by foso on 2007-06-23
i dont think im doing this right because it doesnt do anything else, when the live cd menu comes up, when i have start or install ubuntu highlighted and hit f6,  then it says "boot options:casper initrd=/casper/initrd.gz quiet splash --" is that where i enter it? when i just type in "acpi=force" then it still says i need to do acpi=force and wont go any further thanks

---

### Post by merlinus on 2007-06-23
Try the Alternate Desktop install cd, which is text-based.

-merlin

---

### Post by foso on 2007-06-24
ok, i downloaded the iso and burnt the cd, will give it a shot later today, thanks

---

### Post by foso on 2007-06-24
hey, i t says i dont have enough memory, then it says low memory mode and just sits forever, sometimes the cd spins a bit, but it just sits, any ideas? im a newbie, so it could be something obvious that i just dont know, thanks

---

### Post by merlinus on 2007-06-24
Please post your system details.  You may be able to install from the xubuntu alternate desktop cd.

-merlin

---

### Post by foso on 2007-06-24
its a gateway laptop, i think its a 98, intel pentium II mmx 32 mb ram, its got a 3.5 floppy and a cd drive that are interchangeable, 3.81 gb hd, anything else? thanks alot

---

### Post by merlinus on 2007-06-24
Not nearly enough RAM for any version of ubuntu.  Here are the specs for xubuntu, which is less resource-intensive than the other versions.

To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").

:(

-merlin

---

### Post by foso on 2007-06-24
sad, what about damn small or something like that? is that anything i could use? win 98 is unbearbly slow

---

### Post by merlinus on 2007-06-24
Can you add more RAM?  Another 32MB will let you install xubuntu.

damnsmalllinux -- [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

and puppylinux -- [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

might work.

Good luck!

-merlin

---

