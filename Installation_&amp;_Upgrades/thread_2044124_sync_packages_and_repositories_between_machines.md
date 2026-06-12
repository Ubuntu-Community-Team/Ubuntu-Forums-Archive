---
title: "sync packages and repositories between machines"
date: 2012-08-18
forum: Installation &amp; Upgrades
---

### Post by aleblanc on 2012-08-18
Here is a recipe for keeping your packages and repository information backed up so that you can easily recreate your setup on another machine. Ubuntu versions > 11.10 have the "sync packages" option in the software-center application, but that option is not available in earlier versions of ubuntu. The scripts below will allow you to easily migrate packages from an old ubuntu installation to a new one.

The first script was taken from [[COLOR="Blue"]here[/COLOR]]("http://voidandany.free.fr/index.php/installer-de-facon-automatique-une-liste-de-package-et-les-depots-associes/") and altered slightly. 
It reads a config file and updates packages and repositories.

The second script can be used to automatically create the config file for the first one, aswell as backup other information that might be useful such as dpkg log files. I recommend putting it (the second script) in /etc/cron.daily so that it is run every day. Also you should change the DPKGDIR variable to point to some directory that you have backed up with some offline backup service such as ubuntu one. Then you will always be able to recover your package selections and repositories.

```
#! /bin/bash
 
################################################################################
# Ubuntu (> 9.10) post installation script
# by VoidAndAny
#
# based on cleanstart-packages.list.sh by silverwav - OpenPGP key:03187548 15 Apr 2009
#
# this script read a config file and :
#     add PPA with add-apt-repository
#     add other repositories (not PPA) by writing them in a .list file in /etc/apt/source.list.d
#     add GPG keys
#     install package using aptitude install
#     remove pacakge using aptitude remove
#
################################################################################
#
# Usage:
# installation.sh
# (reads a file called packages.list by default).
# or
# installation.sh <filename>
#
# Any line starting with a # is ignored as are Blank lines.
# Lines beginning by "ppa:" are used to add PPA repositories
# Lines beginning by "deb http", containing ">" followed by a file name with ".list" extension are used to add a repository in /etc/apt/sources.list.d/ (into a the file name specified after the ">")
# Line beginning by "key:" followed by a key id are used to add GPG key from keyserver.ubuntu.com
# Line beginning by "http:", ending by ".gpg" are used to download and add GPG key froman URL
# Other lines are package lists
#  if the line begins with a "-" then the packages listed on the line will be removed, otherwise they will be installed
#
################################################################################
clear
echo "--------------------------------------------------------------------------------"
echo "                 (cleanstart) Script for installing packages (client)                 "
echo "--------------------------------------------------------------------------------"
 
# ensure script is run as root/sudo
if [ "$(id -u)" != "0" ]
then
 echo ""
 echo "Must execute the script as root user."
 echo "--------------------------------------------------------------------------------"
 exit 1
fi
 
# check the argument count
if [ $# -gt "1" ]
then
 echo ""
 echo "Only one file with package names allowed."
 echo "--------------------------------------------------------------------------------"
 exit 1
fi
 
################################################################################
#### Main
#### args: (1)
#### 1. [out] List of input package names
################################################################################
 
CONFIG_FILE=""
# package names to be installed
PACKAGE_NAME_LIST=""
 
# check if filename was supplied as comand line parameter
if [ $# -eq "1" ]
then
 CONFIG_FILE=$1
else
 CONFIG_FILE=packages.list
fi
 
PACKAGE_NAME_LIST=$(cat $CONFIG_FILE | grep -v -E "(^#)|(^ppa:)|(^deb http)|(^-)|(^key:)|(^http:.*\.gpg)" | awk -F'#' '{ print $1}')
REMOVE_PACKAGE_LIST=$(cat $CONFIG_FILE | grep -E "^-" | awk -F'#' '{ print $1}' | sed 's/^-//g')
PPA_NAME_LIST=$(cat $CONFIG_FILE | grep -E "^ppa:" | awk -F'#' '{ print $1}')
REPOSITORY_KEY_LIST=$(cat $CONFIG_FILE | grep -E "^key:" | awk -F'#' '{ print $1}' | sed 's/^key://g')
GPG_URL_LIST=$(cat $CONFIG_FILE | grep -E "^http:.*\.gpg" | awk -F'#' '{ print $1}')
 
echo ""
echo "Installing PPA:" ${PPA_NAME_LIST}
echo "--------------------------------------------------------------------------------"
 
for i in $(echo  $PPA_NAME_LIST ); do
 add-apt-repository $i;
done
 
echo ""
echo "Installing other repositories (not PPA) "
echo "--------------------------------------------------------------------------------"
 
cat $CONFIG_FILE | grep -E "^deb http:.*>.*\.list" | awk -F'>' '{gsub(/[[:space:]]*/,"",$2) ; print $1 > "/etc/apt/sources.list.d/"$2 }'
 
echo ""
echo "Adding GPG key of other repositories (not PPA) "
echo "--------------------------------------------------------------------------------"
 
for i in $(echo $REPOSITORY_KEY_LIST ); do
 apt-key adv --keyserver keyserver.ubuntu.com --recv-key $i;
done
 
for i in $(echo $GPG_URL_LIST ); do
 wget -O - $i | sudo apt-key add - ;
done
 
echo ""
echo "Updating... "
echo "--------------------------------------------------------------------------------"
 
aptitude update
 
echo ""
echo "Installing packages:" ${PACKAGE_NAME_LIST}
echo "--------------------------------------------------------------------------------"
# ajouter le -y
echo ${PACKAGE_NAME_LIST} | xargs aptitude -y install
 
echo ""
echo "Uninstalling packages:" ${REMOVE_PACKAGE_LIST}
echo "--------------------------------------------------------------------------------"
 
echo ${REMOVE_PACKAGE_LIST} | xargs aptitude -y remove
 
echo ""
echo "Done"
echo "--------------------------------------------------------------------------------"

```

Second script:

```
DPKGDIR=$HOME/.config/dpkg/$HOSTNAME
# keep record of currently installed packages for this machine 
/usr/bin/dpkg --get-selections > $DPKGDIR/selections
# write config file for sync_ubuntu_packages.sh
echo "# Currently installed packages" > $DPKGDIR/packages.list
dpkg --get-selections | /usr/bin/awk '/\Winstall/{print $1}' >> $DPKGDIR/packages.list
echo "# Currently deinstalled packages" >> $DPKGDIR/packages.list
dpkg --get-selections | /usr/bin/awk '/\Wdeinstall/{print "-"$1}' >> $DPKGDIR/packages.list
echo "# GPG keys" >> $DPKGDIR/packages.list
apt-key list | /usr/bin/awk '/^pub/{sub(/^pub\W+[0-9]+[RD]\//,"key:");print $1}' >> $DPKGDIR/packages.list
echo "# PPA's" >> $DPKGDIR/packages.list
cat /etc/apt/sources.list.d/*list | /usr/bin/awk '/^deb http:\/\/ppa\./{x=gensub(/^deb http:\/\/ppa\.launchpad\.net\/(.*?)\/.*/,"ppa:\\1",1);print x}' >> $DPKGDIR/packages.list
echo "# Debs. Edit these lines: remove unnecessary ones, uncomment the ones you want to keep and place \" > <FILENAME>.list\" at the end of each line, where <FILENAME>.list is a name for the file to create in /etc/apt/sources.list.d/ " >> $DPKGDIR/packages.list
cat /etc/apt/sources.list | /usr/bin/awk '/^deb(-src)? https?:\/\// && !/archive\.ubuntu\.com/{sub(/#.*/,"");print "# " $0}' >> $DPKGDIR/packages.list
cat /etc/apt/sources.list.d/*list | /usr/bin/awk '/^deb https?:\/\// && !/^deb(-src)? https?:\/\/ppa/{sub(/#.*/,"");print "# " $0}' >> $DPKGDIR/packages.list
# copy dpkg logs that show when packages were installed
/usr/bin/rsync -au /var/log/dpkg.log* $DPKGDIR/



```

---

