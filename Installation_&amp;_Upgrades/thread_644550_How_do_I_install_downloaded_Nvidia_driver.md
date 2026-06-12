---
title: "How do I install downloaded Nvidia driver?"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Quakindude on 2007-12-19
I downloaded the current driver for Linux 64-bit for the 8800GTS from Nvidia. What do I do with it now? It's sitting on the desktop and obviously, I don't just double click it. 

Can someone please help me to get this driver installed? I'm completely new to Ubuntu and know very little about how to do much. But I would appreciate anyones help!

---

### Post by logos34 on 2007-12-19
are you sure the nvidia restricted driver (100.14.19) won't suffice?

---

### Post by Sef on 2007-12-19
> are you sure the nvidia restricted driver (100.14.19) won't suffice?

System > Administration > Restricted Drivers Manager

---

### Post by wolfen69 on 2007-12-19
system>administration>restricted drivers manager

---

### Post by PmDematagoda on 2007-12-19
First kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

Then navigate to where the file is found and do:-

```
sudo sh nameofinstaller
```

After installation do:-

```
sudo /etc/init.d/gdm start
```

@ logos34:- The reason could be because the Restricted Drivers Manager may not be able to install the drivers for the 8800 cards properly since it seems a lot of people have problems with those cards when using RDM.

---

### Post by kpkeerthi on 2007-12-19
See this link for additional packages you might need for the manual install:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by Quakindude on 2007-12-19
> **PmDematagoda said:**
> First kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

Then navigate to where the file is found and do:-

```
sudo sh nameofinstaller
```

After installation do:-

```
sudo /etc/init.d/gdm start
```

@ logos34:- The reason could be because the Restricted Drivers Manager may not be able to install the drivers for the 8800 cards properly since it seems a lot of people have problems with those cards when using RDM.

I'm a total Linux noob bro. I don't know what you mean.

I assume in the first part, kill the GUI, I just open a terminal window and type that in?

When you say navigate to, it's on the desktop. Am I again using the terminal window and if so, how do I navigate to the desktop area?

I've always used Windows, but want to move away from M$. I'm familiar with Windows DOS from the old days, and I'm sure the terminal window is a lot like that, I just don't know the file structure yet, so need some help in that area.

The RDM does offer a driver, however, I've already tried that route and it doesn't work for the 8800GTS. That's why I'm trying to get the driver from Nvidia installed. 

Thank you folks very much for your help.

---

### Post by PmDematagoda on 2007-12-19
> I assume in the first part, kill the GUI, I just open a terminal window and type that in?

When you kill the GUI you are brought to a full terminal with no GUI at all.

> When you say navigate to, it's on the desktop. Am I again using the terminal window and if so, how do I navigate to the desktop area?

You can use:-
```

cd Desktop
```

Once there do(l being simple letter l not the number 1):-

```
ls
```
to list the contents which will make it easier for you to do:-
```

sudo sh nameofinstaller
```
nameofinstaller being the name of the file.

That should be enough. A tip though, the more used you are to the terminal the more you can use Linux and the more you can rescue it from sticky situations.

---

### Post by b1o on 2007-12-19
I have done exactly this. and when i start the xserver again. my screen is white... i have the mouspointer. but the screen is white. any1 have any idea?

---

### Post by PmDematagoda on 2007-12-19
Post the specifications of your PC.

And when you face the white screen press Ctrl+Alt+F1 to get to a terminal. Once there do:-

```
sudo /etc/init.d/gdm stop
```
and
```
sudo dpkg-reconfigure xserver-xorg
```

Select the driver as Nvidia and any others you may want. Once that is done, do:
```

sudo /etc/init.d/gdm start

```

---

