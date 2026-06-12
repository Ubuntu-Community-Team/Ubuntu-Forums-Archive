---
title: "Script to automatically set up basic applications"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by Halcyon-X12 on 2005-06-28
Hi, I don't know if this will help anyone, but I've created a script that will set up a bunch of basic applications for you, or maybe you can just use it to get an idea how to make your own.  It was intended for Ubuntu Hoary 5.04.  As usual, I am not responsible if it doesn't work or you lose data.  Call it script.sh or something and right-click it, and in properties > permissions, select "Execute" for all users.  Open a commandline and run the script as root by typing sudo /path/to/script.sh:

```

#!/bin/sh

echo Be sure you are running this script as root \(type in a terminal: sudo $0\).

while true; do
  echo -n "Install development tools (only if you intend to compile applications)? (y/n) "
  read yn
  case $yn in
    y* | Y* ) INSTDEV=true ; break ;;
    [nN]* )   break ;;
    q* ) exit ;;
    * ) echo "unknown response.  Asking again" ;;
  esac
done

while true; do
  echo -n "Enable nVidia 3D acceleration? (y/n) "
  read yn
  case $yn in
    y* | Y* ) INSTNVID=true ; break ;;
    [nN]* )   break ;;
    q* ) exit ;;
    * ) echo "unknown response.  Asking again" ;;
  esac
done

while true; do
  echo -n "Install desktop icons?  Some applications may not appear on the applications menu, such as K3B and Apollon, and you would need to run them manually. (y/n) "
  read yn
  case $yn in
    y* | Y* ) INSTICONS=true ; break ;;
    [nN]* )   break ;;
    q* ) exit ;;
    * ) echo "unknown response.  Asking again" ;;
  esac
done  

# Get user

UHOMENAME=`ls /home`

while true; do
  echo -n "If $UHOMENAME is not your user name, please enter it now: "
  read yn
  case $yn in
    * ) if [ -d "/home/$yn" ] ; then 
	  set UHOMENAME = $yn
	  break
        else 
	  echo "Doesn't exist, try again."
        fi
  esac
done  

echo $UHOMENAME is your user name.

echo Updating applications database...

# Add apt database sources

echo -e deb http://security.ubuntu.com/ubuntu hoary-security universe\\ndeb-src http://security.ubuntu.com/ubuntu hoary-security universe\\ndeb http://archive.ubuntu.com/ubuntu hoary universe multiverse\\ndeb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse\\ndeb-src deb http://ubuntu.tower-net.de/ubuntu/ hoary java >> /etc/apt/sources.list

# Update apt database

apt-get -y update

# Install extra applications

echo Downloading new applications...

apt-get -y install nfs-kernel-server nfs-common samba openssh-server apollon libgnutella-gift libopenft-gift giftd gkrellm kopete licq k3b cdrdao beep-media-player mplayerplug-in vlc gftp wine winesetup kget gnomebaker sun-j2re1.5 flashplayer-mozilla unrar unace amule 

# Install dev environment

if [ "$INSTDEV" == "true" ]
then

echo Installing development environment

apt-get -y install libcrypto++-dev libglib-dev libgtk-dev libwxgtk-dev manpages-dev autoconf automake libtool flex bison gcc-doc g++ x-window-system-dev libpng-dev libgtk2.0-dev

fi

echo Downloading and installing mplayer fonts and codecs...

# Install mplayer fonts

wget http://ftp5.mplayerhq.hu/mplayer/releases/fonts/font-arial-iso-8859-1.tar.bz2 && tar -xjf font-arial-iso-8859-1.tar.bz2 && mkdir -p /usr/share/mplayer/font && cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/share/mplayer/font/ && rm -Rf font-arial-iso-8859-1 && rm font-arial-iso-8859-1.tar.bz2

# Install codecs

wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2 && tar -xjf essential-20050412.tar.bz2 && mkdir -p /usr/local/lib/codecs && cp essential-20050412/* /usr/local/lib/codecs && rm -Rf essential-20050412 && rm essential-20050412.tar.bz2

if [ $INSTICONS == "true" ]
then

echo Creating desktop icons...

# Create Gnome Baker icon

echo -e [Desktop Entry]\\nVersion=1.0\\nEncoding=UTF-8\\nName=No name\\nType=Application\\nExec=gnomebaker\\nTryExec=\\nX-GNOME-DocPath=\\nTerminal=false\\nName[en]=Gnome Baker\\nGenericName[en]=\\nComment[en]=\\nIcon=/usr/share/pixmaps/gnome-cd.png > /home/$UHOMENAME/Desktop/Gnome\ Baker\ \(CD-R\).desktop

# Create MPlayer icon

echo -e [Desktop Entry]\\nEncoding=UTF-8\\nVersion=1.0\\nType=Application\\nExec=gmplayer\\nTryExec=\\nIcon=/usr/share/pixmaps/mplayer.xpm\\nX-GNOME-DocPath=\\nTerminal=false\\nName[en]=MPlayer\\nGenericName[en]=\\nComment[en]= > /home/$UHOMENAME/Desktop/MPlayer.desktop

# Create K3B icon

echo -e [Desktop Entry]\\nEncoding=UTF-8\\nVersion=1.0\\nType=Application\\nExec=k3b\\nTryExec=\\nIcon=/usr/share/pixmaps/k3b.xpm\\nX-GNOME-DocPath=\\nTerminal=false\\nName[en]=K3B\\nGenericName[en]=\\nComment[en]= > /home/$UHOMENAME/Desktop/K3B\ \(CD-R\).desktop

# Create Apollon icon

echo -e [Desktop Entry]\\nEncoding=UTF-8\\nVersion=1.0\\nType=Application\\nExec=apollon\\nTryExec=\\nIcon=/usr/share/pixmaps/apollon.xpm\\nX-GNOME-DocPath=\\nTerminal=false\\nName[en]=Apollon\\nGenericName[en]=\\nComment[en]= > /home/$UHOMENAME/Desktop/Apollon\ \(P2P\).desktop

# Let the user access the desktop icons

chown $UHOMENAME:$UHOMENAME -R /home/$UHOMENAME/Desktop/*.desktop

fi

# Set up giftd

echo -e [main]\\nsetup = 1\\nhosts_allow = LOCAL\\nclient_port = 1213\\nfollow_symlinks = 1\\nplugins = OpenFT:Gnutella\\n[download]\\nincoming = ~/.giFT/incoming\\ncompleted = ~/.giFT/completed\\n[sharing]\\nmax_peruser_uploads = 1\\nhide_dot_files = 1\\nroot = \\nmax_uploads = 0\\nshares_hidden = 1\\nauto_resync_interval = 86400\\nshare_completed = 0\\nignore_incoming = 1\\n[bandwidth]\\ndownstream = 0\\nupstream = 0 > /home/$UHOMENAME/.giFT/giftd.conf && chown $UHOMENAME:$UHOMENAME /home/$UHOMENAME/.giFT/giftd.conf

# Enable nvidia drivers

if [ "$INSTNVID" == "true" ]
then

echo Enabling nVidia 3D...

apt-get -y install nvidia-glx

nvidia-glx-config enable

fi

```

---

### Post by rnaodm on 2005-06-28
awesome man thanks this may help me out. I am a super noob

---

### Post by Joeb on 2005-06-29
[QUOTE=rnaodm]awesome man thanks this may help me out. I am a super noob[/QUOTE]

You might be interested in this script, too:

[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)

It automatically installs a lot of things for you.

---

### Post by rnaodm on 2005-06-29
Cool time to boot back into ubunto and give it a try

---

### Post by Halcyon-X12 on 2005-06-29
You'll still have to associate the files with the programs though, such as avi, asf, wmv, mov, etc with mplayer, and mp3, ogg, etc with beep-media-player.

Thanks for the tip Joeb.  In my spare time I'm looking into incorporating stuff from that and making a graphical front end that lets you select the various options to install, and only installing stuff where appropriate (nvidia if you have an nvidia card, burning software if you have a burner, audio if you have a sound card, wine only if you have 32-bit and not 64-bit).

I'd also like to make a graphical file association editor...

I'd probably use perl to do it but I'm not sure what widgets library I'll use...  It's a little difficult to design dialogs in wxwidgets for example

---

