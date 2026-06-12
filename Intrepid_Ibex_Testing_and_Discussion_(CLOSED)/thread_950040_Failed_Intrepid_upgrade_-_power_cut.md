---
title: "Failed Intrepid upgrade - power cut"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scotthammy on 2008-10-16
Hey Everyone, well I was upgrading my install from 8.04 and I had a power cut, how can I recover my install? 

it has downloaded everything and was about 1/2 way into installing files..

---

### Post by nanog on 2008-10-16
If you have command line access try:

```
sudo do-release-upgrade -d
```

and/or 
```
sudo apt-get update && sudo apt-get dist-upgrade 
```

if the upgrade works you can 

```
sudo apt-get autoremove && sudo reboot
```


**if you do not have cli access you need to chroot:**

1. Boot up a live cd, or separate linux install.

2. Mount your hardy drive somewhere (replace **** with name of borked linux partition, e.g. hda1 or sda1 etc.)

```

sudo mkdir /media/intrepid
sudo mount /dev/**** /media/intrepid
##(mount your borked intrepid)


sudo chroot /media/hardy su
##(chroot into your gutsy drive.)
##(sudo not required)

sudo nano /etc/apt/sources.list
##make sure your sources are commented out or converted to intrepid

apt-get update
##(and perhaps "dpkg-configure -a" if apt complains)

apt-get upgrade

apt-get dist-upgrade

apt-get dist-upgrade 
##(one more time just to be safe)

```

ctrl+d or type "exit" to exit the chroot, then reboot the computer and you should be able to get back into intrepid.


Sometimes there will be no Internet connection in the chroot environment.

To correct this, before the chroot we have to enter:
sudo cp /etc/resolv.conf /media/intrepid/etc/resolv.conf


Source: from pricechild sticky in dev branch and originally posted by yanns.

---

### Post by ronacc on 2008-10-16
if something was being written at the time the power failed you may have a corrupt drive , you should run fsck on it before doing anything else .

---

