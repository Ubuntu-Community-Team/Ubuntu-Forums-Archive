---
title: "Having trouble with Updates and Libreoffice"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by gongonni on 2013-04-13
Hi! I'm a "new" user, I have Ubuntu 12.04 - 32 Bit and I was adapting, changing and "furnituring" the ubuntu, everything was going OK, but one day, updating ubuntu got crashed... Now I have a "Forbiden" Sign in my upper bar. It says the next, more or less: 

"There was an error, run the Packet-Gestor or type apt-get -f install in console. The error's message: <<Error: Broken count >0 >> This normally means that you've installed packets which dependencies had not been satisfied"... (sorry for my english)

When I try to install again the updates, I've got this: "The next packets have got unsatisfied dependences: libreoffice-common: Depends: libreoffice-style but it's a virtual package"

I think it's because I installed many weeks ago LibreOffice, the last version (it doesn't appeared in Software Center yet, but I follow a little guide from internet and I have got it now)

Now, I follow the first message (with the forbbiden sign) and I open the Software Center. It pop-up a message "You cannot install or uninstall any package until the package's catalog is repared [...] Repair now?" I click on "REPAIR" and it crash... The message of this crash is:

installArchives() failed: dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-common (1:4.0.2~rc2-0ubuntu1~precise1) breaks libreoffice-emailmerge (<< 1:4.0.2~rc2) and is installed.
  Version of libreoffice-emailmerge to be configured is 1:4.0.2~rc1-0ubuntu1~precise2.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 libreoffice-emailmerge
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-common (1:4.0.2~rc2-0ubuntu1~precise1) breaks libreoffice-emailmerge (<< 1:4.0.2~rc2) and is installed.
  Version of libreoffice-emailmerge to be configured is 1:4.0.2~rc1-0ubuntu1~precise2.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured


I need your help, I'm too noob for this level on ubuntu! 8-[ I have no idea what to do... And I can't update or install anything else since this crash it's fixed.

Thank you guys!
__________________________________________________________
[COLOR=#ff0000]_**ESPAÑOL-SPANISH:**_[/COLOR]

Hola, soy un "nuevo" usuario de Ubuntu 12.04 - 32 Bit y estaba adaptando, cambiando y poniendo a mi gusto el S.O. cuando tuve un problema de actualización.Ahora tengo una señal de "prohibido" en la barra superior de la pantalla que dice lo siguiente:

"A ocurrido un error, ejecute el gestor de paquetes o apt-get -f install en la consola. El mensaje de error: <<Error: Broken count >0 >> Eso normalmente significa que hay instalado un paquete cuyas dependencias no se han satisfecho"

Cuando intento actualizar el SO, me lanza error: "Los siguientes paquetes no se han podido satisfacer: libreoffice-common: Depends: libreoffice-style pero es paquete virtual"

Creo que es porque hace tiempo instalé el LibreOffice, la última versión (cuando aún no aparecía en el Centro de Software, pero siguiendo una guía de internet, logré instalarlo)

Ahora, siguiendo el mensaje de error de la señal de prohibido, Abro el Centro de software y me aparece un mensaje: "No se puede instalar o desinstalar ningun programa hasta que se repare el catálogo de paquetes. Reparar ahora?" Le doy en "REPAIR" i falla otra vez... El mensaje de error es:

installArchives() failed: dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-common (1:4.0.2~rc2-0ubuntu1~precise1) breaks libreoffice-emailmerge (<< 1:4.0.2~rc2) and is installed.
  Version of libreoffice-emailmerge to be configured is 1:4.0.2~rc1-0ubuntu1~precise2.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 libreoffice-emailmerge
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-common (1:4.0.2~rc2-0ubuntu1~precise1) breaks libreoffice-emailmerge (<< 1:4.0.2~rc2) and is installed.
  Version of libreoffice-emailmerge to be configured is 1:4.0.2~rc1-0ubuntu1~precise2.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured


Necesito vuestra ayuda, pues soy muy novato para ello todavía! 8-[ Y no tengo ni idea qué hacer ahora. Tampoco puedo instalar o desinstalar nada... Ni siquiera actualizar. No almenos que lo repare.

Gracias chic@s!

---

### Post by gifford on 2013-04-13
So how did you install Libreoffice 4.0.2? Did you activate the ppa?

---

### Post by claracc on 2013-04-14
You can try in a xterm the command:

sudo apt-get -f install

Then , you introduce you password as required and answer Y to the questions.

---

### Post by gongonni on 2013-04-14
I don't know if I installed the ppa, I don't know what it means. I only follow a internet guide (which I'm unable to find it again :/ ) But I remember the installation was trough the terminal (or console). ¿How can I know if I installed the ppa?

I tried the sudo apt-get -f install and I get a error. Error number (1) or something like this.

Thanks for reply!

---

### Post by gifford on 2013-04-17
You would add it manually. Here is the code with the ppa:  [COLOR=#000000][FONT=UbuntuBeta Mono]sudo add-apt-repository ppa:libreoffice/ppa and then: [/FONT][/COLOR][COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get update
It will add the ppa and the try to install again.
[/FONT][/COLOR]First purge libreoffice with this: [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get purge libreoffice*
Then: [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install libreoffice[/FONT][/COLOR]

---

### Post by gongonni on 2013-04-19
Had no effect... :(
¿Is there any way to uninstall it using "hard force"?

thanks!
PD: ¿It would mean that I will have to reinstall ALL ubuntu for this reason?

---

### Post by gongonni on 2013-05-04
Solved!
I search and find out this instruction to uninstall ppa's. I don't know what I've done, but it works!

[FONT=Ubuntu Mono]sudo add-apt-repository --remove ppa:libreoffice-ppa/ppa 
sudo apt-get update[/FONT]

&#8203;then, via ubuntu software center, ask me for "repair" the broken repository (it always fails when I click "repair") but now, it works, and I uninstall every libreoffice that was installed via software center...

Time ago.. I though I saw an "official repository" in software center for LibreOffice 4.0, but I can't find it now.

Anyone knows if there is one?

¿Why there is no Libreoffice 4.0 in software center, but you can download via web? ¿how much time we'll have to wait for an "official" repository?

Thanks!

---

