---
title: "Error on migration from Ubuntu 23.10 to 24.04 LTS"
date: 2024-08-10
forum: Installation &amp; Upgrades
---

### Post by loulou92 on 2024-08-10
Hello, 
I am new user on Linux Administration.
I am trying to update from 23.10 to 24.04.
I got the following message  by using **sudo do-release-upgrade**

Vérification du gestionnaire de paquets
Lecture des listes de paquets… Terminé
Construction de l'arbre des dépendances… Terminé
Lecture des informations d'état… Terminé        
Att [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) mantic InRelease                                  
Att [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) mantic-updates InRelease                          
Att [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) mantic-backports InRelease                        
Att [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) mantic InRelease                             
Att [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                                     
Att [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security InRelease                           
[COLOR=#ff0000]Ign [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) mantic InRelease                                  
Err [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) mantic Release                                    
  404  Not Found [IP : 2620:2d:4000:1003::111 80]        [/COLOR]                                 
0  o réceptionnés en 0s (0  o/s)                                                          
Lecture des listes de paquets… Terminé          
Construction de l'arbre des dépendances… Terminé
Lecture des informations d'état… Terminé  

Thanks in advance if you can help to solve this problem

---

### Post by TheFu on 2024-08-10
Support for 23.10 ended. The repos are probably gone. 23.10.  You waited too long.  End of support means end of support.  Migrate to a new OS BEFORE that happens.

You can try to install 24.04.1 over the existing install.  That will leave some cruft behind.
If you want the cleanest install, format everything and do a fresh 24.04.1 install.  Of course, you should backup everything you don't want to lose BEFORE doing this.  Not just the data, but the file metadata like the owner, group, permissions, ACLs, and xattrs too. Any good backup tool will do that.  Don't just copy files off. That isn't sufficient for system files. It might be sufficient for your personal data files in your $OME directory.  Your choice if you want to risk it.

---

### Post by loulou92 on 2024-08-11
Hi TheFu,
Thanks for you reply and proposal.

---

### Post by loulou92 on 2024-08-14
I update my post because i was able to migrate from 23.10 to 24.04 LTS thank to the French Ubuntu forum.
The problem only resides with [COLOR=#ff0000][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [/COLOR]mantic InRelease                                  


[COLOR=#ff0000]
[/COLOR]

---

