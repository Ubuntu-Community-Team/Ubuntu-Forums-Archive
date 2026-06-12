---
title: "gfxboot"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by benste on 2008-02-15
I tried ["http://ubuntuforums.org/showthread.php?t=540446"]("http://ubuntuforums.org/showthread.php?t=540446")
gfxboot does work fine, but there are still Problems while updating (not only kernel), can someone help me?


```
benste@vaio-fe-31m:~$  sudo apt-get dist-upgrade
[sudo] password for benste:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Berechne Upgrade...Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Es müssen 0B Archive geholt werden.
Nach dem Auspacken werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Richte linux-image-2.6.22-14-generic ein (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: Fehler beim Bearbeiten von linux-image-2.6.22-14-generic (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by benste on 2008-02-23
Still no help?

---

### Post by benste on 2008-02-23
I guess that grub-update doesn't work anymore (it is automaticly launched after update)

---

### Post by Pumalite on 2008-02-23
Run this and post the output:
sudo dpkg --configure -a

---

### Post by benste on 2008-02-23
thank you for helping me
```
benste@vaio-fe-31m:~$ sudo dpkg --configure -a
Richte linux-image-2.6.22-14-generic ein (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: Fehler beim Bearbeiten von linux-image-2.6.22-14-generic (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 linux-image-2.6.22-14-generic

```

---

### Post by Pumalite on 2008-02-23
Run this and post the output:
sudo apt-get install -f

---

### Post by benste on 2008-02-23
```
benste@vaio-fe-31m:~$ sudo apt-get install -f
[sudo] password for benste:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Es müssen 0B Archive geholt werden.
Nach dem Auspacken werden 0B Plattenplatz zusätzlich benutzt.
Richte linux-image-2.6.22-14-generic ein (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.47 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: Fehler beim Bearbeiten von linux-image-2.6.22-14-generic (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Pumalite on 2008-02-23
You might need to force remove a package half installed:
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.22-14-generic
And then reinstall.

---

### Post by benste on 2008-02-23
I'll do what you say (also rm- rf * which we learned at school :-))

Failed with the following messaage:
```
benste@vaio-fe-31m:~$ sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.22-14-generic
[sudo] password for benste:
dpkg: Abhängigkeitsprobleme verhindern Entfernen von linux-image-2.6.22-14-generic:
 linux-ubuntu-modules-2.6.22-14-generic hängt ab von linux-image-2.6.22-14-generic.
 linux-image-generic hängt ab von linux-image-2.6.22-14-generic.
 linux-restricted-modules-2.6.22-14-generic hängt ab von linux-image-2.6.22-14-generic.
dpkg: Fehler beim Bearbeiten von linux-image-2.6.22-14-generic (--remove):
 Abhängigkeitsprobleme - entferne nicht
Fehler traten auf beim Bearbeiten von:
 linux-image-2.6.22-14-generic

```

---

### Post by Pumalite on 2008-02-23
You will have to reinstall unless some guru or staff member comes up with a better answer.

---

### Post by benste on 2008-02-23
Reinstall the whole system - I'll do this when 8.04 is stable but than I don't have gfxboot anymore

---

### Post by Pumalite on 2008-02-23
sorry. Hopefully someone wiser will come up with an answer.

---

### Post by benste on 2008-02-23
Thanks for looking into my post (no one else did for 1 week)

---

### Post by benste on 2008-02-23
Still someonethere who can help me?

---

### Post by excogitation on 2008-04-07
Did you try abandoning gfxboot?

---

### Post by altaaa on 2008-04-07
Check the file /sbin/update-grub.

If the file's first line is[FONT="Courier New"] #!/bin/sh[/FONT] , try changing that in [FONT="Courier New"]#!/bin/bash[/FONT]

Maybe it helps.

See this thread:
[http://ubuntuforums.org/showthread.php?t=208855&page=57](http://ubuntuforums.org/showthread.php?t=208855&page=57)

---

### Post by benste on 2008-04-08
Good idea, I'll try this later,
currently I'musing 8.04 so it will be difficult, and I've to install the package first

---

### Post by excogitation on 2008-04-08
Seems as if that did the trick.

---

