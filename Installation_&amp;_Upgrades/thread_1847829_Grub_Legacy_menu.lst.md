---
title: "Grub Legacy menu.lst"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by avnd on 2011-09-21
I'm having a system where I have two hard disks. Both have Grub Legacy installed on their MBR's with the configuration files residing in a separate boot partition.

Both the menu.lst files look the same. I want to be able to differentiate which hard disk I've booted into at the the time of the menu display. 

Can someone tell me how to add a 'title' at the top of the menu list (a la GRUB2) . I just want to add a line that says 'You have booted into hd0/hd1'.  

I realise that there is an option of adding a dummy menu entry with that line. But I guess that would be considered a  menu option and would really not be 'neat'. 

Kindly offer your suggestions.

Cheers!

---

### Post by drs305 on 2011-09-21
I don't know about the titles, but IIRC there was a 'pretty colors' option that was disabled by default but could be enabled by removing the #. If you changed one, one menu would be black/white and the other blue/white.

Not what you are looking for an easy way to differentiate if you member which color is which.

I just realized how much about Grub legacy I've forgotten....

---

### Post by vinterkind on 2011-09-21
the color thing is a good advice, :D
Else you could try to just echo your line.

```
title ...
root ..
kernel ..
initrd ...

echo ...
```

If you're in the grub shell (simply invoke grub) you could type help to check out the commands.

---

