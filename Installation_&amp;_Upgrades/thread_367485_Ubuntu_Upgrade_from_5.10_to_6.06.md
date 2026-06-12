---
title: "Ubuntu Upgrade from 5.10 to 6.06"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by paulozzzz on 2007-02-22
Greetings, people.

I am trying to upgrade my system from the **Ubuntu 6.06 Alternate Install CD**, following the instuctions in [this site]("https://help.ubuntu.com/community/DapperUpgrades#head-1596eecf4b58a03b3d9f44172a661382f8065a58").

All steps went through until I ran the following command:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

Which yielded lines and lines of errors:

```

Err http://security.ubuntu.com dapper-security Release.gpg
  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Err http://wine.budgetdedicated.com dapper Release.gpg
  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper Release.gpg
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Ign http://security.ubuntu.com dapper-security Release
Ign http://wine.budgetdedicated.com dapper Release
Err http://br.archive.ubuntu.com dapper-updates Release.gpg
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Ign http://br.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://br.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://br.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://br.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Ign http://br.archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Ign http://br.archive.ubuntu.com dapper/main Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Ign http://br.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Ign http://br.archive.ubuntu.com dapper/multiverse Packages
Ign http://br.archive.ubuntu.com dapper-updates/main Packages
Ign http://br.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://br.archive.ubuntu.com dapper-updates/main Sources
Ign http://br.archive.ubuntu.com dapper-updates/restricted Sources
Err http://br.archive.ubuntu.com dapper/main Sources
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper/restricted Sources
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper/universe Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper/main Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper/restricted Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper/multiverse Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Ign http://wine.budgetdedicated.com dapper/main Sources
Err http://br.archive.ubuntu.com dapper-updates/main Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://wine.budgetdedicated.com dapper/main Packages
  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper-updates/restricted Packages
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://wine.budgetdedicated.com dapper/main Sources
  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper-updates/main Sources
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Err http://br.archive.ubuntu.com dapper-updates/restricted Sources
  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Falha ao baixar http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Falha ao baixar http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Falha ao baixar http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i386/Packages.gz  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Falha ao baixar http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Falha ao baixar http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Não foi possível conectar em security.ubuntu.com:80 (82.211.81.138). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://br.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Não foi possível conectar em br.archive.ubuntu.com:80 (200.17.202.1). - connect (111 Conexão recusada)
Falha ao baixar http://wine.budgetdedicated.com/apt/dists/dapper/main/source/Sources.gz  Não foi possível conectar em wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Conexão recusada)
Lendo Lista de Pacotes... Pronto
E: Alguns arquivos de índice falharam no download, eles foram ignorados ou os antigos foram usados em seu lugar.

```

Translations:

*Não foi possível conectar em <URL>* = Unable to connect to <URL>.

*Conexão recusada* = Connection refused

*Alguns arquivos de índice falharam no download, eles foram ignorados ou os antigos foram usados em seu lugar.* = Some index files failed during download, they have been ignored or the older ones were used in their place.

Of course the upgrade attempt went wrong because no activity occurred in the CD-ROM drive.  Judging from the error messages, the package manager is trying to access the **internet** to retrieve the packages, which is strange since I want to upgrade using the **CD**!

Please, I need help as my system is now in a halfway state between two versions!

---

### Post by pay on 2007-02-23
```
sudo apt-cdrom add
```

---

### Post by paulozzzz on 2007-02-23
> **pay said:**
> ```
sudo apt-cdrom add
```

Thank you, pay, but it only added the CD-ROM as a new repository.

I still don't know how to perform the upgrade to 6.06 using **just the CD**.  My problem is that the network administrator blocked downloads larger than 20MB, so I CAN'T perform the upgrade via Internet.

---

### Post by pay on 2007-02-23
Well if the cd is added to your sources list then apt should realise that the cd has newer version of the software that you are trying to install and then install those. Try commenting out every other entry apart from the cdrom one and then ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by paulozzzz on 2007-02-24
> **pay said:**
> Well if the cd is added to your sources list then apt should realise that the cd has newer version of the software that you are trying to install and then install those. Try commenting out every other entry apart from the cdrom one and then ```
sudo aptitude update
sudo aptitude dist-upgrade
```

Pay, what you said is rather logical and is what I understood about the APT behavior.

Chances are I did something wrong.  I will try to undo what I did before and resume.

---

### Post by paulozzzz on 2007-02-25
Pay, indeed, after rolling back some steps, I was able to upgrade to 6.06 using your instructions.:)

---

