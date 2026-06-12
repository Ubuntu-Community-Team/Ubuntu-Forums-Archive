---
title: "Installing Ubuntu on my Home Computer"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by killerabbit on 2008-03-20
Ok. My parents are not very computer smart. I want to install Linux on my main (family) computer, since that is what I use for everyday use. To keep things simple, I would partition of course. My question is simply, is there a way to either have Windows be the first item on the boot list, or to have it automatically boot into Windows? Ie I want it to automatically boot into windows without any buttons needing to be pressed. I have another computer to test this out on as well. Thanks in advance.

---

### Post by logos34 on 2008-03-20
Set the **default **line in menu.lst to windows (e.g. **4** instead of 0)

[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by pbcartwright on 2008-03-20
you need to modify the file /boot/grub/menu.lst
there is a line with default # where # is the default "title" you want to boot to.
they count 0,1,2... so the default is normally "0", the TOP entry.
 my windows is the 6th entry, so I have it default to 5, to boot into windows.

---

