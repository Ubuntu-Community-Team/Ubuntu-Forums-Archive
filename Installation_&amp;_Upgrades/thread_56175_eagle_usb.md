---
title: "eagle usb"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by mozz10844 on 2005-08-11
Default eagle usb
right. ive unpacked it to my desktop so its:
/home/moz/Desktop/eagle
now how the hell do i install the thing.if i put in
/home/moz/Desktop/eagle/install-sh
then this happens
install: no input file specified
im using a sagem fast 800 840 modem.

---

### Post by coolclassic on 2005-08-11
There is a lot of help within these forums to install this software and to get the modem working. Use the search facilty to search for sagem fast modem.

If you still have problem after reading the posts just ask.

---

### Post by mozz10844 on 2005-08-11
still having trouble buddy,can you just guide me through from what ive told you there please.

---

### Post by coolclassic on 2005-08-11
Have you installed the drivers using synaptic or or did you try to install tar file.

---

### Post by mozz10844 on 2005-08-11
i downloaded the one off the website and burnt it to a disc in windows

---

### Post by coolclassic on 2005-08-11
Where did you download from did you use debian files or what???
and what type of file did you down load?

---

### Post by mozz10844 on 2005-08-11
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)
from there
.tar.bz2?

---

### Post by coolclassic on 2005-08-12
The file you will need is here:
[http://mcoolive.free.fr/eagle-usb/](http://mcoolive.free.fr/eagle-usb/)

This has been prepared for use on debian systems.

Save this in your home directory, then in your shell use the following commands.

sudo apt-get remove --purge eagle-usb-*

sudo cp eagle-usb-1.9.8.tar.gz /usr/local/src 
sudo cd /usr/local/src

sudo tar xvzf eagle-usb-1.9.8.tar.gz 
sudo cd eagle-usb-1.9.8

sudo ./configure 
sudo make uninstall 
sudo make clean
sudo make 
sudo make install

eagleconfig

Hopefully all has gone well you should now do in a shell.

sudo startadsl

and to stop

sudo stopadsl

---

### Post by mozz10844 on 2005-08-12
[http://mcoolive.free.fr/eagle-usb/](http://mcoolive.free.fr/eagle-usb/)

which one?

 eagle-1.0.4e.tar.bz2    
eagle-1.9.1.tar.gz      
eagle-1.9.2.tar.bz2    
eagle-1.9.3.tar.bz2     
eagle-1.9.4.tar.bz2     
eagle-1.9.5.tar.bz2     
eagle-1.9.6.tar.bz2     
eagle-usb-1.9.8.tar.bz2

??????????????????????????????? :-|
ive noticed you put sudo cp eagle-usb-1.9.8.tar.gz  but thats not one on there,thus confusing me of which to download and what to type in terminal.please tell me the correct one to get  ](*,)

am i right in thinking  eagle-usb-1.9.8.tar.bz2  ????

---

### Post by coolclassic on 2005-08-12
Yes your correct.

sudo is the command you use to get root access and is put infront of many commands.

---

### Post by mozz10844 on 2005-08-12
just that you put .tar.gz    :???:

---

### Post by mozz10844 on 2005-08-12
sudo apt-get remove --purge eagle-usb-*

sudo cp eagle-usb-1.9.8 /usr/local/src (had to change name)

then it dont work after there.
so fix it for me please.

---

### Post by coolclassic on 2005-08-13
The file name used must be the full name of the file including .tar.gz.

---

