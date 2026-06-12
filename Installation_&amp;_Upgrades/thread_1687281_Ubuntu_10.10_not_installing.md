---
title: "Ubuntu 10.10 not installing"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by dordo3 on 2011-02-13
Currently, I am not able to install ubuntu from my usb, to my usb. When I try to click the "Install Now" Icon on the "Allocate Drive Space" screen, it says that there is no root file defined. Currently, the box above the text is blank, and I am not able to install the operating system. Help?

---

### Post by sikander3786 on 2011-02-13
Welcome to the forums :-)

No root file system defined error means that you are doing a manual partition and have not defined mount points for partitions. See here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Feel free to ask if you've got further queries.

---

### Post by dordo3 on 2011-02-13
The page i'm on is nothing like the pages shown in the link. This is the page I cannot currently get past.

---

### Post by dordo3 on 2011-02-13
I also currently have Windows installed on the harddrive also in the computer, but it is unplugged in order to not be a victim of any mistakes.

---

### Post by sikander3786 on 2011-02-13
You have disconected one of your HDDs but the other one, to which you intend to install Ubuntu is not being detected either. Check for any lose connections, unplugged drive cables.

Also, please post the output of this command from Applications > Accessories > Terminal

```
sudo fdisk -lu
```

---

### Post by dordo3 on 2011-02-13
I cannot install to the usb in which i want to install from?

---

### Post by sikander3786 on 2011-02-13
> **dordo3 said:**
> I cannot install to the usb in which i want to install from?
Not at all. If you intend to install it to a USB, you need to boot from a CD or some other USB. Same USB can't be used both as source and the destination.

---

### Post by dordo3 on 2011-02-13
OH :p Sorry. I didn't understand. I'll be right along then. Thanks for the help!

---

### Post by sikander3786 on 2011-02-13
> **dordo3 said:**
> OH :p Sorry. I didn't understand. I'll be right along then. Thanks for the help!
No problem. You are most Welcome :-)

---

