---
title: "erros with apt-get"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by juraj-papic on 2020-05-07
Hi all

I have the following system, every time I want to install or update with apt-get I get the errors:

```
cat /etc/os-release
NAME="Ubuntu"
VERSION="19.04 (Disco Dingo)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 19.04"
VERSION_ID="19.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=disco
UBUNTU_CODENAME=disco
```
---
Error:

```
Obj:1 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease
Obj:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) disco InRelease                                                                                                                                             
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                               
Obj:4 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                                                                                                          
Obj:5 [https://d3nt0h4h6pmmc4.cloudfront.net/ubuntu](https://d3nt0h4h6pmmc4.cloudfront.net/ubuntu) bionic InRelease                                                                                                                                        
Obj:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                                                                 
Obj:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco InRelease                                                                                                                                                  
Ign:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco InRelease                                                                                 
Obj:9 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) disco InRelease                                   
Obj:11 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ InRelease                                                                      
Ign:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates InRelease                                       
Ign:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports InRelease           
Obj:14 [http://ppa.launchpad.net/nm-l2tp/network-manager-l2tp/ubuntu](http://ppa.launchpad.net/nm-l2tp/network-manager-l2tp/ubuntu) disco InRelease
Ign:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security InRelease            
Err:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco Release                       
  404  Not Found [IP: 91.189.88.152 80]
Obj:17 [http://ppa.launchpad.net/smartfinn/eve-ng-integration/ubuntu](http://ppa.launchpad.net/smartfinn/eve-ng-integration/ubuntu) disco InRelease
Err:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates Release               
  404  Not Found [IP: 91.189.88.152 80]
Err:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports Release             
  404  Not Found [IP: 91.189.88.152 80]
Obj:20 [http://ppa.launchpad.net/webupd8team/terminix/ubuntu](http://ppa.launchpad.net/webupd8team/terminix/ubuntu) disco InRelease
Err:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security Release
  404  Not Found [IP: 91.189.88.152 80]
Leyendo lista de paquetes... Hecho
W: Omitiendo adquisición del archivo configurado «stable/source/Sources» como repositorio «[https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) disco InRelease» no parece proporcionarlo (¿entrada en sources.list mal escrita?)
E: El repositorio «[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: El repositorio «[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: El repositorio «[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
E: El repositorio «[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security Release» no tiene un fichero de Publicación.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.

```

Please how can I fix this? 

thanks.

---

### Post by SeijiSensei on 2020-05-07
19.04 is out of support.  You should upgrade to 20.04 which has support for five years.

Your list of repositories is a mess.  The standard 20.04 /etc/apt/sources.list looks like this:

```

# deb cdrom:[Kubuntu 20.04 LTS _Focal Fossa_ - Alpha amd64 (20200106)]/ focal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu focal partner
#deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
#deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
#deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
#deb-src http://security.ubuntu.com/ubuntu focal-security multiverse
#
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

```
I've activated a few repositories like "multiverse" which I think are commented out by default.

---

### Post by juraj-papic on 2020-05-07
Hello,

Can I get the source.list you posted and use it on my sourcelist?

thanks.

---

### Post by juraj-papic on 2020-05-07
more /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416)]/ disco main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb [arch=amd64] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) disco stable
deb-src [arch=amd64] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) disco stable
```

---

### Post by CelticWarrior on 2020-05-07
> **juraj-papic said:**
> Hello,

Can I get the source.list you posted and use it on my sourcelist?

thanks.

No, you should install a supported release, that's all.

---

### Post by juraj-papic on 2020-05-07
Hello CelticWarrios,

I need to reinstall all again? Im trying to avoid this part.

thansk.

---

### Post by ajgreeny on 2020-05-07
It's theoretically possible to update from 19.04 but firstly you would have to point to the EOL (End Of Life) repos which are now moved away from the old URL, and use them to make sure that 19.04 is fully up to date. You would then need to upgrade to 19.10, and once you have done that and checked that all is OK move from 19.10 to 20.04.

This is a very long process and it does, frankly, offer a great chance of things going wrong, so I also believe, like CelticWarrior that your most sensible option is to just get on with it and clean install 20.04.

---

### Post by Impavidus on 2020-05-07
> **juraj-papic said:**
> Hello,

Can I get the source.list you posted and use it on my sourcelist?

thanks.

If you do so it will trigger a dirty release upgrade. It might work, but it's more likely to end in failure. It can also result in a system that seems to work for some time, but then starts to show strange glitches and nobody will know how to fix them with such a complex history.

You can always try, but I suggest you prepare for a fresh install anyway. A fresh install should only take half an hour.

---

### Post by juraj-papic on 2020-05-07
Hello,

My idea was try to fix the apt-get some how with out the  upgrade. And the issue started when I was trying to install a new app I need. Maybe did the wrong answer every time I want to install something I get that error in the first post.

thanks.

---

### Post by QIII on 2020-05-07
As suggested above, the errors you are encountering are due to the fact that your release has gone out of support and the repositories have been moved -- hence the "404" errors.  The resources cannot be found.  This can't be "fixed".

You may try the old-release path, but as stated your chances of success are very slim and you will likely regret having tried.  You could try to update your sources list, but that is an almost certain recipe for disaster if you skip over several intermediate releases.

As several people have said, your best course of action would be to back up your important files and do a fresh installation of a supported release.

That is simply the best, probably the only, answer.

---

### Post by juraj-papic on 2020-05-07
Thanks, to all for the help , now my question will be how can I do the upgrade with out breaking my notebook?

thanks again.

---

### Post by juraj-papic on 2020-05-07
ok,, thanks to all! I will go the suggested options.

thanks again.

---

