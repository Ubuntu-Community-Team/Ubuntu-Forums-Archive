---
title: "APT network error"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by afmsouza on 2020-03-22
Hi, my Ubuntu installation just broken itself. When I try to run apt-get update it fails the network:
```

sudo apt-get update 
Obter:1 https://download.docker.com/linux/ubuntu cosmic InRelease [45,3 kB]
Atingido:2 http://storage.googleapis.com/bazel-apt stable InRelease                                                                                           
Atingido:3 https://repo.skype.com/deb stable InRelease                                                                                                        
Atingido:4 http://archive.canonical.com/ubuntu cosmic InRelease                                                                                               
Ign:5 http://archive.ubuntu.com/ubuntu cosmic InRelease                                
Ign:6 http://archive.ubuntu.com/ubuntu cosmic-updates InRelease
Ign:7 http://archive.ubuntu.com/ubuntu cosmic-backports InRelease
Ign:8 http://archive.ubuntu.com/ubuntu cosmic-security InRelease
Err:9 http://archive.ubuntu.com/ubuntu cosmic Release
  404  Not Found [IP: 91.189.88.142 80]
Err:10 http://archive.ubuntu.com/ubuntu cosmic-updates Release
  404  Not Found [IP: 91.189.88.142 80]
Err:11 http://archive.ubuntu.com/ubuntu cosmic-backports Release
  404  Not Found [IP: 91.189.88.142 80]
Err:12 http://archive.ubuntu.com/ubuntu cosmic-security Release
  404  Not Found [IP: 91.189.88.142 80]
Lendo listas de pacotes... Pronto
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
No matter what server I choose, all server are broken. But when I open it on browser it loads ok, also all those graphical update manager from ubuntu just fails too.

I just think it's unbeliveble apt-get don't create log and doesn't have a verbose option.

---

### Post by wildmanne39 on 2020-03-22
Cosmic reached End of Life on July 18, 2019 which means you can no longer run updates, it is best for you to do a fresh install of a supported Ubuntu version like 18.04.

---

### Post by guiverc on 2020-03-22
FYI:

[COLOR=#000000][FONT=Arial]Ubuntu 18.10 (cosmic) reached end-of-life on July 18, 2019.

[/FONT][/COLOR]It *release-upgraded* to Ubuntu 19.04, which you would have been prompted to do before then... however

[COLOR=#000000][FONT=Arial]Ubuntu 19.04 (disco) reached end-of-life on January 23, 2020.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
so the error has existed for some time, and your tested & supported upgrade path is also gone.

I'll provide [/FONT][/COLOR]https://help.ubuntu.com/community/EOLUpgrades  however I agree with @wildmanne39 and a re-install is likely your best option, and I suggest your maintain your system more regularly as that issue would have existed for a long time.

Consider using LTS or *long-term-support* releases if you don't like *release-upgrading* every 6-9 months that normal releases require.

---

### Post by afmsouza on 2020-03-22
ok, but why ubuntu-software update whatever the name of this graphical interface just can't  fix it and reset sources again without manual intervention. I deleted sources.list and create a new one.. and seens to work now. This is just ridiculous

---

