---
title: "Webcam?"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by athenix on 2007-04-26
Hi!

I have a PC, HP Pavilion dv9000 with kubuntu.
Some one so know how we install webcam driver, or?
- The webcam is insidebuild.

---

### Post by diskotek on 2007-04-26
there is a similar model here:

[http://ubuntuforums.org/showthread.php?t=421880&highlight=how+to+webcam](http://ubuntuforums.org/showthread.php?t=421880&highlight=how+to+webcam)

---

### Post by athenix on 2007-04-26
Also. I'm not so good with Linux, so i need little bit more information and that. Can some one help?

Hp Pavilion dv9000 - Kubuntu?

---

### Post by loell on 2007-04-26
first plug your webcam, and in the terminal/ command line

type the command

```
lsusb
```

and post the results here

---

### Post by athenix on 2007-04-26
Here:

Bus 005 Device 003: ID 05ca:1870 Ricoh Co., Ltd
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 03f0:171d Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c012 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by loell on 2007-04-26
it seems, it can't be seen as a usb device,  is this a usb webcam?

whats the brand name and model?

---

### Post by athenix on 2007-04-26
I have a inside build webcam, so only i know is that the webcam driver has the name Hp pavilion Webcam, this information is the only information i found out of hp.no :/

---

### Post by loell on 2007-04-26
found this but its in french

[http://doc.ubuntu-fr.org/materiel/liste_portables/hewlett-packard/dv9001ea#etape_6_installation_de_la_webcam_integre_sonix]("http://doc.ubuntu-fr.org/materiel/liste_portables/hewlett-packard/dv9001ea#etape_6_installation_de_la_webcam_integre_sonix")

google translate

[http://google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fliste_portables%2Fhewlett-packard%2Fdv9001ea%23etape_6_installation_de_la_webcam_integre_sonix&langpair=fr%7Cen&hl=en&ie=UTF8]("http://google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fliste_portables%2Fhewlett-packard%2Fdv9001ea%23etape_6_installation_de_la_webcam_integre_sonix&langpair=fr%7Cen&hl=en&ie=UTF8")

in the webcam ricoh section.

---

### Post by loell on 2007-04-26
wait , looking at the output maybe, its already detected

you can install camorama, run it, and see if your webcam shows up.

---

### Post by athenix on 2007-04-26
I have allready download it :)

Buut... I get this follow message: " No detected Video osv.. "

---

### Post by athenix on 2007-04-26
> **loell said:**
> found this but its in french

[http://doc.ubuntu-fr.org/materiel/liste_portables/hewlett-packard/dv9001ea#etape_6_installation_de_la_webcam_integre_sonix]("http://doc.ubuntu-fr.org/materiel/liste_portables/hewlett-packard/dv9001ea#etape_6_installation_de_la_webcam_integre_sonix")

google translate

[http://google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fliste_portables%2Fhewlett-packard%2Fdv9001ea%23etape_6_installation_de_la_webcam_integre_sonix&langpair=fr%7Cen&hl=en&ie=UTF8]("http://google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fliste_portables%2Fhewlett-packard%2Fdv9001ea%23etape_6_installation_de_la_webcam_integre_sonix&langpair=fr%7Cen&hl=en&ie=UTF8")

in the webcam ricoh section.

I have tryed.. but.. in "kubuntu" this one:

*****@****:~$ Cd r5u870-0.9.0/make sudo make install sudo modprobe r5u870
bash: Cd: command not found

---------------------------------------------------------------------------

I dont understand!?

---

### Post by loell on 2007-04-26
i guess you will have to compile the driver then. just follow those instructions.

you must have build-essential in order to compile from source.
```
sudo apt-get build-essential
```

---

### Post by athenix on 2007-04-26
it's dosent work :/

---

### Post by loell on 2007-04-26
> **athenix said:**
> I have tryed.. but.. in "kubuntu" this one:

*****@****:~$ Cd r5u870-0.9.0/make sudo make install sudo modprobe r5u870
bash: Cd: command not found

---------------------------------------------------------------------------

I dont understand!?

it should be ```
cd r5u870-0.9.0/make sudo make install sudo modprobe r5u870
```

notice the small cd

---

### Post by athenix on 2007-04-26
Okei, i have fix the cam, but what is the best prg for kubuntu to take pictures with it?

---

### Post by loell on 2007-04-26
i'm not aware of a KDE/Kubuntu program for webcam, but you can just use camorama and xawtv for taking pictures.

---

### Post by athenix on 2007-04-27
Hmm, allready try it..

Canorama doesn't work in Kubuntu.
Same with xawtv :/

---

### Post by loell on 2007-04-27
its the webcam, xawvt and camorama is indepent from kubuntu/ubuntu/xubuntu.

in command line do

```
lspci
```

and post it,
also 

```
lsmod
```

also post it.

---

