---
title: "Keep Windows 7 Boot Menu"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by ramakanta on 2014-05-03
I have install Ubuntu 12.04 inside the windows (Win 7) , when stated this black and white boot menu appears 

[[IMG]http://s19.postimg.org/b3wwruy3j/bootmenu2.jpg[/IMG]]("http://postimg.org/image/b3wwruy3j/")
then uninstalled the Ubuntu.

but when direct  installed with other partition ,I think after that Ubuntu boot menu overwrite the win7 boot menu and following  boot menu displayed .

[[IMG]http://s19.postimg.org/8lb7r6cdb/bootmenu1.jpg[/IMG]]("http://postimg.org/image/8lb7r6cdb/")

is there  any procedure to keep win 7 boot menu (black & white)  when the  installing  Ubuntu with other partition ???. need help ???
thank you.

---

### Post by oldfred on 2014-05-03
If you uninstalled wubi, you should not get any Windows boot menu. And you get the standard grub menu with both Ubuntu and Windows.

Windows does not know about Linux, so will not boot it without several work arounds and third party Windows boot tools. You also have to cripple grub by converting it to blocklists or hard coded addresses. 

Best to just use grub2 as boot manager.

---

### Post by ramakanta on 2014-05-15
Today I have install Ubuntu 14.04 ( install inside windows 7 ) . after completion ,and restarted , then , I have seen the GNU BRUB boot loader 2.02 bete.  how ?? previously was not happened in 10.04 , which is windows boot loader  , please help ????

---

### Post by Mark Phelps on 2014-05-16
WUBI is not supported anymore.  I'm surprised it worked at all with 14.04.  

You need to consider using a stand-alone Ubuntu installation instead of Wubi.

---

