---
title: "Who wants to help with a script that installs things like Java Update 2?"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Tea4all on 2007-07-27
I have made a script to install Java update 2 and other things. I was hoping for some ideas!  And please don't say it looks like a 12 year old put it together!  FYI I AM 12 YEARS OLD!  Help would be appreciated!

```
#!/bin/sh
# This is a script to install commonly used applications.
# To allow this to execute, type sudo chmod ugo+x "The Feature Installer.sh"
clear 
echo "Hello $USERNAME."
sleep 2
echo "This is a script to install commonly used applications."
sleep 2
echo "Today is `date`."
sleep 2
echo "You have"
df -h /home/tea4all
echo "left of space."
sleep 1.5
echo "You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work."
echo
echo "You MUST execute this script from the $HOME folder!" 
echo
echo "To enable the Commercial repository, go to System > Administration > Software Sources.  Then go to the Third Party Software tab and click add. Copy and paste    deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 5
echo "Answer 1 for yes and 2 for no."
sleep 2
if [ `pwd` = $HOME ]
then echo "You're in the `pwd` folder!"
else echo "You must execute this script from the $HOME folder!"
exit
fi 
sudo apt-get install -y nautilus-open-terminal
echo "Do you want to enable the Medibuntu repository?"
read a17
if [ $a17 -eq 1 ]
then 
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to enable the wine respository? (for latest wine)"
read a51
if [ $a51 -eq 1 ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to enable encrypted DVD support?"
read a1
if [ $a1 -eq 1 ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install all ripping codacs (for Sound Juicer and movie rippers)?"
read a2
if [ $a2 -eq 1 ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox   
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install all gstreamer plugins $USERNAME ?"
read a3
if [ $a3 -eq 1 ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install all xine plugins?"
read a50
if [ $a50 -eq 1 ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install all Linux Compression Formats?"
read a10
if [ $a10 -eq 1 ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace 
else echo "OK"
fi
echo "exit code $?"
echo "Do you wish to install the Wine windows emulator? (to run windows programs) (command line)"
read a12
if [ $a12 -eq 1 ]
then
sudo apt-get install -y wine msttcorefonts
echo 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo "or http://frankscorner.org/"
echo
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
echo
else echo "OK"
fi
echo "exit code $?"
# This installs the Sun Java 6 package, and overwrites it with Sun Java 6 Update 2
echo "Do you wish to enable sun-java 6?"
read a4
if [ $a4 -eq 1 ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
sudo chmod ugo+x jre6.bin
./jre6.bin
sudo cp -r /home/$USERNAME/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo cp -r /home/$USERNAME/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
sudo rm -r jre6.bin
sudo rm -r jre1.6.0_02
java -version
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install the Adobe Flashplayer?"
read b20
if [ $b20 -eq 1 ]
then sudo apt-get install -y flashplugin-nonfree
else echo "OK"
fi 
echo "exit code $?"
echo "If the field below says "direct rendering: Yes" then you already have 3D acceleration enabled!" 
glxinfo | grep render
echo "Do you wish to enable 3D acceleration?"
read a6
if [ $a6 -eq 1 ]
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sudo restricted-manager
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install java 3D? (You must have 3D enabled and Java installed!)"
read a55
if [ $a55 -eq 1 ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
unzip java3d.zip
rm -r java3d.zip
cd /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo unzip $HOME/java3d-1_5_1-linux-i586/j3d-jre.zip
cd lib/i386/
sudo ln libj3dcore-ogl.so /usr/lib/firefox/plugins/
cd $HOME
rm -r java3d-1_5_1-linux-i586
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install alien (for RPM packages)"
read b1
if [ $b1 -eq 1 ]
then sudo apt-get install -y alien
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to install gDesklets? (for really cool effects like the mac bar)"
read d1  
if [ $d1 -eq 1 ]
then sudo apt-get install -y gdesklets
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
else echo "OK"
fi 
echo "exit code $?"
echo "Would you want to install a firewall?"
read f1 
if [ $f1 -eq 1 ]
then sudo apt-get install -y firestarter
else echo "OK"
fi 
echo "exit code $?"
echo "Remove unused applications?"
read a7
if [ $a7 -eq 1 ]
then 
sudo apt-get autoremove
else echo "OK"
fi
echo "exit code $?"
echo "Do you want to update your computer now?"
read a9
if [ $a9 -eq 1 ]
then 
sudo apt-get -y upgrade
else echo "OK"
fi
echo "exit code $?"
echo "To complete these actions your computer must be restarted. Reboot now?"
read a8
if [ $a8 -eq 1 ]
then
echo "goodbye!"
sleep 6
sudo reboot 
else echo "goodbye!"
fi
echo "exit code $?"
exit 

```  :lolflag:

---

### Post by Tea4all on 2007-07-27
please send a private message for a reply!:guitar:

---

