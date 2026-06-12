---
title: "Reinstall xp help"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by miko16 on 2008-10-12
hi, im new here, need help. i canot understand the other threads about this, and im having this kind of problem. my xp goes nuts, im using a grub 1.5 loader. i can select my 2 os. first is the ubuntu, then other os is the xp. how can i reinstall my xp? i installed the both of them in different HDD, but, reinstalling the xp may have a problem with my ubuntu os? what should i do? :( thanks peeps

---

### Post by sokopok on 2008-10-12
If you reinstall Windows, it will overwrite your boot sector, so make sure you have your ubuntu cd at hand to be able to boot you Ubuntu to revert this process.
When windows is installed, reboot using your Ubuntu CD, and follow these instructions: [http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)

---

### Post by miko16 on 2008-10-12
ok bro. thanks for the help. :popcorn:

---

### Post by miko16 on 2008-10-13
> **sokopok said:**
> If you reinstall Windows, it will overwrite your boot sector, so make sure you have your ubuntu cd at hand to be able to boot you Ubuntu to revert this process.
When windows is installed, reboot using your Ubuntu CD, and follow these instructions: [http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)


hi.still this not works. this is what i did

i entered sudo grub
then password

after that i wrote in this key. grub>root (hdo

is says error..

---

### Post by sokopok on 2008-10-13
Start Grub:
```
sudo grub
```Tell Grub on which partition the /boot directory is located (If you created a separate boot partition during install of Ubuntu, that's the one, otherwise it is your root partition). Grub starts counting from 0, so first harddisk, first partition is (hd0,0); first harddisk, second partition (hd0,1) and so on.
```
root (hd[COLOR=DarkOrange]0[/COLOR],[COLOR=DarkOrange]0[/COLOR])
```Install Grub to MBR harddisk (again Grub starts counting from 0):
```
setup (hd[COLOR=DarkOrange]0[/COLOR])
```You should adapt everything in [COLOR=DarkOrange]orange[/COLOR] to suit your needs.

Are you using Ubuntu 8.10 intrepid? Cause I just tried these commands and autocompletion with the TAB key as suggested in the article i posted does not work for me. Maybe that's why you got confused. I'll have to file a bugreport for that.

---

