---
title: "Reinstallation of GitLab not working after apt purge ?"
date: 2021-12-01
forum: Installation &amp; Upgrades
---

### Post by gigi1335 on 2021-12-01
Hello,


I'm desperate to install Gitlab on my Ubuntu 20.04.3 LTS workstation.


I had done a first installation with :
> sudo apt install gitlab-ce

The problem is that I had forgotten to specify to use the local IP address (local installation of GitLab on my workstation).
So I removed gitlab with the commands :
> sudo gitlab-ctl stop
sudo gitlab-ctl uninstallsudo apt purge gitlab-ce
sudo rm -rf  /opt/gitlabsudo rm -rf  /etc/gitlab

The last 2 commands were necessary because the purge did not delete these 2 files.
I restarted the installation by specifying the access URL with my local IP:

> $ sudo EXTERNAL_URL="http://192.168.0.5" apt install gitlab-ce
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les NOUVEAUX paquets suivants seront installés :
  gitlab-ce
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/972 Mo dans les archives.
Après cette opération, 2637 Mo d'espace disque supplémentaires seront utilisés.
Sélection du paquet gitlab-ce précédemment désélectionné.
(Lecture de la base de données... 161281 fichiers et répertoires déjà installés.
)
Préparation du dépaquetage de .../gitlab-ce_14.5.0-ce.0_amd64.deb ...
Dépaquetage de gitlab-ce (14.5.0-ce.0) ...
Paramétrage de gitlab-ce (14.5.0-ce.0) ...
It looks like GitLab has not been configured yet; skipping the upgrade script.
...
Thank you for installing GitLab!
GitLab should be available at [http://192.168.0.5](http://192.168.0.5)

The installation seems to have gone well but no start of GitLab :
> $ curl [http://192.168.0.5](http://192.168.0.5)
curl: (7) Failed to connect to 192.168.0.5 port 80 after 0 ms: Connection refused
$ ps -eaf|grep gitlab
root      112548       1  0 09:47 ?        00:00:00 runsvdir -P /opt/gitlab/service log: oes not exist runsvdir /opt/gitlab/service: warning: unable to stat /opt/gitlab/service: file does not exist runsvdir /opt/gitlab/service: warning: unable to stat /opt/gitlab/service: file does not exist runsvdir /opt/gitlab/service: warning: unable to stat /opt/gitlab/service: file does not exist runsvdir /opt/gitlab/service: warning: unable to stat /opt/gitlab/service: file does not exist .
/etc/gitlab is present:> etc/gitlab$ ls -la
total 144
drwxr-xr-x   2 root root   4096 déc.   1 09:53 .
drwxr-xr-x 142 root root  12288 déc.   1 09:53 ..
-rw-------   1 root root 127748 déc.   1 09:53 gitlab.rbHow to restore /opt/gitlab and fix the Gitlab startup problem please?

Thanks in advance for your help.

Gilles

---

### Post by gigi1335 on 2021-12-03
Hi, 

I solved the problem by :

> sudo gitlab-ctl reconfigure

---

