---
title: "Things to do after installing Ubuntu 14.04 Trusty Tahr"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2014-07-18
Someone made an AWESOME guide here: [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr)

I keep finding myself installing Ubuntu on other computers and going through this guide again. Because I'm a fan of shortcuts and laziness, I took all of the commands from the guide and compacted them into 1 MASSIVE command. I thought I might not be the only one who'd want this list, so I figured I'd post it. :biggrin:

I've incorporated some suggestions to the commands. The original is in [post 4]("http://ubuntuforums.org/showthread.php?t=2235066&p=13077541#post13077541") if you want to see.

-----EDIT-----

I uploaded a script to automate all of this.
[ATTACH]256408[/ATTACH]
Either you can copy and paste "the beast" command, or you can download this attached file and then run:
```
cd ~/Downloads && chmod +x ubuntu-basic-updates.sh && sudo sh ubuntu-basic-updates.sh
```

The beast:
```
sudo apt-get update || sudo apt-get install -yr gdebi aptitude &&
if [[ $(getconf LONG_BIT) = "64" ]]
then
    echo "64bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb &&
    sudo gdebi google-chrome-stable_current_amd64.deb &&
    rm -f google-chrome-stable_current_amd64.deb
else
    echo "32bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb &&
    sudo gdebi google-chrome-stable_current_i386.deb &&
    rm -f google-chrome-stable_current_i386.deb
fi &&

echo "Downloading GetDeb and PlayDeb" &&
wget http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb &&

echo "Installing GetDeb" &&
sudo gdebi getdeb-repository_0.1-1~getdeb1_all.deb &&

echo "Installing PlayDeb" &&
sudo gdebi playdeb_0.3-1~getdeb1_all.deb &&

echo "Deleting Downloads" &&
rm -f getdeb-repository_0.1-1~getdeb1_all.deb &&
rm -f playdeb_0.3-1~getdeb1_all.deb &&

sudo add-apt-repository -y ppa:videolan/stable-daily && sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp && sudo add-apt-repository -y ppa:gnome3-team/gnome3 && sudo add-apt-repository -y ppa:webupd8team/java && sudo add-apt-repository -y ppa:webupd8team/y-ppa-manager &&

echo 'deb http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
echo 'deb-src http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
wget -O - http://download.videolan.org/pub/debian/videolan-apt.asc|sudo apt-key add - &&

sudo aptitude update || sudo aptitude upgrade -y && sudo aptitude full-upgrade -y && sudo aptitude install -yr synaptic vlc gimp gimp-data gimp-plugin-registry gimp-data-extras y-ppa-manager bleachbit openjdk-7-jre oracle-java8-installer flashplugin-installer unace unrar zip unzip p7zip-full p7zip-rar sharutils rar uudeview mpack arj cabextract file-roller libxine1-ffmpeg mencoder flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview libmpeg3-1 mpeg3-utils mpegdemux liba52-dev mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 totem-mozilla icedax lame libmad0 libjpeg-progs libdvdcss2 libdvdread4 libdvdnav4 libswscale-extra-2 ubuntu-restricted-extras ubuntu-wallpapers* &&

echo "Cleaning Up" &&
sudo apt-get autoremove &&
sudo aptitude -y autoclean &&
sudo aptitude -y clean
```

---

### Post by TheFu on 2014-07-18
Installing .deb files directly is asking for repository dependency issues, if not now, later.

I prefer using aptitude over apt-get (as Debian recommended for a few years now). It tends to be smarter about dependencies.

Oh - and you left off all sorts of things - like purging unity-scope-*, unity-lens-* and nano. ;) Of course, installing xfce4 or lxde is smart before doing that.

Regardless, having a script to do these things is smart.  I like to make a list of all the packages from my old desktop with  dpkg --get-selections > file.lst; then put those onto a fresh install and import them - sudo  dpkg --set-selections < file.lst; to get the programs I have previously installed onto the new box.

---

### Post by GreenRaccoon on 2014-07-19
> **TheFu said:**
> Installing .deb files directly is asking for repository dependency issues, if not now, later.

I prefer using aptitude over apt-get (as Debian recommended for a few years now). It tends to be smarter about dependencies.

Oh - and you left off all sorts of things - like purging unity-scope-*, unity-lens-* and nano. ;) Of course, installing xfce4 or lxde is smart before doing that.

Regardless, having a script to do these things is smart.  I like to make a list of all the packages from my old desktop with  dpkg --get-selections > file.lst; then put those onto a fresh install and import them - sudo  dpkg --set-selections < file.lst; to get the programs I have previously installed onto the new box.

Haha I thought you were serious at first about purging those packages.

Whoa that "dpkg --get-selections > file.lst" command is awesome! I would've never figured out how to do that! I'm definitely going to be using that from now on.

---

### Post by GreenRaccoon on 2014-07-19
> **TheFu said:**
> Installing .deb files directly is asking for repository dependency issues, if not now, later.

I prefer using aptitude over apt-get (as Debian recommended for a few years now). It tends to be smarter about dependencies.

Oh - and you left off all sorts of things - like purging unity-scope-*, unity-lens-* and nano. ;) Of course, installing xfce4 or lxde is smart before doing that.

Regardless, having a script to do these things is smart.  I like to make a list of all the packages from my old desktop with  dpkg --get-selections > file.lst; then put those onto a fresh install and import them - sudo  dpkg --set-selections < file.lst; to get the programs I have previously installed onto the new box.

I like that suggestion. I'll incorporate it. Here's the original:

This first command does nothing. It's a fake command I do that to make it so I don't have to type in the sudo password later.
```
sudo /
```

Now the real commands.
```
if [[ $(getconf LONG_BIT) = "64" ]]
then
    echo "64bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb &&
    sudo dpkg -i google-chrome-stable_current_amd64.deb &&
    rm -f google-chrome-stable_current_amd64.deb
else
    echo "32bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb &&
    sudo dpkg -i google-chrome-stable_current_i386.deb &&
    rm -f google-chrome-stable_current_i386.deb
fi
```

The beast:
```
echo "Downloading GetDeb and PlayDeb" &&
wget http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb &&


echo "Installing GetDeb" &&
sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb &&


echo "Installing PlayDeb" &&
sudo dpkg -i playdeb_0.3-1~getdeb1_all.deb &&


echo "Deleting Downloads" &&
rm -f getdeb-repository_0.1-1~getdeb1_all.deb &&
rm -f playdeb_0.3-1~getdeb1_all.deb &&

sudo add-apt-repository -y ppa:videolan/stable-daily && sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp && sudo add-apt-repository -y ppa:gnome3-team/gnome3 && sudo add-apt-repository -y ppa:webupd8team/java && sudo add-apt-repository -y ppa:webupd8team/y-ppa-manager &&


echo 'deb http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
echo 'deb-src http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
wget -O - http://download.videolan.org/pub/debian/videolan-apt.asc|sudo apt-key add - &&


sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get install -y synaptic vlc gimp gimp-data gimp-plugin-registry gimp-data-extras y-ppa-manager bleachbit openjdk-7-jre oracle-java8-installer flashplugin-installer unace unrar zip unzip p7zip-full p7zip-rar sharutils rar uudeview mpack arj cabextract file-roller libxine1-ffmpeg mencoder flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview libmpeg3-1 mpeg3-utils mpegdemux liba52-dev mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 totem-mozilla icedax lame libmad0 libjpeg-progs libdvdcss2 libdvdread4 libdvdnav4 libswscale-extra-2 ubuntu-restricted-extras ubuntu-wallpapers* &&


echo "Cleaning Up" &&
sudo apt-get -f install &&
sudo apt-get autoremove &&
sudo apt-get -y autoclean &&
sudo apt-get -y clean
```

---

### Post by TheFu on 2014-07-19
I'd swap apt-get for aptitude. It isn't installed by default anymore, but it is can resolve dependency issues that apt-get cannot.  This has been important to me when using mariaDB (replacement for mysql). There have been other times too.

Anyone interested in doing this through **ansible playbook** instead of a script?  I've been building machines with ansible for about 6 months. Before that, I'd dabbled with ansible, rexify, puppet, chef, salt, and shell scripts for the last  ... er ... 20 yrs.
My first 5 minutes on a server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) ... this is the base for my desktops too.

Oh - and I was completely serious about purging those packages. 100%. They don't add anything useful to my computing environment, so why have them loaded? Others may love, love, love them, which is fine. Customization is a valid reason for running Linux.

---

### Post by GreenRaccoon on 2014-07-20
=;> **TheFu said:**
> I'd swap apt-get for aptitude. It isn't installed by default anymore, but it is can resolve dependency issues that apt-get cannot.  This has been important to me when using mariaDB (replacement for mysql). There have been other times too.

Anyone interested in doing this through **ansible playbook** instead of a script?  I've been building machines with ansible for about 6 months. Before that, I'd dabbled with ansible, rexify, puppet, chef, salt, and shell scripts for the last  ... er ... 20 yrs.
My first 5 minutes on a server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) ... this is the base for my desktops too.

Oh - and I was completely serious about purging those packages. 100%. They don't add anything useful to my computing environment, so why have them loaded? Others may love, love, love them, which is fine. Customization is a valid reason for running Linux.
I didn't know what the sense and lens packages were, but I just looked them up. I didn't know you could uninstall those! I don't use them either. I'll uninstall them too. :biggrin:

Yes, that's the main reason I use Linux over Windows: cause the possibilities are endless. That and because Windows has all of these little, annoying things that drive me crazy. When I'm using Windows, I feel like a kid is poking me repeatedly with a pen. Like the other day I was in the middle of a full screen game when Windows decided to kick me off and ask me if I wanted to update Java. "Yes Windows, I know Java's important, but you literally just killed me. Get your priorities in line." And of course, the Java automatic update didn't work like it hasn't in the past 2 billion versions.

I'm rambling. With all that said, I still think Windows is a great OS, just not my favorite OS.

---

### Post by Raj_Sanmugam on 2014-09-18
I ran this script file. It runs smoothly until it prompts for "end user microsoft license agreement for EULA" I tried to press enter to agree to the terms 'ok' but it is hanging... anyone had similar problems?

---

### Post by echotech2 on 2014-09-18
TAB 'til "OK" is highlighted, hit "ENTER"

---

### Post by Raj_Sanmugam on 2014-09-19
Great that worked, thanks echotech2

---

