---
title: "Bash script updater logic question"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by highspider on 2011-03-02
The question is for the update logic not the bash syntax. 

I wrote this script to update to natty and skip maverick.  (aka Lucid -> natty ) the theory was you should be able update and skip distros. The sripted worked fine, and seemed to be installing natty, but natty didn't load.  I got a unable to mount / press S to skip or M for Manuel and it.  I had to reinstall as maverick.

I know natty has not yet "officially" been released.  
  so is natty my issue or should this work.

:confused:I just don't know if the logic behind my script is wrong or if I missed something entirely.:confused:

```
#!/bin/bash
# Init
FILE="/tmp/out.$$"
GREP="/bin/grep"
# check if user opened as root UUID
if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

shopt -s extglob
while [[ 1 ]]
do
    echo -e "\n\t\tThe any Version Ubuntu Linux Updater\n\t\tBy: Highspider on ubuntuforums.org\n\n\t1) Dapper Drake (June 1, 2006 )\n\t2) Hardy Heron (April 24, 2008)\n\t3) Karmic Koala (October 29, 2009)\n\t4) Lucid Lynx (April 29, 2010)\n\t5) Maverick Meerkat (October 10, 2010)\n\t6) Natty Narwhal(April 2011)\n"
    read -p "Please make a selection, select \"q\" to quit \"a\" for about: " choice
    case $choice in
     1) uv=dapper 
         break ;;
     2) uv=hardy
         break ;;
     3) uv=karmic
         break ;;
     4) uv=lucid
         break ;;
     5) uv=maverick
         break ;;
     6) uv=natty
         break ;;
    a|A) echo -e "\n\nThe point of this program is to update from any version Ubuntu to any other version. This should also help get around \"Could not calculate the upgrade\n An unresolvable problem occurred while calculating the upgrade: ...\" Error and other Errors caused by upgrade manger.\n"
         break ;;
    q|Q) break ;;
      *) echo -e "\n\n\tSorry \"$choice\" is an Invalid Choice"
           ;;
    esac
done

#if not q and not Q 
if [ "$choice" != "q" -a "$choice" != "Q" -a "$choice" != "a" -a "$choice" != "A"  ]; then
 echo -e "\n\n Are you sure you want to update your system to $uv"
 read -p "       Enter \"y\" for (y)es: " dcheck
 #if is y or is Y
 if [ "$dcheck" == "y" -o "$dcheck" == "Y" ]; then 
  echo "deb http://us.archive.ubuntu.com/ubuntu $uv main restricted universe multiverse" >> /etc/apt/sources.list
  echo "deb http://security.ubuntu.com/ubuntu $uv-security main restricted universe multiverse" >> /etc/apt/sources.list
  echo "deb http://us.archive.ubuntu.com/ubuntu $uv-updates main restricted universe multiverse" >> /etc/apt/sources.list
  echo "deb http://us.archive.ubuntu.com/ubuntu $uv-proposed main restricted universe multiverse" >> /etc/apt/sources.list
  echo "deb http://us.archive.ubuntu.com/ubuntu $uv-backports main restricted universe multiverse" >> /etc/apt/sources.list
  
  apt-get update
  sudo apt-get dist-upgrade
 
 fi
fi 
```

---

