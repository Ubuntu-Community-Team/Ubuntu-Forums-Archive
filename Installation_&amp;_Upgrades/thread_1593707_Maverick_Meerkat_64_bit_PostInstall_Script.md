---
title: "Maverick Meerkat 64 bit PostInstall Script"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by tabletuser on 2010-10-11
WILL THIS WORK for 10.10 64 bit?  Anyone see stuff that can be modified.  I'm using bits and pieces, thanks to [Uruz7]("http://ubuntuforums.org/member.php?u=558552") for the original script [post]("http://ubuntuforums.org/showthread.php?t=1379511"). 

[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] 				**Ubuntu Karmic 64 bit PostInstall Script** 			
 			 			 		   		 		 		Hi people!

I always use ubuntuforums.org for fixing problems and searching solutions. 

For work I have to do many fresh Ubuntu installations, and Ultamatix is not my way of do things.

So I have written a post-install script in order to automatize  configuring the system. For once I would like to share, not only to copy  tricks and tips.

At my site (a bad apache-listing directory):
[http://www.infiniteandbeyond.com/ubuntu/](http://www.infiniteandbeyond.com/ubuntu/)
I've uploaded this postinstall script and strong related files.
It is tested and developed for Ubuntu 64-bit 9.10 with an Nvidia graphic  card, but changing few things it can work for much more of hardware.  Besides, you can see it as a long list of useful hacks (not ALL the  hacks on the market!!).

There are some bugs, but nothing impossible to handle by hand.
Read it before use! Obviously, all suggestions are welcome.

Enjoy :grin:

<[COLOR=blue]div id[/COLOR]="[COLOR=green]scrollbox[/COLOR]">
<![COLOR=red]-- Put what Uruz7 scripted here --[/COLOR]>
<[COLOR=blue]/div[/COLOR]>

---

### Post by tabletuser on 2010-10-11
```

[CODE]#!/bin/bash
# Copyright Alberto Zugno, January 2010
# Used for Ubuntu 64-bit 9.10 (Karmic Koala), Italian; NVidia Graphic card; 
# etx3 / partition (logical) and 2xRam for swap partition.

# first:
# chmod 755 post*.sh
# or
# chmod +x post*.sh
# then:
# 

# ./post*.sh inch-screen password server samba-workgroup vncpass lang

usr=`whoami`
user=`echo $usr`

inchs="$1"
pass="$2"
inst="$3"
wgroup="$4"
vncpass="$5"
lang="$6"

if [ "$lang" == "ita" ]; then
    desk="Scrivania"
elif [ "$lang" == "eng" ]; then
    desk="Desktop"
fi


# hacking sudo timeout
echo "Defaults passwd_timeout=360" | sudo tee -a /etc/sudoers > /dev/null

## Add repositories
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
sudo sed -i -e "s/deb http:\/\/it.archive.ubuntu.com\/ubuntu\/  karmic-backports/# deb http:\/\/it.archive.ubuntu.com\/ubuntu\/  karmic-backports/g" /etc/apt/sources.list
sudo sed -i -e "s/deb-src http:\/\/it.archive.ubuntu.com\/ubuntu\/  karmic-backports/# deb-src http:\/\/it.archive.ubuntu.com\/ubuntu\/  karmic-backports/g" /etc/apt/sources.list

echo "deb http://download.virtualbox.org/virtualbox/debian karmic non-free" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main" | sudo tee -a /etc/apt/sources.list > /dev/null
echo "deb http://www.moioli.net/files/repository ubuntu stable" | sudo tee -a /etc/apt/sources.list > /dev/null

#echo "deb http://repository.cairo-dock.org/ubuntu $(lsb_release -sc)  cairo-dock" | sudo tee -a /etc/apt/sources.list > /dev/null  ##  sometimes offline
echo "deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu  $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a  /etc/apt/sources.list
# here     $(lsb_release -sc) = karmic    
# wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -  ## sometimes offline
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29


sudo apt-get update
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update

## AutoPreferences
echo -e "sun-java6-jdk shared/accepted-sun-dlj-v1-1 boolean  true\nsun-java6-jre shared/accepted-sun-dlj-v1-1 boolean  true\nsun-java6-bin shared/accepted-sun-dlj-v1-1 boolean  true\nvirtualbox virtualbox/module-compilation-allowed boolean  true\nvirtualbox virtualbox/delete-old-modules boolean true\nvirtualbox  virtualbox/group-vboxusers boolean true\n" > autoprefs
sudo debconf-set-selections < autoprefs
rm autoprefs

## I have a small "home" server, w/ LaTeX in order to access it through ssh on android phone
if [ "$inst" == "server" ]; then
    serv="texlive-full vuze kile eclipse blender apache2 php5  libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql  phpmyadmin"
else
    serv=""
fi

## Many packages to install!!
sudo apt-get install -y --force-yes --install-recommends $serv virtualbox-3.1 sun-java6-jre \
sun-java6-plugin sun-java6-fonts grub2 ubuntu-tweak dkms \
app-install-data-medibuntu scim-bridge-client-qt apport-hooks-medibuntu \
tracker tracker-search-tool libavahi-client3 libavahi-common3 libc6 \
libjpeg62 libssl0.9.8 libvncserver0 libx11-6 libxdamage1 libxext6 libxfixes3 \
libxinerama1 libxrandr2 libxtst6 zlib1g xorg-dev tracker-utils acidrip dvdrip \
openclipart preload kdebase googleearth-package cairo-dock bluez blueman \
bluez-compat bluez-utils bluez-alsa bluez-cups bluez-gstreamer python-bluez \
bluez-hcidump bluez-gnome bluez-btsco prelink cairo-dock-plug-ins envyng-qt \
moiosms sshfs totem-xine libdvdcss2 libdvdnav4 audacious audacious-plugins  \
lightning-extension-locale-it  clamtk gshare smbfs gsambad \
grsync gthumb hal-cups-utils flashplugin-nonfree klipper gnumeric frozen-bubble \
gimp-help-it sox knetwalk curl uml-utilities pstoedit acpi acroread-fonts \
nautilus-open-terminal bridge-utils amarok14 openoffice.org alarm-clock \
gnome-app-install gftp screenlets inkscape speedcrunch filezilla kino p7zip-full \
k3b rar unrar kdebluetooth kdebase compizconfig-settings-manager gparted \
sound-juicer audacity ssh gnome-splashscreen-manager mail-notification \
bluez-gnome wine vlc thunderbird myspell-it libxine1-ffmpeg phonon-backend-xine \
ubuntu-restricted-extras lightning-extension cups-pdf startupmanager enigmail \
tuxpaint tuxpaint-stamps-default ntfs-config msttcorefonts unace-nonfree openvpn \
isomaster gmountiso pdfedit sysinfo samba libsox-fmt-mp3 openoffice.org-ogltrans mpg123  \
system-config-samba libdvdcss2 w64codecs gstreamer0.10-ffmpeg acroread \
gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-base  \
ntfsprogs gstreamer0.10-plugins-good gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly mozplugger \
gstreamer0.10-plugins-ugly-multiverse libxine1-ffmpeg libxine1-plugins \
thunderbird-locale-it kde-l10n-it kde-i18n-it language-pack-kde-it language-support-it \
audacious-plugins-extra exaile streamtuner gxine gxineplugin libxine1 \
libxine1-gnome libxine1-plugins xine-plugin mplayer mplayer-fonts mplayer-skins \
realplayer tagtool brasero transcode wmctrl openoffice.org-style-oxygen \
# kdelibs5 kdepimlibs5 kdebase-runtime kdebase-workspace kdeadmin  kdeartwork kdegraphics kdemultimedia kdeutils dolphin # dolphin ask for  gdm/kdm
# clamav clamav-daemon clamav-freshclam # sometimes interferes with attachments in Thunderbird


if [ "$inst" == "server" ]; then    
    ## RARCrack (usage: $ rarcrack file.zip, $ rarcrack file.7z)
    wget  http://downloads.sourceforge.net/project/rarcrack/rarcrack-0.2/%5BUnnamed%20release%5D/rarcrack-0.2.tar.bz2?use_mirror=kent
    tar xvjf rarcrack-0.2.tar.bz2
    cd rarcrack-0.2
    sudo apt-get install -y --force-yes libxml2-dev
    make
    sudo make install
    cd ~
    rm -f -R rarcrack*
fi

## DVD Playback
sudo sh /usr/share/doc/libdvdread4/install-css.sh

## x11vnc (default VNC server doesn't work with compiz), see also "Gdm init script" for configuration
wget --progress=bar "http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz" -O x11vnc-0.9.9.tar.gz
tar -zxvf x11vnc*.tar.gz
cd ~/x11vnc*
./configure
make
sudo make install
make clean
make distclean
cd ~
rm -f -R x11vnc*
sudo x11vnc -storepasswd "$vncpass" /etc/x11vnc.pass

## Gdm init script
sudo sed -i -e "s/exit 0//g" /etc/gdm/Init/Default
echo "sudo x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever  -bg -noxdamage -rfbport 5900 -avahi -display :0" | sudo tee -a  /etc/gdm/Init/Default > /dev/null
echo "sudo modprobe vboxnetflt" | sudo tee -a /etc/gdm/Init/Default > /dev/null
echo "exit 0" | sudo tee -a /etc/gdm/Init/Default > /dev/null

## How may reboots between hd checks, w/ /dev/sda6 your root partition
sudo tune2fs -c 120 /dev/sda6

## Set master volume (it works only w/ master volume)
amixer set Master 20%

## Add current user to samba, set workgroup
(echo $pass; echo $pass) | sudo smbpasswd -s -a $user
sudo sed -i -e "s/workgroup = WORKGROUP/workgroup = "$wgroup"/g" /etc/samba/smb.conf

## Nvidia Graphic Card
echo -e "$pass\n1\n0\n1\n" > out
sudo -S envyng -t < out
rm -f out

## Groups
sudo adduser "$user" vboxusers
sudo adduser "$user" floppy

## Skype
wget --progress=bar "http://download.skype.com/linux/skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb"
sudo dpkg -i skype*.deb
rm -f skype*.deb

## Google Earth, BUT STRANGE FONTS
make-googleearth-package
sudo dpkg -i googleearth*.deb
rm -f -R googl*
rm -f -R Googl*
rm -f -R usr*

## Notification at top-right corner as wished
wget --progress=bar "https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1_amd64.deb"
echo -e "0\n0\n0\n" > out
sudo dpkg -i notify-osd*.deb < out
rm -f out
rm -f notify-osd*.deb

## Mac fonts
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/macfonts.tar.gz"
tar -zxvf macfonts.tar.gz && sudo mv macfonts /usr/share/fonts/ ## without "&&" seems to work in async mode..
sudo fc-cache -f -v
rm macfonts.tar.gz

## PDF Import 64-bit OpenOffice.org extension
echo -e "yes\n" > out
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/ooo/sun-pdfimport64.oxt" -O /tmp/sun-pdfimport64.oxt
sudo unopkg add --shared sun-pdfimport64.oxt < out
rm -f out
rm -f sun-pdfimport64.oxt

## Openoffice prefs (save as MS Office as default), NOT WORKING
sudo rm -f /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-writer.xcu
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/Setup-writer.xcu" -O  /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-writer.xcu

sudo rm -f /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-calc.xcu
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/Setup-calc.xcu" -O  /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-calc.xcu

sudo rm -f /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-impress.xcu
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/Setup-impress.xcu" -O  /usr/lib/openoffice/basis3.1/share/registry/modules/org/openoffice/Setup/Setup-impress.xcu

## Openoffice splash screen
cd /usr/lib/openoffice/program
sudo mv openintro_ubuntu_sun.bmp openintro_ubuntu_sun.bmp.bak
cd ~
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/openintro_ubuntu_sun.bmp"  -O /usr/lib/openoffice/program/openintro_ubuntu_sun.bmp


## Cairo Dock Icon Document Launcer for OpenOffice 3
#    in the .zips:
#    /res/lx03249.png impress
#    /res/lx03250.png calc
#    /res/lx03251.png writer
cd /usr/lib/openoffice/basis3.1/share/config/
sudo mv images_human.zip images_humanOLD.zip
sudo mv images_oxygen.zip images_oxygenOLD.zip
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/images_human.zip" -O  /usr/lib/openoffice/basis3.1/share/config/images_human.zip
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/images_oxygen.zip" -O  /usr/lib/openoffice/basis3.1/share/config/images_oxygen.zip
sudo chmod 755 images_human.zip
sudo chmod 755 images_oxygen.zip
cd ~



## Enable NFTS write support
sudo rm -f /etc/hal/fdi/policy/20-ntfs-config-ro-policy.fdi
sudo ln -s /usr/share/ntfs-config/write-policy.fdi /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi


## usplash boot resolution & boot splash image & text during boot
sudo chmod -R a+rw /usr/share/images/xsplash
tar -cf /usr/share/images/xsplash/backup /usr/share/images/xsplash/*
sudo rm -f /usr/share/images/xsplash/bg_2560x1600.jpg

if [ "$inchs" == "22" ]; then
    sudo rm -f /etc/usplash.conf
    inchx="# Usplash configuration file\n\nxres=1280\nyres=960\n"
    sudo echo -e "$inchx" > /etc/usplash.conf
    sudo sed -i -e "s/#GRUB_GFXMODE=640x480/GRUB_GFXMODE=1280x960/g" /etc/default/grub
elif [ "$inchs" == "24" ]; then
    sudo rm -f /etc/usplash.conf
    inchx="# Usplash configuration file\n\nxres=1680\nyres=1050\n"
    sudo echo -e "$inchx" > /etc/usplash.conf
    sudo sed -i -e "s/#GRUB_GFXMODE=640x480/GRUB_GFXMODE=1680x1050/g" /etc/default/grub
fi
    
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/xsplash-bg/horseheadnebula_2560x1600.jpg" -O xbg.jpg
# orionnebula_2560x1600.jpg horseheadnebula_2560x1600.jpg  elemental_1920x1200.jpg abandoned_2560x1600.jpg  helixnebulabytcx_1920x1200.jpg
sudo mv xbg.jpg /usr/share/images/xsplash/bg_2560x1600.jpg
rm -f xbg.jpg

sudo update-initramfs -u


if [ "$inst" == "server" ]; then    
    sudo sed -i -e "s/GRUB_TIMEOUT=\"3\"/GRUB_TIMEOUT=\"60\"/g"  /etc/default/grub ## my Ubuntu server waits for another (slower) server  booting up, for shared items..
else
    sudo sed -i -e "s/GRUB_CMDLINE_LINUX_DEFAULT=\"quiet splash\"/GRUB_CMDLINE_LINUX_DEFAULT=\" splash\"/g" /etc/default/grub
    sudo sed -i -e "s/GRUB_TIMEOUT=\"3\"/GRUB_TIMEOUT=\"6\"/g" /etc/default/grub
fi

sudo sed -i -e "s/GRUB_HIDDEN_TIMEOUT_QUIET=true/GRUB_HIDDEN_TIMEOUT_QUIET=false/g" /etc/default/grub 
sudo sed -i -e "s/GRUB_HIDDEN_TIMEOUT=0/# GRUB_HIDDEN_TIMEOUT=0/g" /etc/default/grub 
sudo update-grub

## Mail-notification Settings
sudo wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/sound/GoogleBeep1.mp3" -O /usr/share/sounds/GoogleBeep1.mp3
sudo wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/sound/GoogleBeep2.mp3" -O /usr/share/sounds/GoogleBeep2.mp3
gconftool --set /apps/mail-notification/always-display-icon --type=bool true
gconftool --set /apps/mail-notification/commands/new-mail/enabled --type=bool true
gconftool --set /apps/mail-notification/commands/new-mail/command --type=string "play /usr/share/sounds/GoogleBeep2.mp3"

## Gnome Desktop Settings
gconftool --set /desktop/gnome/interface/menus_have_icons --type=bool true
gconftool --set /apps/nautilus/desktop/computer_icon_visible --type=bool true
gconftool --set /apps/nautilus/desktop/home_icon_visible --type=bool true
gconftool --set /apps/nautilus/desktop/network_icon_visible --type=bool true
gconftool --set /apps/nautilus/desktop/trash_icon_visible --type=bool true
gconftool --set /apps/nautilus/desktop/volumes_visible --type=bool true
## optimized only for 22-inch-wide screen (lack of time..)!!!
gconftool --set /apps/nautilus/desktop-metadata/computer/nautilus-icon-position --type=string "64,42"
gconftool --set /apps/nautilus/desktop-metadata/computer/nautilus-icon-position-timestamp --type=string "1261555313"
gconftool --set /apps/nautilus/desktop-metadata/home/nautilus-icon-position --type=string "64,142"
gconftool --set /apps/nautilus/desktop-metadata/home/nautilus-icon-position-timestamp --type=string "1261555313"
gconftool --set /apps/nautilus/desktop-metadata/network/nautilus-icon-position --type=string "64,242"
gconftool --set /apps/nautilus/desktop-metadata/network/nautilus-icon-position-timestamp --type=string "1261555313"
gconftool --set /apps/nautilus/desktop-metadata/trash/nautilus-icon-position --type=string "64,342"
gconftool --set /apps/nautilus/desktop-metadata/trash/nautilus-icon-position-timestamp --type=string "1261555313"

## MoioSMS Fix (MoioSMS is an Italian Internet SMS App)
sudo sed -i -e "s/#\!\/usr\/bin\/python2.4/#\!\/usr\/bin\/python/g" /usr/share/moiosms/sms.py

## Firefox Settings
firefox &  # start and kill in order to create .mozilla folder, NOT WORKING
sleep 5 && kill `ps -fu $user|grep firefox| cut -d":" -f1| sed "s/$user  //g"|cut -d" " -f1|sed ':a;N;$!ba;s/\n/ /g'`
echo "tmpfs /tmp tmpfs noexec,defaults,noatime 0 0" | sudo tee -a /etc/fstab > /dev/null
echo "tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0" | sudo tee -a /etc/fstab > /dev/null
echo "vm.swappiness=1" | sudo tee -a /etc/sysctl.conf > /dev/null
echo "user_pref("browser.cache.disk.parent_directory", "/tmp");" | tee  -a $HOME/.mozilla/firefox/*.default/prefs.js > /dev/null
echo "user_pref("browser.tabs.autoHide", false);" | tee -a $HOME/.mozilla/firefox/*.default/prefs.js > /dev/null
echo "user_pref("browser.download.manager.closeWhenDone", true);" | tee  -a $HOME/.mozilla/firefox/*.default/prefs.js > /dev/null
echo "user_pref("browser.download.useDownloadDir", false);" | tee -a $HOME/.mozilla/firefox/*.default/prefs.js > /dev/null

## Thunderbird Settings
thunderbird & # start and kill in order to create .mozilla-thunderbird folder, NOT WORKING
sleep 5 && kill `ps -fu $user|grep thunderbird| cut -d":" -f1|  sed "s/$user  //g"|cut -d" " -f1|sed ':a;N;$!ba;s/\n/ /g'`
# Anybody knows how to install mozilla extensions from addons site @ bash?
#*NOT WORKING:
#sudo wget --progress=bar  "https://addons.mozilla.org/en-US/thunderbird/downloads/latest/4394/addon-4394-latest.xpi?src=addondetail"  -O /usr/lib/thunderbird/extensions/stationery.xpi
#sudo wget --progress=bar  "https://addons.mozilla.org/en-US/thunderbird/downloads/latest/70/addon-70-latest.xpi?src=addondetail"  -O /usr/lib/thunderbird/extensions/contacts_sidebar.xpi
echo "user_pref("openattachment.extension.pdf", "/usr/bin/acroread");" |  tee -a $HOME/.mozilla-thunderbird/*.default/prefs.js > /dev/null
echo "user_pref("openattachment.extension.doc", "/usr/bin/oowriter");" |  tee -a $HOME/.mozilla-thunderbird/*.default/prefs.js > /dev/null
echo "user_pref("openattachment.extension.xls", "/usr/bin/oocalc");" |  tee -a $HOME/.mozilla-thunderbird/*.default/prefs.js > /dev/null
echo "user_pref("openattachment.extension.ppt", "/usr/bin/ooimpress");" |  tee -a $HOME/.mozilla-thunderbird/*.default/prefs.js > /dev/null
echo "user_pref("openattachment.extension.zip", "/usr/bin/zip");" | tee  -a $HOME/.mozilla-thunderbird/*.default/prefs.js > /dev/null

## Thunderbird icons for Cairo-Dock
cd /usr/share/thunderbird/chrome/icons/default/
sudo mv msgcomposeWindow.xpm msgcomposeWindowOLD.xpm # edit messages
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/thunderbird-dock-icons/msgcomposeWindow.xpm"  -O /usr/share/thunderbird/chrome/icons/default/msgcomposeWindow.xpm
sudo mv default.xpm defaultOLD.xpm # main window
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/thunderbird-dock-icons/default.xpm"  -O /usr/share/thunderbird/chrome/icons/default/default.xpm
sudo mv abcardWindow.xpm abcardWindowOLD.xpm  # address book cards
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/thunderbird-dock-icons/abcardWindow.xpm"  -O /usr/share/thunderbird/chrome/icons/default/abcardWindow.xpm
sudo mv addressbookWindow.xpm addressbookWindowOLD.xpm # address book
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/thunderbird-dock-icons/addressbookWindow.xpm"  -O /usr/share/thunderbird/chrome/icons/default/addressbookWindow.xpm

cd /usr/lib/lightning-extension/chrome/icons/default
sudo mv calendar-alarm-dialog.xpm calendar-alarm-dialogOLD.xpm # lightning alarms
sudo wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/thunderbird-dock-icons/calendar-alarm-dialog.xpm"  -O  /usr/lib/lightning-extension/chrome/icons/default/calendar-alarm-dialog.xpm
cd ~


## A better wallpaper
mkdir .other
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/wallpaper/bamboo2_1440x900.jpg" -O .other/bamboo2_1440x900.jpg
gconftool-2 -t str --set /desktop/gnome/background/picture_filename $HOME/.other/bamboo2_1440x900.jpg

## Apps Associations mimetype
sudo rm -f ~/.local/share/applications/defaults.list
mkdir ~/.local/share/applications/
echo -e "[Default  Applications]\nimage/jpeg=gimp.desktop\napplication/vnd.ms-excel=openoffice.org3-calc.desktop\napplication/msword=openoffice.org3-writer.desktop\naudio/mpeg=vlc.desktop\nvideo/x-msvideo=vlc.desktop\napplication/rtf=openoffice.org3-writer.desktop\napplication/pdf=AdobeReader.desktop\napplication/x-shellscript=gedit.desktop"  > ~/.local/share/applications/defaults.list

## Cairo-Dock prefs
rm -f -R ~/.config/cairo-dock
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/cairo-dock.zip" -O /tmp/cairo-dock.zip
unzip -o -d ~/.config/ /tmp/cairo-dock.zip
sudo rm -f /usr/share/cairo-dock/explosion.png
sudo wget "http://www.infiniteandbeyond.com/ubuntu/conf/explosion.png" -O /usr/share/cairo-dock/explosion.png

## Compiz prefs
rm -f -R ~/.gconf/apps/compiz/
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/compiz.zip" -O compiz.zip
unzip -o -d ~/.gconf/apps/ compiz.zip
rm -f compiz.zip

## Gnome-panel prefs
rm -f -R ~/.gconf/apps/panel/
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/panel.zip" -O panel.zip
unzip -o -d ~/.gconf/apps/ panel.zip
gconftool --set /apps/panel/toplevels/top_panel_screen0/background/image   --type=string "$HOME/.gconf/apps/panel/general/panel-background.png"
gconftool --set /apps/bluetooth-manager/icon_policy  --type=string "never"
rm -f panel.zip

## Virtualbox prefs
rm -f -R ~/.Virtualbox
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/VirtualBox.zip" -O VirtualBox.zip
unzip -o -d ~/ VirtualBox.zip
mv VirtualBox .VirtualBox
sudo chown -R $user .VirtualBox
chmod 755 -R .VirtualBox
# random MAC Address
tmp=`date|cut -d":" -f3|cut -d" " -f1`
sec=`echo $tmp`
tmp=`date|cut -d":" -f2`
min=`echo $tmp`
sed -i -e "s/<Adapter slot=\"0\" enabled=\"true\"  MACAddress=\"08002729A966\" cable=\"true\" speed=\"0\"  type=\"Am79C973\">/<Adapter slot=\"0\" enabled=\"true\"  MACAddress=\"080027"$min"A9"$sec"\" cable=\"true\" speed=\"0\"  type=\"Am79C973\">/g" ~/.VirtualBox/Machines/Windows XP/"Windows  XP.xml"
rm -f VirtualBox.zip

## Fix permissions
sudo chown -R "$user" .gconf
chmod 755 -R .gconf
sudo chown -R "$user" .config
chmod 755 -R .config
mkdir .kde
sudo chown -R "$user" .kde
chmod 755 -R ~/.kde

## Klipper prefs
mkdir ~/.kde/share/config/
echo -e "[General]\nIgnoreSelection=true\nMaxClipItems=2048" > ~/.kde/share/config/klipperrc
mkdir ~/.scripts
## hack in order to use klipper (starts 20 sec after login), klipper's autostart is in autostart.zip
echo -e "#!/bin/bash\n\nsleep 20\nklipper &" > ~/.scripts/klipper-login.sh
chmod 755 ~/.scripts/klipper-login.sh

## CUPS-PDF prefs
mkdir $HOME/PDF
sudo chmod 777 -R $HOME/PDF
nm=`hostname`
host=`echo $nm`
sudo cupsaddsmb -v -H "$host".local -U "$user"%"$pass" PDF
sudo sed -i -e "s/#UserUMask 0077/UserUMask 0000/g" /etc/cups/cups-pdf.conf

## Autostart prefs
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/autostart.zip" -O autostart.zip
unzip -o -d ~/.config/ autostart.zip
sed -i -e "s/Exec=sh ~\/.scripts\/klipper-login.sh/Exec=sh  \/home\/"$user"\/.scripts\/klipper-login.sh/g"  ~/.config/autostart/klipper.desktop
rm -f autostart.zip


## Hydroxygen Iconset
wget -U 'Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6)  Gecko/20070802 SeaMonkey/1.1.4' --progress=bar  "http://www.deviantart.com/download/100826865/hydroxygen_iconset_by_deviantdark.zip"  -O hydroxygen.zip
unzip hydroxygen.zip && tar xvjf iconset/hydroxygen*.tar.bz2  && mv hydroxygen ~/.icons  ## without "&&" seems to work  in async mode..
sudo rm -f ~/.icons/hydroxygen/icon-theme.cache
cd ~/.icons/hydroxygen/
./change-type.sh oxybluefolder
cd ~
rm -f hydroxygen.zip
rm -f -R iconset

## Icons Fixs
dim="16x16 22x22 24x24 32x32 48x48 72x72 128x128"
for pxs in $dim; do
    cd ~/.icons/hydroxygen/"$pxs"/places/
     
    if [ -f user-trash.png ];
    then
        mv user-trash.png user-trashOLD.png
        mv user-trash01.png user-trash.png
    fi
    
    cd ~/.icons/hydroxygen/"$pxs"/status/
    if [ -f trashcan_full-new.png ];
    then
        mv trashcan_full-new.png trashcan_full-newOLD.png
        mv trashcan_full01.png trashcan_full-new.png
    fi
    
    cd ~/.icons/hydroxygen/"$pxs"/mimetypes/
    
    if [ -f application-vnd.ms-word.png ];
    then
        mv application-vnd.ms-word.png application-vnd.ms-wordOLD.png
        cp /usr/share/icons/oxygen/"$pxs"/mimetypes/application-msword.png application-vnd.ms-word.png
        
        mv application-vnd.ms-excel.png application-vnd.ms-excelOLD.png
        cp /usr/share/icons/oxygen/"$pxs"/mimetypes/application-vnd.ms-excel.png application-vnd.ms-excel.png

    fi
    
    cd ~/.icons/hydroxygen/"$pxs"/apps/
    
    if [ -f openofficeorg-writer.png ];
    then
        mv openoffice.png openofficeOLD.png ## for cairo-dock document-type-based icons (above)
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-writer.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-writer.png
        mv openofficeorg-writer.png openofficeorg-writerOLD.png
        mv openofficeorg3-writer.png openofficeorg-writer.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-impress.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-impress.png
        mv openofficeorg-impress.png openofficeorg-impressOLD.png
        mv openofficeorg3-impress.png openofficeorg-impress.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-calc.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-calc.png
        mv openofficeorg-calc.png openofficeorg-calcOLD.png
        mv openofficeorg3-calc.png openofficeorg-calc.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-printeradmin.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-printeradmin.png
        mv openofficeorg-printeradmin.png openofficeorg-printeradminOLD.png
        mv openofficeorg3-printeradmin.png openofficeorg-printeradmin.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-math.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-math.png
        mv openofficeorg-math.png openofficeorg-mathOLD.png
        mv openofficeorg3-math.png openofficeorg-math.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-draw.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-draw.png
        mv openofficeorg-draw.png openofficeorg-drawOLD.png
        mv openofficeorg3-draw.png openofficeorg-draw.png
        
        wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/ooo/icons/$pxs/openofficeorg3-base.png"  -O ~/.icons/hydroxygen/"$pxs"/apps/openofficeorg3-base.png
        mv openofficeorg-base.png openofficeorg-baseOLD.png
        mv openofficeorg3-base.png openofficeorg-base.png
    fi
    
    if [ -f thunderbird.png ];
    then
        mv thunderbird.png thunderbirdOLD.png
        mv thunderbird-original.png thunderbird.png
    fi
    
    if [ -f skype.png ];
    then
        mv skype.png skypeOLD.png
        cp /usr/share/pixmaps/skype.png skype.png
        chmod 755 skype.png
    fi
    
    if [ -f skype.png ];
    then
        mv skype.png skypeOLD.png
        cp /usr/share/pixmaps/skype.png skype.png
        chmod 755 skype.png
    fi
    
done
cd ~
sudo chown -R "$user" .icons
chmod 755 -R ~/.icons
gconftool --set /desktop/gnome/interface/icon_theme --type string "hydroxygen"


## KDE4 GTK-Metacity theme
wget --progress=bar "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen.tar.gz" -O kde4-oxygen.tar.gz
tar -zxvf kde4-oxygen.tar.gz
mkdir ~/.themes
mv kde4-oxygen ~/.themes/kde4-oxygen
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "kde4-oxygen"
gconftool-2 --type string --set /apps/metacity/general/theme "kde4-oxygen"
rm -f kde4-oxygen.tar.gz


## KDE4 Theme Fixs
wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen-costum/progressbar.png"  -O ~/.themes/kde4-oxygen/gtk-2.0/others/progressbarN.png
cd ~/.themes/kde4-oxygen/gtk-2.0/others/
mv progressbar.png progressbarOLD.png
mv progressbarN.png progressbar.png
wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen-costum/progressbar-v.png"  -O ~/.themes/kde4-oxygen/gtk-2.0/others/progressbar-vN.png
cd ~/.themes/kde4-oxygen/gtk-2.0/others/
mv progressbar-v.png progressbar-vOLD.png
mv progressbar-vN.png progressbar-v.png

wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen-costum/slider-horiz.png"  -O ~/.themes/kde4-oxygen/gtk-2.0/Scrollbars/slider-horizN.png
cd ~/.themes/kde4-oxygen/gtk-2.0/Scrollbars/
mv slider-horiz.png slider-horizOLD.png
mv slider-horizN.png slider-horiz.png
wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen-costum/slider-vert.png"  -O ~/.themes/kde4-oxygen/gtk-2.0/Scrollbars/slider-vertN.png
cd ~/.themes/kde4-oxygen/gtk-2.0/Scrollbars/
mv slider-vert.png slider-vertOLD.png
mv slider-vertN.png slider-vert.png

cd ~/.themes/kde4-oxygen/metacity-1/
namex="button-close-focused button-close-pressed button-close-unfocused \
button-maximize-focused button-maximize-pressed button-maximize-unfocused \
button-minimize-focused button-minimize-pressed button-minimize-unfocused \
top_left top_right top un_top_left un_top_right un_top"
for xs in $namex; do
wget --progress=bar  "http://www.infiniteandbeyond.com/ubuntu/conf/kde4-oxygen-costum/$xs.png"  -O ~/.themes/kde4-oxygen/metacity-1/"$xs"N.png
mv "$xs".png "$xs"OLD.png
mv "$xs"N.png "$xs".png
done
cd ~

## Prelink Apps
sudo sed -i -e "s/PRELINKING=unknown/PRELINKING=yes/g" /etc/default/prelink
sudo /etc/cron.daily/prelink

## Apt-Get autoclean
sudo apt-get autoclean

## restoring sudo timeout
sudo sed -i -e "s/Defaults passwd_timeout=360//g" /etc/sudoers

## Clear the history of this script's command
history -c

rm -f examples.desktop

sudo reboot
```[/CODE][/QUOTE]

---

