---
title: "Jockey crashes and messes up the drivers"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mnox on 2008-10-09
I downloaded and installed Nvidia drivers, but jockey crashed during the installation and after that Ubuntu fails to boot into desktop. I only get a black screen with text asking to log in and if I log in, I can use the terminal commands. So, how should I restore the desktop (or more likely remove the driver which is probably broken and causing this)?
PC: Amd Sempron 3000+ 64 bit
    Nvidia 8600GT 512MB
    Ubuntu Intrepid 64 bit.

---

### Post by plun on 2008-10-09
From terminal

```
sudo apt-get install nvidia-glx-177
```

Was this a clean beta install ?  Jockey is upgraded after beta release.

---

### Post by mnox on 2008-10-09
This was a clean beta install and unfortunately after typing:

sudo apt-get install nvidia-glx-177

I got a message that a newest version is already installed and I still can't get to the desktop.

---

### Post by plun on 2008-10-09
Ok...try this

```
sudo apt-get install --reinstall linux-image-2.6.27-6-generic
```

Reboot

A kernel install/reinstall triggers DKMS detection which is now used for drivers

---

### Post by mnox on 2008-10-09
It got even worse. Everything froze at:
*enabling additional executable binary formats binfmt-support [ ok ]
*checking battery state... [ ok ]
By the way, what battery? I'm not using a laptop.

---

### Post by plun on 2008-10-09
Then you must update your install
```

sudo apt-get update


sudo apt-get upgrade
```


Upgrade can be done with other options but try that first.

---

### Post by mnox on 2008-10-09
It still freezes at:

*checking battery state... [ ok ]

---

### Post by plun on 2008-10-09
Well, this is difficult.....

Probably a kernel bug

Change boot options

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20On%20An%20Existing%20Ubuntu%20System](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20On%20An%20Existing%20Ubuntu%20System)


acpi=off   would I try.


Maybe other have more ideas....

---

### Post by mnox on 2008-10-09
Nothing new happened. System froze at the same spot.

---

### Post by plun on 2008-10-09
> **mnox said:**
> Nothing new happened. System froze at the same spot.

Well, your PC boots but Gnome freezes   ?

One bug I found

[https://bugs.launchpad.net/ubuntu/+bug/277587](https://bugs.launchpad.net/ubuntu/+bug/277587)

Launchpad search

[https://launchpad.net/+search?field.text=Checking+battery+state](https://launchpad.net/+search?field.text=Checking+battery+state)


I have no more ideas howto solve this.... :(  Sorry..

---

