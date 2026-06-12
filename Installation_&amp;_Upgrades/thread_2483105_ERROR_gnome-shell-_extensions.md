---
title: "ERROR gnome-shell- extensions"
date: 2023-01-20
forum: Installation &amp; Upgrades
---

### Post by leoxavi3r on 2023-01-20
Hi,

I want macOS theme

So I followed these steps < [https://itslinuxfoss.com/how-to-apply-macos-theme-on-ubuntu-22-04/](https://itslinuxfoss.com/how-to-apply-macos-theme-on-ubuntu-22-04/) >

But this command line
sudo apt install gnome - shell - extensions

back this error:

The gnome - shell - extensions package is not available, but is referenced by another package.
This may mean that the package is missing, has become obsolete, or
is available only from another source


E: The gnome - shell - extensions package has no candidate for installation

---

### Post by #&amp;thj^% on 2023-01-20
do you have this installed:
```
apt policy gnome-shell-extension-manager
```

---

### Post by leoxavi3r on 2023-01-20
i think no

> apt policy gnome-shell-extension-manager
gnome-shell-extension-manager:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de versão:


---

### Post by leoxavi3r on 2023-01-20
sorry quotes in portuguese but
same error than extensions

> sudo apt-get install gnome-shell-extension-manager
[sudo] password for leoxavier: 
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
O pacote gnome-shell-extension-manager não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'gnome-shell-extension-manager' não tem candidato para instalação

---

### Post by #&amp;thj^% on 2023-01-20
Try this please:
```
sudo apt install inxi
```
it's a system monitoring tool-cli
Now show us the return from this:
```
inxi -r

```

---

### Post by leoxavi3r on 2023-01-20
sorry the same thing

> sudo apt install inxi
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
O pacote inxi não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'inxi' não tem candidato para instalação

---

### Post by #&amp;thj^% on 2023-01-20
something very wrong with your install,,,,
show this:
```
cat /etc/apt/sources.list
```
and 
```
cat /etc/os-release
```

---

### Post by deadflowr on 2023-01-20
```
sudo add-apt-repository universe
sudo apt update 
sudo apt install gnome-shell-extensions
```

Edit: realize I deleted what i wrote outside the code block, so

Most likely universe is not enabled.
the above command will enable it and allow installing packages from that repository.

---

### Post by leoxavi3r on 2023-01-20
leoxavier@leoxavier:~$ cat /etc/apt/sources.list
## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

leoxavier@leoxavier:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
leoxavier@leoxavier:~$

---

### Post by leoxavi3r on 2023-01-20
leoxavier@leoxavier:~$ sudo add-apt-repository universe
Adding component(s) 'universe' to all repositories.
Press [ENTER] to continue or Ctrl-c to cancel.
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Atingido:2 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Lendo listas de pacotes... Pronto        
                  
leoxavier@leoxavier:~$ sudo apt update 
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Atingido:2 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
All packages are up to date.

leoxavier@leoxavier:~$ sudo apt install gnome-shell-extensions
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
O pacote gnome-shell-extensions não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

**E: O pacote 'gnome-shell-extensions' não tem candidato para instalação**

sorry continue the same

---

### Post by #&amp;thj^% on 2023-01-20
you show absolutely no Sources, before following deadflowr post will you run this and show us
```
sudo apt update
```

---

### Post by leoxavi3r on 2023-01-20
sudo apt update
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Atingido:2 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Lendo listas de pacotes... Pronto                          
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
All packages are up to date.

---

### Post by #&amp;thj^% on 2023-01-20
your missing some key source's
```
sudo nano /etc/apt/sources.list
```
make your list read like below:
```
deb http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu/ jammy partner
# deb-src http://archive.canonical.com/ubuntu/ jammy partn

```
Please have a quick check for duplicates, and remove those *only*
now:
```
sudo apt update 
sudo apt upgrade
```

---

### Post by deadflowr on 2023-01-20
No sources? hmm.
There should be a default sources.list in /usr/share/doc/apt/examples.
Copy it to /etc/apt like so
```
sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/
``` 
then re-run the commands I posted before.

(The default sources.list file only has the main and restricted repositories enabled, so you need to add the universe repository.)

Edit: Ninja'd

Though there is no need to add the partner repository since it is now empty or basically useless.
(The only package it had was for the adobe-flashplugin, but that just an installer script to grab flash from adobe, which no longer provides it,
so it's pretty much a package without a country)

---

### Post by leoxavi3r on 2023-01-20
> **1fallen said:**
> your missing some key source's
```
sudo nano /etc/apt/sources.list
```
make your list read like below:
```
deb http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu/ jammy partner
# deb-src http://archive.canonical.com/ubuntu/ jammy partn

```
Please have a quick check for duplicates, and remove those *only*
now:
```
sudo apt update 
sudo apt upgrade
```

this is working wait a minute

---

### Post by leoxavi3r on 2023-01-20
all done 1fallen lets try the commands deadflowr talked about wait a minute

---

### Post by leoxavi3r on 2023-01-20
> **deadflowr said:**
> ```
sudo add-apt-repository universe
sudo apt update 
sudo apt install gnome-shell-extensions
```

Edit: realize I deleted what i wrote outside the code block, so

Most likely universe is not enabled.
the above command will enable it and allow installing packages from that repository.


leoxavier@leoxavier:~$ sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/
leoxavier@leoxavier:~$ sudo add-apt-repository universe
sudo apt update 
sudo apt install gnome-shell-extensions
Adding component(s) 'universe' to all repositories.
Press [ENTER] to continue or Ctrl-c to cancel.
Added universe to: deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute main restricted universe
Added universe to: deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute main restricted universe
Added universe to: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security main restricted universe
Added universe to: deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security main restricted universe
Added universe to: deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates main restricted universe
Added universe to: deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates main restricted universe
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security InRelease                                                           
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute InRelease                                                                  
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security Release                        
  404  Not Found [IP: 185.125.190.36 80]
Ign:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates InRelease
Atingido:6 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute Release
  404  Not Found [IP: 91.189.91.39 80]
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates Release
  404  Not Found [IP: 91.189.91.39 80]
Lendo listas de pacotes... Pronto
E: The repository 'http://security.ubuntu.com/ubuntu hirsute-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu hirsute Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu hirsute-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Atingido:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security InRelease                                                           
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute InRelease                                                                  
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security Release                                                     
  404  Not Found [IP: 91.189.91.39 80]
Ign:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates InRelease                                                  
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute Release                               
  404  Not Found [IP: 91.189.91.39 80]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates Release
  404  Not Found [IP: 91.189.91.39 80]
Atingido:8 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease
Lendo listas de pacotes... Pronto
E: The repository 'http://security.ubuntu.com/ubuntu hirsute-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu hirsute Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu hirsute-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
O pacote gnome-shell-extensions não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'gnome-shell-extensions' não tem candidato para instalação

---

### Post by #&amp;thj^% on 2023-01-20
I'll bet we get duplicate sources now....LOL
Holy Crap, I'll let deadflowr help you sort this out now :P
you know I still love you deadflowr...:)

---

### Post by leoxavi3r on 2023-01-20
why this now oh ****
sorry im noob lol

---

### Post by leoxavi3r on 2023-01-20
GNU nano 6.2                                         /etc/apt/sources.list                                                  
# See sources.list(5) manpage for more information
# Remember that CD-ROMs, DVDs and such are managed through the apt-cdrom tool.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hirsute-security main restricted universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hirsute-updates main restricted universe


after deadflowr tip

---

### Post by leoxavi3r on 2023-01-20
i read the edit but i dont understood all the context
please what i can do to fix this?

---

### Post by #&amp;thj^% on 2023-01-20
Just remove those now:
```
deb http://us.archive.ubuntu.com/ubuntu hirsute main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu hirsute main restricted universe

deb http://security.ubuntu.com/ubuntu hirsute-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hirsute-security main restricted universe

deb http://us.archive.ubuntu.com/ubuntu hirsute-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu hirsute-updates main restricted universe

```
I'm not even going to ask about those.

---

### Post by leoxavi3r on 2023-01-20
lol

thanks a lot 1fallen

sudo apt install gnome-shell-extensions

worked

i am trying to add theme now

---

### Post by deadflowr on 2023-01-20
Sorry, ignore what i wrote and just delete the entries made when you copied the default sources and add the entries 1fallen posted in post #13.
It seems they have not been updating the doc files.
No need to run the add-apt-repository command since he has the universe entries already in there.
If that makes sense.

Edit: I am taking too long to type today.
Ignore this since you seem to have figured it out.

---

### Post by #&amp;thj^% on 2023-01-20
Good Luck and have fun..

---

### Post by leoxavi3r on 2023-01-20
all right
command works
so topic is solved
thank for you both
but i am really trapped in this mission
like
system dont have Software & Updates
system settings dont have all options like in ~appearance just have Light or Dark
and tweaks isn'n so complete like propaganda
whats can i do to solve this, any tutorial or tips

---

### Post by #&amp;thj^% on 2023-01-20
```
apt policy ubuntu-desktop
```
Have you fully upgraded yet?
```
sudo apt upgrade
```

---

### Post by leoxavi3r on 2023-01-20
pt policy ubuntu-desktop
ubuntu-desktop:
  Instalado: (nenhum)
  Candidato: 1.481
  Tabela de versão:
     1.481 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
leoxavier@leoxavier:~$ sudo apt upgrade
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
Calculando atualização... Pronto
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
Os pacotes a seguir serão mantidos em suas versões atuais:
  grub-common grub-pc grub-pc-bin grub2-common update-notifier-common
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 5 não atualizados.


maybe the error consists on this

500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages

just a though, maybe??
if yes, dont know how to delete

---

### Post by leoxavi3r on 2023-01-20
cause the apperance or software & updates continues the same
the same with Extensions, there are different options than the tutorial that i sent the link in beginning
srry i am trully lost

Edit
all day long on this

---

### Post by #&amp;thj^% on 2023-01-20
Not a error, just tells me it's not installed, and there is phased update that will come in when ubuntu push's it out to you.
Now your whole set-up has me begging to ask, "

You did want a Ubuntu-Gnome desktop right?

---

### Post by leoxavi3r on 2023-01-20
Good. First i installed a linux deepin in this machine but i chose to change to lubuntu cause the keyboard compatibily and it fixed and then wifi fixed and then i almost installed firefox well done but not so much cause firefox launcher is hidden just a shortcut on desktop and when i tried to improve the appearance of all lubuntu i tried install this mac os theme or i could try windows theme cause i cant find things on this distro like where is software & updates configs where are settings advanced configs and i want to create a better desktop to work on my university this year without head pain and now you told me ubuntu gnome maybe its better to me but i already installed this lubuntu and it keeps a lot of time so you think i can fix these pontual dinamic use of lubuntu and then "ubuntu push's it out to you" cause i'm really burnout here

---

### Post by leoxavi3r on 2023-01-20
Apple MacBook "Core 2 Duo" 2.4 (Black-08)
Identifiers: Early 2008 - MB404LL/A - MacBook4,1 - A1181 - 2242

lubuntu®&#65039; 22.04.1 LTS (Jammy Jellyfish)

there was no more upgrade system from Apple
just Leopard to Lion but it's no more covered by nothing

i just hate apple

---

### Post by #&amp;thj^% on 2023-01-20
Well if it's just too much for you rest a bit, I'm not a Lubuntu user, I'll leave that to someone wiser in that field.
We just did not know what the Hades you installed for a desk-top use.

---

### Post by leoxavi3r on 2023-01-20
[https://www.youtube.com/watch?v=nHRai14ETKU](https://www.youtube.com/watch?v=nHRai14ETKU)

tutorials....

---

### Post by leoxavi3r on 2023-01-20
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

what do you think about this?

---

### Post by leoxavi3r on 2023-01-20
sorry you contribute a lot today
thanks and peace brother

---

