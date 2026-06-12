---
title: "Upgrade Ubuntu to Xfce environment using Xubuntu ISO image"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by enpakkam on 2008-07-11
please help me how to upgrade ubuntu to Xfce environment without using internet connection 

how to upgrade by using Xubuntu ISO (xubuntu-8.04-desktop-i386.iso) image.

---

### Post by sdennie on 2008-07-11
```

sudo apt-cdrom add
sudo apt-get install xubuntu-desktop

```

---

### Post by enpakkam on 2008-07-11
> **vor said:**
> ```

sudo apt-cdrom add
sudo apt-get install xubuntu-desktop

```
My combo cd drive is not working properly, how to use with USB pen drive?

---

### Post by powerpleb on 2008-07-11
Maybe you could mount the ISO
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_an_.iso_file](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_an_.iso_file)

then follow vor's instructions

---

### Post by enpakkam on 2008-07-11
i have mounted ISO image into /media/cdrom

then i executed the command  "sudo apt-cdrom add"

it asks to insert the cdrom.

how to use this "apt" command to add our mounted path ?

---

### Post by sdennie on 2008-07-11
If you know where the USB drive is mounted, you could try:

```

sudo apt-cdrom -d=/place/where/usb/drive/is/mounted

```

I have no idea if that will work but, it's worth a try.

---

### Post by enpakkam on 2008-07-11
hi vor, thanks for your input.

but it is not worked.

any other way to upgrade XFCE environment on ubuntu? without using internet connection.

---

### Post by SkonesMickLoud on 2008-07-11
You could try extracting the .iso to "/var/cache/apt/archives" and then running:

```
sudo apt-get install xubuntu-desktop
```

No guarantees that this will work though...

---

