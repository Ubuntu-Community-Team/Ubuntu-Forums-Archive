---
title: "cant fully update edgy, synaptic broken"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by jesterthejedi on 2006-10-24
Help!

I did the standard upgrade to edgy. it was downloading all the packages ok. then on the install it failed on writing to /usr/X11R6/bin, its said something about having files in there that needed to be removed. I removed them and tried to update again. it said i had a broken package, i ran apt-get install -f, and then used synaptic to fix the broken dependency. then i tried the update, it downloaded 1042 files, and then errored out. i can post the errors but it wont copy the synaptic window. HELP!

---

### Post by jesterthejedi on 2006-10-24
I get this bad message too:

(gedit:10444): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",

It seems as this error is stopping all updates in synaptic. i have te repositories for edgy listed, but none of the updated files are installed. I have 1042 files waiting to be installed.

---

### Post by jesterthejedi on 2006-10-24
more errors in synatic:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)

---

### Post by fatdaddy on 2006-10-24
> **jesterthejedi said:**
> more errors in synatic:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)

I too am getting the same errors in synaptic.  However during the upgrade from dapper to edgy I saw something about a broken api in apt.    Also going to /var/lib/apt/lists I cannot find any duplicate entries unless I click go to the partial folder.  Should that folder be deleted or will i break apt?

---

### Post by friviere01 on 2006-11-02
More errors, no idea on what to do, here is output to sudo apt-get install -f:

S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'estan corregint les dependències... Fet
The following packages were automatically installed and are no longer required:
  webmin-mailboxes webmin-inetd webmin-core webmin-proftpd webmin-samba
  webmin-grub webmin-burner
Use 'apt-get autoremove' to remove them.
S'ELIMINARAN els següents paquets:
  webmin-burner webmin-core webmin-grub webmin-inetd webmin-mailboxes
  webmin-proftpd webmin-samba
0 actualitzats, 0 nous a instal·lar, 7 a eliminar i 4 no actualitzats.
7 no instal·lats o eliminats completament.
Es necessita obtenir 0B d'arxius.
Després de desempaquetar s'alliberaran 14,1MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 174501 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant webmin-burner ...
/var/lib/dpkg/info/webmin-burner.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-burner (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
/var/lib/dpkg/info/webmin-burner.postinst: line 4: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en netejar:
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-grub ...
/var/lib/dpkg/info/webmin-grub.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-grub (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-core ...
/var/lib/dpkg/info/webmin-core.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-core (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-mailboxes ...
/var/lib/dpkg/info/webmin-mailboxes.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-mailboxes (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-samba ...
/var/lib/dpkg/info/webmin-samba.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-samba (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-inetd ...
/var/lib/dpkg/info/webmin-inetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-inetd (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'està desinstal·lant webmin-proftpd ...
/var/lib/dpkg/info/webmin-proftpd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: s'ha produït un error en processar webmin-proftpd (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 webmin-burner
 webmin-grub
 webmin-core
 webmin-mailboxes
 webmin-samba
 webmin-inetd
 webmin-proftpd
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-ca (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_i18n_Translation-ca)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-ca (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_i18n_Translation-ca)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-ca (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_i18n_Translation-ca)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Potser voldreu executar apt-get update per a corregir aquests problemes
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

