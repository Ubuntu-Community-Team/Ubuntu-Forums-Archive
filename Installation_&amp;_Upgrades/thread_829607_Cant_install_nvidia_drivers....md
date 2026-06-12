---
title: "Cant install nvidia drivers..."
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by Merc84TD on 2008-06-15
Iv been trying to install the 173.14.05 drivers for the 9600gt, but it never works. It downloads fine, but terminal says that the downloaded file cant be opened.

kyle@kyle-desktop:~$ sudo sh NVIDIA-Linux-x86-173.14.05.pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.05.pkg1.run
kyle@kyle-desktop:~$

---

### Post by PmDematagoda on 2008-06-15
Make the file executable with:-
```
sudo chmod +x NVIDIA-Linux-x86-173.14.05.pkg1.run
```
and try running the file again.

---

### Post by Merc84TD on 2008-06-15
I got kyle@kyle-desktop:~$ sudo chmod +x NVIDIA-Linux-x86-173.14.05.pkg1.run
[sudo] password for kyle:
chmod: cannot access `NVIDIA-Linux-x86-173.14.05.pkg1.run': No such file or directory
kyle@kyle-desktop:~$ 

But the file is and directory are deffinatly there

---

### Post by PmDematagoda on 2008-06-15
Post the output of:-
```
ls
```

---

### Post by logos34 on 2008-06-15
You can't simply run it in an xterminal on the desktop

Personally, I'd recommend you install the latest nvidia driver with Milone's [EnvyNG script]("http://www.albertomilone.com/nvidia_scripts1.html") just to make sure it goes in correctly with the right headers, restricted kernels, etc.

If you must do it manually with the interactive binary installer, you'll have to first drop to the console and kill the x server:

alt+ctrl+F1

sudo /etc/init.d/gdm stop

then cd over to the same dir as the driver and run

sudo sh NVIDIA-Linux-x86-173.14.05.pkg1.run

when done run

sudo nvidia-xconfig

sudo /etc/init.d/gdm start

ctrl+alt+F7

I think that's how it goes--been a while since I did the manual install

---

### Post by PmDematagoda on 2008-06-15
You can run the installer even while running an X-Server, it just won't run completely and will stop, that's all. And you are right, why don't you(the OP) try to install the Nvidia drivers using Envy and see if that fixes it?

---

### Post by logos34 on 2008-06-15
> **PmDematagoda said:**
> You can run the installer even while running an X-Server, it just won't run completely and will stop, that's all.

right, it won't work, spits out warnings, etc, IIRC (a year+ ago for me)...Nor does it like to be installed in recovery mode (which didn't prevent me from trying once--and succeeding!)

---

### Post by PmDematagoda on 2008-06-15
> **logos34 said:**
> Nor does it like to be installed in recovery mode (which didn't prevent me from trying once--and succeeding!)

In what way didn't it like Recovery Mode?

---

### Post by logos34 on 2008-06-15
it throws a warning, or else nvidia docs recommend not to do so...can't remember exactly.  I just know I was surprised when I succeeded, and even more surprised when it worked afterwards flawlessly.

---

### Post by PmDematagoda on 2008-06-15
> **logos34 said:**
> it throws a warning, or else nvidia docs recommend not to do so...can't remember exactly.  I just know I was surprised when I succeeded, and even more surprised when it worked afterwards flawlessly.
Really? Well, I installed the Nvidia driver in Recovery Mode almost all the time, but it never gave up any errors and it worked properly. Don't know how that might have been different in your case.

---

### Post by logos34 on 2008-06-15
well, as I said it has been over a year (edgy to feisty upgrade), so I guess I read it in nvidia docs or some other official source/guide

---

### Post by Merc84TD on 2008-06-15
Thanks everyone for you help but im still having some trouble.

I realize that I cant install  the drivers without shutting down the x-server, but that isn't the problem. I cant even open the downloaded file to start the installation. When using terminal i get "sh: Can't open NVIDIA-Linux-x86-173.14.05-pkg1.run"

 When i double click in the downloaded file, and open it with gedit the get an error saying " could not open the file home/kyle/documents/NVI.....           gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I cant use envy because it doesnt have the drivers that i need "173.14.05"

---

### Post by Merc84TD on 2008-06-15
Wow, i would like to say that i feel like and idiot. All i needed to do was use cd to change the file directory. Thanks for everyones help.

---

### Post by Pooka2132 on 2008-06-15
Just in case anyone else is as dense as me last night and can't figure this one out, heres what made mine work step by step.

download the nvidia driver to the desktop.
Ctrl+Alt+F1
login
sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NVIDIA*
when this is finished...
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
Ctrl+Alt+F7

yay finally more than 800x600 resolution and the nvidia splash at boot.

All of this knowlede is here from other posters in this and many other threads its just sometimes I (and others) need it spelled out to the letter.

Pooka

---

