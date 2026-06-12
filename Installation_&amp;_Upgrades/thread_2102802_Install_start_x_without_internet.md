---
title: "Install start x without internet"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by caleb12134 on 2013-01-08
;):p:popcorn::KS:mad:How do you install start x on ubuntu ***_server _***without internet connection from a flashdrive using sudo commands. Can you give me a link to the xinit download file and the list of commands. :guitar::lolflag:):P

---

### Post by ibjsb4 on 2013-01-08
There are several ways to do that.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+offline&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+offline&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by caleb12134 on 2013-01-08
I know i have it on usb but how do i install it????? Ive been using sudo apt-get install /media/CALEB/xinint.deb and it gives me the error it cant find the package??:D

---

### Post by steeldriver on 2013-01-08
You will need to use dpkg

```
dpkg -i *packagename*.deb
```apt-get is for installing things from a repository

---

### Post by caleb12134 on 2013-01-10
But now it says unknown option 1?? i had to manually mount the drive????

---

### Post by steeldriver on 2013-01-10
Did you maybe type a number 1 instead of the lower case letter i?

```
 dpkg [SIZE=4][COLOR=Red]-i[/COLOR][/SIZE] packagename.deb
```USB drives will usually auto mount under the /media directory so you will need to look there

FYI you will need MUCH more than just the xinit package to start an X session if you are beginning from the standard Ubuntu Server install

---

### Post by caleb12134 on 2013-01-10
Now its saying this requires superuser privilege?????

---

### Post by Bufeu on 2013-01-10
> **caleb12134 said:**
> Now its saying this requires superuser privilege?????
Just type *sudo* in front of dpkg then...?

---

### Post by caleb12134 on 2013-01-10
now it says error proccessing file no such file or directory??

---

### Post by Bufeu on 2013-01-10
> **caleb12134 said:**
> now it says error proccessing file no such file or directory??
Then, you are typing the wrong filepath to the .deb file. It should be:
```
sudo dpkg -i /path/to/file.deb
```

---

### Post by caleb12134 on 2013-01-10
so it should be sudo dpkg -i /Econ/xinit.deb 
the flash drives name is "Econ" and the package is xinit.deb
so what would it look like with the following info plugged in

---

### Post by Bufeu on 2013-01-10
> **caleb12134 said:**
> so it should be sudo dpkg -i /Econ/xinit.deb 
the flash drives name is "Econ" and the package is xinit.deb
so what would it look like with the following info plugged in
It would be that, if you mounted the USB at */Econ*, otherwise it is mounted at */**media**/Econ*, or something.

---

### Post by caleb12134 on 2013-01-10
so the usb name is "Econ" and the file name is xinit.deb and this is a new server and new install of ubuntu. We set it up to the sudo command. and we arent approved for internet access so i downloaded the file on a flashdrive. so what should it look like with the following info i listed??

---

### Post by Bufeu on 2013-01-10
> **caleb12134 said:**
> so the usb name is "Econ" and the file name is xinit.deb and this is a new server and new install of ubuntu. We set it up to the sudo command. and we arent approved for internet access so i downloaded the file on a flashdrive. so what should it look like with the following info i listed??
Well, that depends on where the USB is mounted.

---

### Post by caleb12134 on 2013-01-10
what goes in the /to/ spot?

---

### Post by Cheesemill on 2013-01-11
Can you take a step back for a minute and tell us exactly what you are trying to achieve.

Trying to install the xinit .deb package by itself from a USB stick isn't going to work, first you need to install all of its [dependencies]("http://packages.ubuntu.com/precise/xinit"). But all of those packages need their dependancies installing first as well, and so on, and so on.

This is why Ubuntu machines really should have an internet connection, without it you have to spend hours manually tracking down, installing, and keeping packages up to date. This is not the way it was designed to be used. If you had an internet connection on your machine you could do all of this hard work automatically with one simple command...
```
sudo apt-get install xinit
```

Even if you do manage to sort out all of these dependancies and install xinit, it isn't any use by itself, xinit is just used to initialise whatever graphical user interface you have installed.

Also there is a good argument for not installing a GUI on a server in the first place. All of the configuration of services on a Ubuntu server is done by editing text files, this can be done just as easily from the command line. Also having a GUI uses up system resources unnecessarily and provides a bigger surface for attackers.

---

### Post by caleb12134 on 2013-01-11
I really need a GUI on the server. Can you guys help me install it? what do i need. all we need to run is a webserver and mail server. We are gonna host the schools sites and club sites and we need emails.  we also need to know how to set up the firewall and encryption.

---

### Post by Cheesemill on 2013-01-11
You have a lot of learning ahead of you, I would recommend starting by reading through the official Ubuntu Server documentation.

[https://help.ubuntu.com/12.04/index.html](https://help.ubuntu.com/12.04/index.html)

Make sure you read the sections titled Installation, Package Management, Security, Web Servers, LAMP Applications and Email Services.

There are also plenty of good tutorials online, Googling for something like 'ubuntu server 12.04 lamp' will get you started.

Why do you need a GUI? As I mentioned earlier all of the configuration of a Ubuntu server is done by editing text files, which is just as easy without a GUI. Having a GUI uses unnecessary resources and provides a much larger attack surface for people trying to compromise your machine.

Also you mention that you don't have authorisation to connect this server to the internet, without internet connectivity it is impossible to set up a mail server or a web server.

---

### Post by Elfy on 2013-01-16
Thread closed. Please do not post duplicates, it dilutes community effort.

---

