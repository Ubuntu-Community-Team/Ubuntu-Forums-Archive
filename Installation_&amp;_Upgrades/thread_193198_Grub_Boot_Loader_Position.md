---
title: "Grub Boot Loader Position"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by Harley51 on 2006-06-09
I would like during install to have grub be on the first sector of the second hard drive but during install there's no chose to put on the second drive it puts it right on the MBR. Any help?

---

### Post by Rui Pais on 2006-06-09
hi,
try:
```
sudo grub-install /dev/hdb
```
assuming that you 2nd HD is /dev/hdb.

Or in the grub shell:
```
sudo grub
```
then on grub comand line:
```
setup (hd1)
```

good luck.

---

### Post by Harley51 on 2006-06-09
Thanks for the help. But I'm not understanding when this is suppose to happen. When I boot to the live CD. Then I install fron the desk top. I don't remember seeing a place to do this with auto parition???

---

### Post by Rui Pais on 2006-06-09
Oh sorry, 
i must misreading your post... get the idea that you have finished install been forced to install on 1st. disk.

If the installer didn't accept that option (strange i installed an ubuntu that way, boot on 2nd disk, but it was hoary i think... ) 

But i think that you should be able to run grub from live cd and do that commands. Skip then the grub MBR boot install phase on installation process.

Sorry i'm not a great expert on the install proccess. As i said i was thinking that you have already installed...

good luck

---

