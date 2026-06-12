---
title: "Upgrading trouble!"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by user_cero on 2006-07-25
Well, i was happily upgrading my ubuntu dist from 5.10 to 6.06 but suddenly in the paradise(Dominican Republic), we got a black-out...

I was upgrading from the cd just as the [documentation]("https://help.ubuntu.com/community/DapperUpgrades#head-1596eecf4b58a03b3d9f44172a661382f8065a58") says:

#

To install from a physical CD

   1.

      Run:
          *

     sudo apt-cdrom add 

            Insert the CD, and press enter.
   2.

      Run:
          *

     sudo apt-get update && sudo apt-get dist-upgrade 

then the computer began to update..... but when there were like 3 minutes left... the black out!

Now when i try to upgrade the 5.10 it says:

crismar@ubuntu:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se han retenido:
  cpp cpp-4.0
0 actualizados, 0 se instalarán, 0 para eliminar y 2 no actualizados.

crismar@ubuntu:~$ sudo apt-get dist-upgrade
reading pkg list..done
creating tree of dependencies...done
calculating update..done
the following pkg have been kept:
cpp cpp-4.0
0 update, 0 will be installed, 0 to delete y 2 not updated

Then i run sytem update a it says the same thing and tells me to mark all updates on synaptic. I go to synaptic check all repositories are ok, mark all updates but it still doesn't work.

I also:

Ensure all necessary packages are completely installed and configured by issuing these commands (via ALT+F2 if necessary):

  sudo apt-get -f install
  sudo dpkg --configure -

What should i do?:confused: Please help me!

---

