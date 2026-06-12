---
title: "move packages from one computer to another"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Strannik on 2006-11-22
Hi Everbody, I tried searching this forum and google for a way how to create the deb files of the packages that I have installed currently on my computer so that a friend of mine could install them on his computer? 

Could somebody point me in the right direction?

---

### Post by pandu.rs on 2006-11-22
i have done this already to install ubuntu dapper at home. i will share my ideas with u.

created a directory. This is where we are going to download all deb packages that are installed on ur system.

mkdir ~/debs
cd ~/debs

u will already have some deb packages stored in ur /var/cache/apt/archives/ so we dont want to download them again.. so do this

cp /var/cache/apt/archives/*.deb ./

then the next step is to produce a list of packages that are installed the system
dpkg --get-selections | sed -n 's/^\(.*\)\tinstall$/\1$/p' | cut -f1 > ~/installed_pkgs

Ok..now u have to boot using live cd. (yes otherwise apt-get will say it is already newer version nothing needs to be done)

Once u r in live cd mount ur home, or whatever that has ur debs dir that we created..

sudo mkdir /actual_home
sudo mount <partition> /actual_home

make sure that live cd user (ubuntu) is able to write /actual_home/debs dir. (by mouting apprpriately or using chmod)

then

cd /actual_home/debs
cat /atcual_home/installed_pkgs | xargs -i apt-get install -qq --print-uris {} | cut -d\' -f2 | xargs wget -c -nc

that is it.. the above steps will download all the debs installed ur system (including dependencies).


Now u can leave the live cd and boot as usual.
Labe1l: 
u can create ur own local repository and use them
([http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages))

cd ~
dpkg-scanpackages debs /dev/null | gzip > debs/Packages.gz

to make use of the local repository u shld add the following line to /etc/apt/sources.list

deb file:/home/<username> debs/

So just transfer the debs dir to another computer and follow the steps from label1 to install any package that u already installed in first computer.

---

### Post by pandu.rs on 2006-11-22
Alternatively if u want to install all the packages that u have in the current system into a new one.. there is a better way (u have to do all steps in my previous post before u proceed here)..

copy installed_packages to the target machine.

cat installed_packages | xargs sudo dpkg --set-selections

then run

sudo dselect

and choose install.. all the packages will be installed! that is it... so easy

The power of Linux!

---

### Post by Strannik on 2006-12-04
Thanks a lot!!! I will definately try this out at home today!

---

