---
title: "Startup Script - Install Everything with ONE Command"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by strid3r on 2013-01-07
I just started working on this and it is something that has saved me so much time as my system crashed and I had to reinstall. 
It took me a couple of hours after a fresh install and I'm back to the system I had before.

I like linux as much as the next guy, but the install process can be a pain in the rear, which is why I came up with this script.

It's basically every install command I've run since installing 12.10 on my laptop. Don't just blindly run this, as there are many programs included, some that you won't want. 
I'm pasting this as an example, use what you like.

Features:
Auto-mount windows network drive for backups
Add all needed repositories
You can even automatically compile programs (conky-colors, etc)
Automatically copy settings and whatever you want to keep from your backup home folder.
Just make a file called .excludelist in the home folder of the backup and fill it with folder and file names of things you DON'T want to get copied.
I always include ".cache" ".nv" and a few other files that shouldn't be copied from one installation to another.

How to use:
If you don't know what you're doing, do not use this. You can seriously F* up your system. If you have any doubts about a piece of code, test it out in smaller batches.

Just run this as ```
./startup /path/to/backup/home ~
```

I like it because I can just run this script, and even if I don't have my home directory, my system will be 90% the way it was before it decided to blow up. Njoy!


```
#!/bin/bash

## Mount Samba Network Drive
if grep -q "smbcredentials" /etc/fstab
then
    echo "Mounting all drives in fstab"
    sudo mount -a
else
    echo "Setting up /media/windows"
    sudo mkdir /media/windows
    sudo apt-get update
    sudo apt-get install -y cifs-utils
### edit the following to your windows user info
    echo "username=WINDOWSUSER
password=#########" | sudo tee /root/.smbcredentials
    sudo chmod 700 /root/.smbcredentials
    echo "//192.168.1.XX/Users/WINDOWSUSER /media/windows  cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0"  | sudo tee -a /etc/fstab
    sudo mount -a
fi
#
## BACKUPS
rsync -Phruv --progress --exclude-from=$1/.excludelist $1/.[a-zA-Z0-9]* $2
rsync -Phruv --progress --exclude-from=$1/.excludelist $1/Documents $2/
rsync -Phruv --progress --exclude-from=$1/.excludelist $1/Pictures $2/
rsync -Phruv --progress --exclude-from=$1/.excludelist $1/Music $2/
rsync -Phruv --progress --exclude-from=$1/.excludelist $1/Downloads $2/
rsync -Phruv --progress --exclude-from=$1/.excludelist "$1/My Games" $2/
find $2/Documents/scripts -type f -name '*~' -exec rm -v '{}' \;
sudo chmod -R +x $2/Documents/scripts/bin
sudo cp -rfv $2/Documents/scripts/bin/* /bin/
#
## REPOSITORIES
sudo apt-add-repository -y ppa:mixxx/mixxxbetas
sudo apt-add-repository -y ppa:webupd8team/themes 
sudo apt-add-repository -y ppa:tiheum/equinox 
sudo apt-add-repository -y ppa:satyajit-happy/themes 
sudo apt-add-repository -y ppa:upubuntu-com/chat
sudo apt-add-repository -y ppa:ubuntu-wine/ppa
sudo apt-add-repository -y ppa:caffeine-developers/ppa
sudo add-apt-repository -y ppa:gnome3-team/gnome3
sudo add-apt-repository -y ppa:n-muench/burg
sudo add-apt-repository -y ppa:ubun-tor/ppa
sudo apt-get update && sudo apt-get -y dist-upgrade
#
## PACKAGE INSTALL + REMOVAL
sudo apt-get remove -y gnome-screensaver ubuntu-settings
sudo apt-get install -y mixxx skype gimp ubuntu-restricted-extras chromium-browser wine playonlinux smplayer

sudo apt-get install -y compizconfig-settings-manager compiz-plugins compiz-plugins-extra
sudo apt-get install -y gnome-shell gnome-tweak-tool gir1.2-gtop* faience-theme faience-icon-theme faenza-icon-theme gnome-shell-theme-elegance dconf-tools gconf-editor burg burg-themes
#sudo apt-get install -y ubuntu-gnome-desktop ubuntu-gnome-default-settings 
sudo apt-get install -y gnome-documents gnome-boxes
sudo apt-get install -y conky-all python-statgrab ttf-droid curl python-keyring
sudo apt-get install -y p7zip-full rar linux-headers-$(uname -r) linux-source nvidia-experimental-310 nvidia-settings-experimental-310 ia32-libs-multiarch
sudo apt-get install -y xscreensaver xscreensaver-gl-extra xscreensaver-data-extra caffeine  
sudo apt-get install -y lm-sensors hddtemp tor privoxy
sudo sensors-detect
#
## CUSTOM INSTALLATION
# conky colors
if [ ! -d $2/Downloads/Apps/conky_colors ];
then
    echo "##############   Installing Conky Colors!"
    mkdir ~/Downloads/Apps
    cd ~/Downloads/Apps
    wget http://www.deviantart.com/download/244793180/conky_colors_by_helmuthdu-d41qrmk.zip
    unzip -x conky_colors_by_helmuthdu-d41qrmk.zip
    rm conky_colors_by_helmuthdu-d41qrmk.zip
    cd conky_*
    make
    sudo make install
fi
# tor browser bundle
if [ ! -d $2/Downloads/Apps/tor-browser ];
then
    echo "##############   Installing Tor Browser!"
    mkdir -p $2/Downloads/Apps
    cd ~/Downloads/Apps 
    wget https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-2.3.25-1-dev-en-US.tar.gz
    tar -xvf tor-browser-gnu-linux-x86_64-2.3.25-1-dev-en-US.tar.gz
    mv tor-browser_en* tor-browser
    cd tor-browser
	rm tor-browser-gnu-linux-x86_64-2.3.25-1-dev-en-US.tar.gz
#    ./start-tor-browser
fi
# google voice plugin
if [ ! -f $2/Downloads/google-talkplugin_current_amd64.deb ];
then
    echo "##############   Installing Google Voice Plugin!"
    cd $2/Downloads && wget https://dl.google.com/linux/direct/google-talkplugin_current_amd64.deb
    sudo dpkg -i google-talkplugin_current_amd64.deb
    rm google-talkplugin_current_amd64.deb
fi
# gnome shell 3.6
if [ ! -f $2/Downloads/gs-extensions-3.6.deb ];
then
    echo "##############   Installing Gnome 3.6 Shell Extensions!"
    cd $2/Downloads && wget -O gs-extensions-3.6.deb http://dl.dropbox.com/u/53319850/NoobsLab.com/apps/gs-extensions-3.6.deb
    sudo dpkg -i gs-extensions-3.6.deb
    rm
	gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'
fi
# burg
while true; do
    read -p "Install Burg? (y/n) " yn
    case $yn in
        [Yy]* ) read -p "ENTER DEVICE /dev/" device; sudo burg-install /dev/$device;  sudo update-burg; break;;
        [Nn]* ) exit;;
        * ) echo "Please answer yes or no.";;
    esac
done
# themes
if [ ! -d $2/.icons/Vienna3Ubuntu ];
then
mkdir -p $2/Downloads/del
mkdir -p $2/.icons
mkdir -p $2/.themes
cd $2/Downloads/del

   # cursor themes
wget http://205.196.122.96/3dccgnfb93rg/85k2e8ye47drrdr/Vienna3Ubuntu.tar.gz
wget http://205.196.120.205/co9b9rabd1rg/wozu8wehnvysb1c/Vienna3Orange.tar.gz
wget http://gnome-look.org/CONTENT/content-files/106210-Eclipse.tar.gz
for i in *.tar.gz; do tar xzvf $i; done
rm -rv *.tar.gz
mv * $2/.icons
rm -rv *
   # gtk/shell themes
wget http://gnome-look.org/CONTENT/content-files/148398-MediterraneanNight-G36.tar.gz
for i in *.tar.gz; do tar xzvf $i; done
rm -rv *.tar.gz
mv * $2/.themes
rm -rv *

sudo ln -s /home/$USER/.themes/* /usr/share/themes/
sudo ln -s /home/$USER/.icons/* /usr/share/icons/
fi

sudo apt-get remove -y unity-lens-shopping
sudo apt-get autoremove -y
sudo apt-get clean

```




**If you have your own script that you use for fresh installs, post it below!**

.

---

### Post by Bucky Ball on 2013-01-07
Reinstalling is *always* a last resort. Much more helpful to the community (and your knowledge) to work out why your machine 'blew up'. But horses for courses and whatever suits. Guess that's what it's about.

Well done on the coding though.

---

### Post by strid3r on 2013-01-08
> **Bucky Ball said:**
> Reinstalling is *always* a last resort. Much more helpful to the community (and your knowledge) to work out why your machine 'blew up'. But horses for courses and whatever suits. Guess that's what it's about.

Well done on the coding though.


Thanks!


To be honest, I didn't even try to fix my system. I would get a boot up error that said failed to start failsafe session and then it would start replacing words and letters with random ascii characters and some I've never seen before. Lol that's why I re-installed, but if you can tell me what may have happened, I would be curious to know.

---

### Post by strid3r on 2013-01-23
Turns out it was a corrupt SSD. Don't buy Patriot! :0

---

### Post by Bucky Ball on 2013-01-23
Problem solved. Could you mark it that way from Thread Tools to help others? Thanks for tying this off. ;)

---

