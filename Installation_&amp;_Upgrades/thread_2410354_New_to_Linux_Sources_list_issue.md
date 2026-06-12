---
title: "New to Linux Sources list issue"
date: 2019-01-14
forum: Installation &amp; Upgrades
---

### Post by jne14 on 2019-01-14
Hello I am having  some issued with my source.list aparently I made some mistakes from check multiverse on the GUI. When I type sudo apt-get update  this comes up after downloading  some other updates.

W: El objetivo Sources (multiverse/source/Sources) está configurado varias veces en /etc/apt/sources.list:51 y /etc/apt/sources.list:52
W: Omitiendo adquisición del archivo configurado «multiverse/source/Sources» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/binary-amd64/Packages» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/binary-i386/Packages» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/i18n/Translation-en» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/i18n/Translation-es» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/i18n/Translation-es_ES» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/dep11/Components-amd64.yml» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/dep11/icons-48x48.tar» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/dep11/icons-64x64.tar» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: Omitiendo adquisición del archivo configurado «multiverse/cnf/Commands-amd64» como repositorio «[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease» no tiene el componente «multiverse» (¿componente mal escrito en sources.list?)
W: El objetivo Sources (multiverse/source/Sources) está configurado varias veces en /etc/apt/sources.list:51 y /etc/apt/sources.list:52

---

### Post by Bashing-om on 2019-01-14
jne14; Hello - Welcome to the forum 

Looks like you have duplicated line 51 with a line 52 in the /etc/apt/sources.list file.

To confirm post back - Between code tags - the out put of terminal command:
```

cat -n /etc/apt/sources.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jne14 on 2019-01-14
> **Bashing-om said:**
> jne14; Hello - Welcome to the forum 

Looks like you have duplicated line 51 with a line 52 in the /etc/apt/sources.list file.

To confirm post back - Between code tags - the out put of terminal command:
```

cat -n /etc/apt/sources.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


    45    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security main restricted
    46    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
    47    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security universe
    48    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    49    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security multiverse
    50    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
    51    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic multiverse
    52    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic multiverse
    53    deb [http://archive.canonical.com/](http://archive.canonical.com/) cosmic partner
    54    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) cosmic partne

---

### Post by jne14 on 2019-01-14
Thank you Ive fixed it.

---

### Post by Bashing-om on 2019-01-14
jne14;Uh Huh -

confirmed:
> 
51 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic multiverse
52 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic multiverse


The terminal way to fix this:
Make a backup of  /etc/apt/sources.list - just in case of any mishap
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-14jan19

```
Fire up your favorite text editor with admin privileges and remove line 52. save the file and exit the editor.

Now what shows:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

