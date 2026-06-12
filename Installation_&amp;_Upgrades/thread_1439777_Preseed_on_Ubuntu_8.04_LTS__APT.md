---
title: "Preseed on Ubuntu 8.04 LTS / APT"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by gustavonfr on 2010-03-26
Hello everybody,

I'm creating a file preseeding to automate the installation of 8.04, because I have many machines to be installed (laboratory). My preseed file works very well, just have a problem .... it does not include the additionals repositories that I'm putting (universe and multiverse). I need these repositories because I am installing some packages that are not in the main repository, as the python-simplejson and others who want to add. When arrive at the install packages it gives error saying that the package is not installable. Going into the shell of the facility and giving the chroot / target I realize that really are not the repositories in sources.list. What do I do? I already read all documentation preseed that are in the web. Sorry my english  =)

Preseed file:
```

# Ingles por default
d-i debian-installer/locale string en_US
#Desabilita a escolha do teclado e seleciona o padrão "us"
d-i console-setup/ask_detect boolean false


#Parte de rede(ip estatico)
d-i netcfg/choose_interface select auto
d-i netcfg/disable_dhcp boolean true
d-i netcfg/dhcp_failed note
d-i netcfg/dhcp_options select Configure network manually

d-i netcfg/get_nameservers string 192.168.100.1
d-i netcfg/get_ipaddress string 192.168.100.50
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.168.100.1
d-i netcfg/confirm_static boolean true

#Proxy
d-i mirror/http/proxy string

#Nome do maquina
d-i netcfg/get_hostname string lab10
d-i netcfg/get_domain string localdomain

#Timezone
d-i time/zone string US/Eastern
d-i clock-setup/utc-auto boolean true

#Kernel
d-i base-installer/kernel/override-image string linux-server

# Only install basic language packs. Let tasksel ask about tasks.
d-i pkgsel/language-pack-patterns string

# No language support packages.
d-i pkgsel/install-language-support boolean false

#Usuario root/usuario normal com senha padrao
d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password $1$MKmDJ9hz$rPeyy9LYo7Ri0fAwloyNB/
d-i passwd/make-user boolean false

d-i passwd/user-fullname string admin
d-i passwd/username string admin
d-i passwd/user-password-crypted password $1$MKmDJ9hz$rPeyy9LYo7Ri0fAwloyNB/

#Conf do apt
#d-i apt-setup/local0/repository string \
#       deb cdrom:[Ubuntu-Server 8.04.3 "Hardy Heron" - Release i386]/ nimbus main
apt-mirror-setup        apt-setup/multiverse    boolean true
apt-mirror-setup        apt-setup/universe    boolean true
d-i debian-installer/allow_unauthenticated string true


#Pacotes padrao + ssh
tasksel tasksel/first multiselect standard
d-i pkgsel/include string openssh-server libmysqlclient15off mysql-server-5.0 apache2  libapache2-mod-fastcgi python-flup python-pkg-resources python-simplejson

mysql-server-5.0        mysql-server/root_password password changeme
mysql-server-5.0        mysql-server/root_password_again password changeme

```

I appreciate all the help

---

