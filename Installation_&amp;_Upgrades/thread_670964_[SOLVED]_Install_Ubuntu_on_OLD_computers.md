---
title: "[SOLVED] Install Ubuntu on OLD computers"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2008-01-18
Hello All,
In connection with a project "ReUsebe4ReCycle" I want to revitalize old computers and distribute them in our schools and make aware that there are alternatives to Windows.
My first OLDY, an ASUS-VX97, is probably some 8-10 years old and has the following specs - see attachment. I want to install Ubuntu6.06.It stared promising - see screenshots UbuntuLoad01-03, and then the loading stopped with the message; > ACPI: Unable to locate RSDP:confused:
Can any body tell me what that means and how I can get around it?

---

### Post by pebo on 2008-01-18
AFAIK ACPI is not supported on MoBos dating from before about 2001, so you could try the "acpi-off" boot option.
However your spec is a bit light for a graphical install - I couldn't do it on a PII 300mHz. Instead I did a server install using [this]("http://ubuntuforums.org/showthread.php?t=339029&highlight=icewm") howto.
You may find DSL or Puppy linux  better options for your spec.
Good luck!

---

### Post by Cariboo1938 on 2008-01-18
> **pebo said:**
> ..... so you could try the "acpi-off" boot option.
Thank you pebo, 
Please, could you give me an hint how to get to acpi-off option....?
I checked the BIOS and there I could not find a switch for that...
> **pebo said:**
> 
However your spec is a bit light for a graphical install - 
That's OK, i don't expect to get all the graphical features, I just want to build a basic machine...Internet browsing, music, text and pictures.......

---

### Post by Pumalite on 2008-01-18
With your RAM I'd stick to Xubuntu Alternate CD (remember you have integrated graphics eating at your RAM too)- [http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/)
Is that doesn't work then go with Puppy or DSL.

As for boot parameters, here is a guide and a collection to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

(You need at least 340 MB of ram to boot a Live CD)

---

### Post by pebo on 2008-01-18
When you get to the boot prompt when  booting off the cd, I think you just type it in there. Anyway if you hit f1 it gives you a help page which gives the info. 
If you are downloading the iso, definitely go for the alternate cd, it's a better bet on a low spec machine
Hmm, beaten to it...

---

### Post by FenderGuy2112 on 2008-01-18
Good luck with that old mobo.... I think you'll need a new one. :)

FenderGuy2112

---

### Post by wolfen69 on 2008-01-18
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Cariboo1938 on 2008-01-18
Thank you, Pumalite, pebo, wolfen69,
for now I have lots to do to work through all your supportive suggestions....thanks!
My first step will be to change the boot parameters.
I'll keep you posted...:)

---

### Post by Cariboo1938 on 2008-02-08
Hi,
I tried LinuxMint and had also the problem that the live CD didn't finish loading.
Then I tried VectorLinux and after some difficulties with the Logitech MouseMan Serial mouse I got the system installed and the GUI running. It is a nice System, not as versatile as Ubuntu, but at least some basics are running quite well.
I don't have the 56K USRobotics ISA modem (jumper setting COM3 and IRQ4) set up yet and I hope I'll get more information on that at the VL forums.
So, I thank all you great people who tried to help me and declare this thread as closed as far as Ubuntu is concerned.
Cariboo:)

---

