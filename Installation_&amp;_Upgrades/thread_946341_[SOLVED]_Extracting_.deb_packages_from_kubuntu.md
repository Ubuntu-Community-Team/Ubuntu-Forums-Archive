---
title: "[SOLVED] Extracting .deb packages from kubuntu"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by prabath_fun on 2008-10-13
Hi,
   I have got Kubuntu 8.04 installed. 
   Is it possible to get .deb packages of some of the applications, etc., from fresh / installed Kubuntu.
   Say, I want to extract kde-desktop or kwrite or etc., package from Kubuntu and use it in Ubuntu.
  Please help me, how to do it?
With advanced Thanks,
[COLOR="Purple"]Prabath[/COLOR]

---

### Post by alynx on 2008-10-13
I have installed kde programs on ubuntu and the other way around by going into the terminal and using apt-get.

for instance if you write apt-cache search kde in your ubuntu terminal you should find it.

---

### Post by caljohnsmith on 2008-10-13
I agree with alynx; I think the best way would be to just download and install the packages in Ubuntu either using Synaptic Package Manager or "sudo apt-get install <package>" from the command line. You could look in your /var/cache/apt/archives directory in your Kubuntu install and see if the .deb packages you want are there. Or if you have your Kubuntu Live CD, maybe the .deb files you want would be on there somewhere; you would have to search the CD.

---

### Post by prabath_fun on 2008-10-13
Hi,
   Since, I have very low speed net connection, I could not able to download with help of apt-get or aptitude or synaptic. 
   Further, I have Live CD only. I came to know that, from Live CD it is not possible to install kde-desktop itseems.
   So, what, I want to know, whether, Is it possible to get .deb packages of KDE packages from Kubuntu installations.
   Please update me.
With Thanks,
[COLOR="Blue"]Prabath[/COLOR]

---

### Post by zvacet on 2008-10-13
You can try this

1. make iso from your CD

```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=/home/username/image.iso
```

Then read [this.]("http://ubuntuforums.org/showthread.php?t=743943")

When iso is added to the synaptic run

```
sudo apt-get install kubuntu-desktop
```

---

### Post by prabath_fun on 2008-10-15
Hi,
   I tried making ISO and mounting with command "mount" and checked at mount point. I got same content as in CD. No deb packages. 
   If there is any other way, please...........
[COLOR="Blue"]Prabath[/COLOR]

---

### Post by zvacet on 2008-10-15
> I got same content as in CD.

That is a point.Promblem with Live Cd is that you can not install u/k/x desktops.That is possible with alternate CD.That is why I suggested you to do it in way I described.

---

### Post by prabath_fun on 2008-10-17
hi,
   So, I am considering that With Live CD it is not at all possible to install kubuntu-desktop.
With Thanks,
Prabath

---

### Post by element_G on 2008-10-19
you can tell synaptic to use a live cd as a package repository 

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

is what my old sources.list had for the Kubuntu 7.10 live CD

---

### Post by prabath_fun on 2008-10-26
HI,

  After my long search, i came to know that live cd can be used to install only few packages, which are not embedded for live bootup. 

Prabath

---

### Post by zvacet on 2008-10-26
To install kubuntu-desktop you need** alternate CD** or install via net 

```
sudo apt-get install kubuntu-desktop
```

---

### Post by prabath_fun on 2008-10-28
Yes, zvacet. This is my final conclusion.
[COLOR="RoyalBlue"]Prabath[/COLOR]

---

