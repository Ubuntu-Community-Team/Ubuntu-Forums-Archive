---
title: "busybox , ubuntu , usb flash"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by savalan86 on 2008-09-15
hi ,
i install ubuntu 8.4 on a flash disk from this article :
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/")

install and succesfully boot ubuntu from flash disk , like live cd 
but afew sec , show this for me :
```

busybox v1.1.3(debian 1:1.1.3-3 ubuntu 3)built-in shell(ash)
enter 'help' for a list of built-in commands

```

i search about this , often says this a hardware problem , 
( i test this in 3 different pc )
for example :
1 - says unplug hard drive and cdrom ( IDE's ) from pc and try : tried but not successfull
2 - says when first page on booting press F6 and type after -- :
```

all_generic_ide

```

i tried this , but not successfull

3 - after i pressed F6 , i delete  " quite splash " for view all jobs , but still give me same error ( busybox ) , but i take a photo from monitor , you can see here :
[http://i38.tinypic.com/bcrci.jpg]("http://i38.tinypic.com/bcrci.jpg")

you know , this issues is very very important for me , i dont have any laptop and in university i need linux ( ubuntu ).
only i have this way , if you help me ...
please !
thanks .

---

### Post by sriramin on 2008-09-19
Hi
Even I am facing the same problem. I did everything as mentioned in the pendrivelinux site. Also, I downloaded the initrd file too. Still I am getting the error as shown by the posted jpg file. I checked the casper.log which says : init .... no media found in /dev/scd0 something. I even kept a cdrom (ubuntu live cd) but same error. BTB I am using ubuntu 8.04.1

Hope some body can help. The livecd works great. I have a toshiba a100 sattellite 2214 laptop. All the hw is detected perfectly. The laptop has Vista Business. I dont have much HDD space. So I thought ubuntu on USB will be of great help. But I am really stuck

---

