---
title: "Trouble Editing GRUB settings"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by degslon on 2011-01-18
Hello,

I am a new Ubuntu user, and I am attempting to set Windows 7 64 bit as my default OS in the boot loader instead of Ubuntu 10.10.

I have entered the command
*gksudo gedit /boot/grub/menu.lst *
into terminal, and the menu.lst file does open. However, this file appears to be completely blank, which does not seem to make sense and is preventing me from changing the boot order.  

If anyone could be of assistance it would be greatly appreciated.

Thanks.

---

### Post by Quackers on 2011-01-18
Welcome to UF.
If you are using 10.10 you will be using grub2. Grub2 does not use menu.lst
To change the default boot option you should edit the line
GRUB_DEFAULT=0
in the file /etc/default/grub
as explained in the etc/default/grub section of this guide, by drs305

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Then run in the terminal```
sudo update-grub
```

---

### Post by degslon on 2011-01-18
Thank you for your help, it worked. It did take me a little effort to figure out how to edit the file, which I ended up editing in Kate.

---

### Post by Quackers on 2011-01-18
You're welcome :-)
You lost me there though, who's Kate?
Will you mark the thread as solved please, using the Thread Tools near the top of the page.

---

### Post by degslon on 2011-01-18
Basically, when I entered the /etc/default/grub into terminal it just gave me the message: > access denied
I searched for more info about Grub2 and found a thread which said that I needed to use an advanced console such as one called Kate to edit the file.

---

