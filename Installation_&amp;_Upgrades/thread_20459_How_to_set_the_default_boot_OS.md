---
title: "How to set the default boot OS"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by Volvere on 2005-03-16
hi,

I have successfully installed UBuntu in my slave HD. Everything is working fine now. However, I use Windows more than UBuntu at the moment and UBuntu is the first on the GRUB list. How to make Windows back as the default boot OS?

Thanks

---

### Post by bored2k on 2005-03-16
[QUOTE=Volvere]hi,

I have successfully installed UBuntu in my slave HD. Everything is working fine now. However, I use Windows more than UBuntu at the moment and UBuntu is the first on the GRUB list. How to make Windows back as the default boot OS?

Thanks[/QUOTE]
 [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

---

### Post by bonifacio on 2005-03-17
X_sequence didn't change my default OS so it seems  :-k

---

### Post by Volvere on 2005-03-17
Thanks bored2k, I'll try it tonight.

---

### Post by Volvere on 2005-03-17
[QUOTE=bonifacio]X_sequence didn't change my default OS so it seems  :-k[/QUOTE]

I suppose X_sequence means the list index which determines the OS position. So, 0 is the first OS in the list, while 1 is the second and so forth.....

---

### Post by bored2k on 2005-03-17
[QUOTE=Volvere]I suppose X_sequence means the list index which determines the OS position. So, 0 is the first OS in the list, while 1 is the second and so forth.....[/QUOTE]
 If you guys are running hoary grubconf is the perfect GUI tool for you all .

With a single click you can edit this AND add graphical boot easily and harmlessly :D .

---

### Post by noelferg on 2005-03-24
[QUOTE=bored2k]If you guys are running hoary grubconf is the perfect GUI tool for you all .

With a single click you can edit this AND add graphical boot easily and harmlessly :D .[/QUOTE]

How do you run grubconf in Hoary?   :confused:

---

### Post by bonifacio on 2005-03-24
sudo boot-admin?

at least thats what I use in one of my machine with a Gentoo distro.

---

### Post by noelferg on 2005-03-24
[QUOTE=bonifacio]sudo boot-admin?

at least thats what I use in one of my machine with a Gentoo distro.[/QUOTE]


 sudo boot-admin brings up a Command not found response

---

### Post by bored2k on 2005-03-27
[QUOTE=noelferg]How do you run grubconf in Hoary?   :confused:[/QUOTE]
 sudo grubconf .

Oh and you need to install it first [sudo apt-get install grubconf or "synaptic it" ] .

---

