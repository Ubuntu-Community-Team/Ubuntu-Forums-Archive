---
title: "ubuntu en msi bios raid"
date: 2017-12-03
forum: Installation &amp; Upgrades
---

### Post by drakomagno on 2017-12-03
Español/Spanish.
Hola a todos,
Laptop: MSI GT72s 6QE Dominator pro G.
O.S.: Win10 pro.
Hard Disk: 1TB x1.
SSD: 128GB x2.

Resulta que el sistema esta instalado en RAID, pero la RAID esta echa desde la BIOS, uniendo el almacenamiento de los dos SSD, por lo que no me deja instalar Ubuntu 17.04, mis preguntas son las siguientes.

1.- ¿Alguna forma de poder instalar Ubuntu?
2.- Si elimino el RAID, supongo que el Win10 no arrancara y podre instalar un Win en un SSD y Ubuntu en otro SSD, dejando el HHDlibre.

Espero que me puedan ayudar, estaré atentos a sus comentarios.
Saludos.

Ingles/English (Traductor Google/Google translator).
Hello everyone,
Laptop: MSI GT72s 6QE Dominator pro G.
O.S .: Win10 pro.
Hard Disk: 1TB x1.
SSD: 128GB x2.


It turns out that the system is installed in RAID, but the RAID is thrown from the BIOS, joining the storage of the two SSD, so it does not let me install Ubuntu 17.04, my questions are as follows.


1.- Any way to install Ubuntu?
2.- If I delete the RAID, I suppose the Win10 will not start and I could install a Win in an SSD and Ubuntu in another SSD, leaving the HHDfree.


I hope you can help me, I will be attentive to your comments.
Greetings.

---

### Post by oldfred on 2017-12-03
IF RAID 0, then half of system is on one drive and half on other drive in alternating stripes (if hard drive, not sure exactly with SSD).
So if you turn RAID off you destroy system. But you should be able to fully back up system and then restore. But not idea of details and potential issues.
RAID 0 offten used to make for faster system, but Internet and user typing is not any faster. And newer NVMe drivers are faster still. And very good backups are required.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Some similar MSI systems. Issues are often common by vendor across models.

 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)

---

### Post by gtenzo7sr on 2018-08-03
Hola. grato encontrar a alguien que hable español. Soy totalmente nuevo en ubuntu y mi primer encuentro ha sido muy bueno, pero como toda buena experiencia tiene su
aprendizaje, el ubuntu dejo de correr; trate de reinstalar y ahora no me reconoce el dvd ni el boot por usb. Y no tengo ni idea de como proceder. Si alguien pudiera darme una orientación estaría agradecido.

---

### Post by oldfred on 2018-08-03
This is an English site.
There are several sub-forums that speak Spanish and local Ubuntu forums in most countries.
[https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183)

---

