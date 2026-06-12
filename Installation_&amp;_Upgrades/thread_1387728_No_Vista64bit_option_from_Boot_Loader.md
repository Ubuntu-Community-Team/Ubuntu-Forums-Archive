---
title: "No Vista64bit option from Boot Loader"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by greetingsfrommike on 2010-01-22
Hello there!

I've just installed Ubuntu on my machine to dual boot with Vista 64bit. When i reboot i get absolutely no windows options to boot to, just 3 ubuntu options (one normal; one safe mode and one "memtest86+").

The hard drives being used are raid and the two OS are on separate partitions of the same HD and the Vista drive did not require shrinking - ubuntu went straight onto free drive space.

I did the whole "[COLOR=#ff0000]**sudo gedit /boot/grub/menu.lst**[/COLOR]" thing and the results are below:


## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic-pae
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.31-17-generic-pae root=/dev/mapper/isw_gefahhchc_Volume05 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-17-generic-pae (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.31-17-generic-pae root=/dev/mapper/isw_gefahhchc_Volume05 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic-pae

title        Ubuntu 9.10, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


...as you can see there are no "other operating systems" results.

I would very much appreciate it anyone could offer any ideas about what's occurring...

regards

---

### Post by darkod on 2010-01-22
I believe for fakeraid you have to add it yourself. This might help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

On the right in the content, look in section 3.1.1.9 Finish the install.

---

### Post by greetingsfrommike on 2010-01-22
Cheers for the reply

So would you suggest re-installing from the Alternate CD?

---

### Post by darkod on 2010-01-22
I haven't installed on raid yet, but I was reading about it. It doesn't sound like you need a reinstall. That article recommends Alternative CD from the start but it seems the standard cd worked for you. You even have grub and can boot ubuntu.

Now in that article just focus on the part where it says to add your windows entry manually in menu.lst, that's in that Finish the install section.

---

### Post by greetingsfrommike on 2010-01-22
sorry... didn't read that far!

I'll give it a go now... thanks again!

---

