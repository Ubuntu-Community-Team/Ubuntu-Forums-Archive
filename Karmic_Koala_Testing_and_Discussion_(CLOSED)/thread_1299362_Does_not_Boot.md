---
title: "Does not Boot"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rakeshreddyn on 2009-10-23
Hello Guys,

I have been using Kubuntu since a month and recently after going for upgrade options, restarted the system and the only option it shows me as

[B]Ubuntu Karmic (development branch) , memtest86+

[/B]and this runs for ever. Shows my other other operating system as vista and that boots good.

I am not sure, if i have done any thing wrong. 

I have a program on my desktop which i need it by tomorrow badly.

Any help will be greatly appreciated.

Thanks. 
Rakesh.:)

---

### Post by falconindy on 2009-10-23
You'll to provide more information. Boot from a LiveCD and post for us the contents of '/boot/grub/menu.lst', the output of `sudo fdisk -l`, and the output of `sudo blkid`.

---

### Post by rakeshreddyn on 2009-10-23
Can you please be a little more specific.

---

### Post by falconindy on 2009-10-23
1) Boot from a LiveCD. That's the CD you installed from. Select 'Try Ubuntu without any changes to my computer' instead of the install. It'll load up a familiar desktop.
2) Open up a terminal. To do that, press alt-f2 and type 'gnome-terminal', without the quotes.
3) Type 'sudo blkid', again without the quotes. Copy and paste the contents of that into a post here.

---

