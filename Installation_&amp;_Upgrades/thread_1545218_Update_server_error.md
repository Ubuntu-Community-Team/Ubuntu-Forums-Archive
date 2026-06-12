---
title: "Update server error"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Belteshazzar on 2010-08-03
Hello,
I'm running Ubuntu 10.04 in French and updates no longer seem to be working. I keep getting the following error message:

> Échec du téléchargement de tous les fichiers d'index

Le dépôt ne semble plus être disponible ou ne peut être contacté à cause de problèmes de réseau. S'il existe un fichier d'index plus ancien, il sera utilisé. Sinon, le dépôt sera ignoré. Vérifiez votre connexion réseau et corrigez l'adresse du dépôt dans les préférences.

English:

[I]Failure to download all the index files
The 'depot' no longer seems to be available or cannot be contacted due to network problems. If there is an older index file, it will be used. If not, the 'depot' will be ignored. Check your network connection and correct the 'depot' address in the preferences.[/I]

The terms *dépôt* and *fichier d'index* mean almost nothing to me in this context; I suspect *dépôt* might be "repository" in English though I am not sure.

I am pretty sure there is no problem with the network as I can access all other functionalities. I don't know however how I can change the *dépôt* address if I don't know what it is / which "preferences" it is talking about (unless it means MAC address in the network prefs?)

The issue could be the proxy, squid, which I am using in conjunction with DansGuardian. I don't have enough technical knowledge to fix it however. (I suspect it will be quite a simple problem that I have just misjudged)

The following error code is displayed beneath that message:

```
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2  Le sous-processus /bin/bzip2 a renvoyé un code d'erreur (2)
Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
```

I would be very grateful for any help anyone could give me.

---

### Post by lechien73 on 2010-08-03
You are correct that *dépôt* refers to repositories. *Fichier d'index* are the repository index files.

I had this problem once when updating from the Ireland server. It was solved for me by going to System > Administration > Software Sources and changing "Download From" to "Main Server".

Clicking the "Close" button then reloaded all the repository indexes, and it worked fine. I later switched back to Ireland to ease the load on the main servers.

If you still get the problem, then could it actually be something to do with your Internet connection? Are you accessing via a proxy or through a corporate network? Could the Ubuntu update servers be blocked somehow?

---

### Post by Belteshazzar on 2010-08-06
Thanks, changing the server to "main server" solved the problem. The issue was probably that I had it set to the French server even though I am not in France at the moment. Solved!

---

