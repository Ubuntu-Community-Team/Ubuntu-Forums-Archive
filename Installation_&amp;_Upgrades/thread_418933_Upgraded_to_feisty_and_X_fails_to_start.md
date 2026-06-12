---
title: "Upgraded to feisty and X fails to start"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by craz on 2007-04-22
I'm not sure what to do.  X is failing to start when I try to boot feisty and it asks me to manually fix it.  I am not sure what is wrong, the error says something about screens found but none are usable or something.  I changed X back to the default graphics driver and it still does not work.  What should I do?  I can't get onto ubuntu and I dont know where the X logs are saved.  Can anybody help?

---

### Post by carpex on 2007-04-22
Can you describe the details of your computer? Do you have an ATI card with widescreen resolution?

GL

---

### Post by craz on 2007-04-22
OK well I had a working Edgy installation and I upgraded to Feisty today through Update Manager.
My computer is:
Pentium 4
512 MB Ram
128 MB MX4000 graphics card
120 GB HD with partitions for / , /home , and swap
thats about it I guess...

---

### Post by craz on 2007-04-22
Does anybody know what I can do?  I'm stuck here and I need to run linux again!  Thanks!

---

### Post by craz on 2007-04-23
*bump*

---

### Post by craz on 2007-04-24
Anybody???

---

### Post by rocknrolf77 on 2007-04-24
You can try ```
sudo nvidia-xconfig
```

If that don't help you can try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Try the nv driver or the vesa driver. Maybe you have to reinstall the nvidia driver.

To start X you can do a ```
sudo /etc/init.d/gdm restart
```

---

### Post by craz on 2007-04-24
Following your advice I looked into the error more and I changed the PCI bus number to the one that was mentioned in the error and everything works like a champ now.  Thanks.

---

