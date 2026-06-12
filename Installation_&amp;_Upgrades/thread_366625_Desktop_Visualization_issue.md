---
title: "Desktop Visualization issue"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Napu on 2007-02-21
Hi, ill try to explain my problem. First of all sorry ab my english

I boot from cd and instalation screen appears. I choose first option and when load ends my screen appears with a wrong display like this
[http://img72.imageshack.us/img72/9199/20022007036qm3.jpg]("http://img72.imageshack.us/img72/9199/20022007036qm3.jpg")

Rebot and then i choose safe mode, same issue ( with other colors )

i tried changing screen resolution with F4 menu, but still fails. Also i tried with the boot option "vga=771", same issue

I really dont understand, may u help me?

My rig
Amd Venice 250x10 HTT x4
Dfi Lanparty UT Ultra-D
2x512 Twinmos sp UTT
PNY 7800Gt 256mb
Lg l1730s

Trying to install Ubuntu 6.10 desktop amd64.

Now in spanish if one knows spanish, ill be better explained.

Una vez arrancado desde el cd me sale la pantalla de instalación, hasta ahi todo bien. Eligiendo la opcion de "iniciar o instalar ubuntu" tras el proceso de carga, la pantalla se muestra erroreamente, como cuando has elegido una resolución que no está soportada por la tarjeta gráfica o el monitor.

Después de este primer problema, elegí la opcion del "modo grafico seguro" obteniendo el mismo resultado ( pero con distinta visualización, colores diferente y aspecto parecido a la primera opcion.

Probé cambiando la resolucion con el F4, probe varias y obtuve el mismo resultado. Tambien añadí la opcion de arrange vga=771, obteniendo parecidos resultados.

Actualmente no se que hacer.

Estoy tratando de instalar el Ubuntu 6.10 desktop amd64
A parte os añado una foto que explica mejor como se queda la pantalla
[http://img72.imageshack.us/img72/9199/20022007036qm3.jpg](http://img72.imageshack.us/img72/9199/20022007036qm3.jpg)

---

### Post by aberry5555 on 2007-02-21
Try the following, I will use as little english as I can. Get to same place as in the picture, so that your screen looks bad and do this:

*Alt+Ctrl+F1*

A Console (a line to enter text) should show on the screen, type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will ask you what kind of graphics card you have, try and find a line that says "Nvidia". Next do this:

```
reboot
```

Hopefully this will load up Ubuntu.

Good luck!

---

### Post by gasull on 2007-02-21
Hi/Hola.

[Spanish below]  It seems that the Ubuntu installation doesn't recognize your graphics card or monitor.  First thing you need is to know exactly which graphic card and monitor you have.  There should be  some programs for either Linux or Windows that help you know your hardware.  Post the information here after you know it.

Parece que la instalación de Ubuntu no reconoce tu tarjeta gráfica o tu monitor.  Lo primero que necesitas es saber exactamente qué tarjeta gráfica y monitor tienes.  Debe haber varios programas tanto para Linux como para Windows que te ayudan a saber tu hardware.  Escribe aquí la información cuando la sepas.

Suerte/good luck.

---

### Post by aberry5555 on 2007-02-21
to Gasul, the PNY graphics card is Nvidia based, this is why I said to try the nvidia driver, also would you mind translating my post for him as I'm sure he will find it easier that way :)

thanks

---

### Post by Napu on 2007-02-21
hi again

aberry555:
With this code a screen appears that let me the posibility to select a resolution, not my card. I tried this again and i write wrong the "-phigh" option. A new screen prompt. this one give me a wizard to configure auto or manual the card. i choose nv and all default options that appears after. put the amount of memory in kb of the card and a lot of more information.
Then, it continues with the keyboard layout and mouse.

When i finished it a another screen let me the posibility of save configuration, i said yes.

Then "sudo reboot" and this screen appears and nothing can i do ( press enter with tray closed & cd out and nothing change )
[http://img329.imageshack.us/img329/619/21022007037kg3.jpg]("http://img329.imageshack.us/img329/619/21022007037kg3.jpg")

---

### Post by christhemonkey on 2007-02-21
Shutdown the computer (hold down the button on the front if needed) then switch it back on.

Are you saying that you havent installed ubuntu yet? And this is just the desktop cd you are booting?

In which case rebooting after changing xserver setup will not help as all changes will be lost.

Please again run the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg  
```

And then after you have finished selecting correct options. do this:
```
sudo /etc/init.d/gdm restart 
```

---

### Post by Napu on 2007-02-21
Hi

I tried this code again. Again its appears a screen for resolution select ( only resoluction select ). i flag 1024, 800 and 640, then press ok

I tried "sudo /etc/init.d/gdm restart". Stop gnome OK, init gnome fail.

Thanks for yours anwers

---

### Post by christhemonkey on 2007-02-21
Could you give us the error messages it gives?

If it does not display them, please do this and give the output:
```
cat /var/log/Xorg.0.log | less
```
Press <enter> or <down> to go down and press q to escape.

---

### Post by aberry5555 on 2007-02-22
Ok, I think you should try and install the nvidia accelerated drivers and see if that helps, because the nvidia drivers comes with automatic configuration scripts so it might help. Get to a terminal and type the following in:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx
```

There may be some settings to do when you install this so do that and then type in the following code:

```
sudo nvidia-xconfig
```

This will hopefully set up your graphics card properly, then do this to test:

```
sudo /etc/init.d/gdm restart
```

good luck!

---

### Post by Napu on 2007-02-22
Well, because i have these problems, i tried 6.06.1 & in safe graphics mode works for me. now im trying to install in a Raid system and i get some problems

I get dmraid package and create a partition with gpart. i tried in ext3 filesystem and install throw an error. i tried without format this partition and get same error.

Now im in windows ( bcause i need to do some things ) and i dont remember the exact problem but is kind a error with format options, the install stop at 15%

im following [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
but im a bit confused. it said that i only need to do 2 partition but i think i need 3. boot, root & swap. how many mb i need for each partition? i think 1gb for swap, whatever i want for root &  ??? for boot.

Thanks in advance

---

