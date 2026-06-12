---
title: "Who wants to help with a shell script?"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by Tea4all on 2007-08-01
Well here it is!  Tell me how I can improve!
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
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<control><alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
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
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs 
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
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
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

```
And here is my other (less useful) one.```
#!/bin/sh
# Yor hed e SPLODE HE HE HE!!!
clear
echo "Self Destruct in 10 seconds"
sleep 1
clear
echo "Self Destruct in 9 seconds"
sleep 1
clear 
echo "Self Destruct in 8 seconds"
sleep 1
clear
echo "Self Destruct in 7 seconds"
sleep 1
clear
echo "Self Destruct in 6 seconds"
sleep 1
clear
echo "Self Destruct in 5 seconds"
sleep 1
clear
echo "Self Destruct in 4 seconds"
sleep 1
clear
echo "Self Destruct in 3 seconds"
sleep 1
clear
echo "Self Destruct in 2 seconds"
sleep 1
clear
echo "Self Destruct in 1 second"
sleep 1
clear
echo -e "\a"
sleep 1
echo -e "\a"
sleep .7
echo -e "\a"
sleep .7
echo -e "\a"
sleep .7
echo -e "\a"
sleep .6
echo -e "\a"
sleep .6
echo -e "\a"
sleep .4
echo -e "\a"
sleep .4
echo -e "\a"
sleep .4
echo -e "\a"
sleep .4
echo -e "\a"
sleep .2
echo -e "\a"
sleep .2
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo -e "\a"
sleep .1
echo " __________   __________    ___________    ____   ____"
echo "|          | |          |  |           |  |     \/     |"
echo "|          | |          |  |           |  |      |     |"
echo "|      ___/  |          |  |           |  |      |     |"
echo "|         \  |          |  |           |  |      |     |"
echo "|          | |          |  |           |  |      |     |"
echo "~~~~~~~~~~~~  ~~~~~~~~~~    ~~~~~~~~~~~"
echo "U ded now"  
```

---

### Post by nichipet on 2007-08-01
Alright, let's see. Everything is made much easier if the script has no spaces in its filename. So maybe TheFeatureInstaller.sh instead.

All of your extra echo's could be put on the same line as the previous statement. For example:

```
echo "You MUST execute this script from the $HOME folder!"; echo
```

It saves space, makes the file smaller, fewer lines to deal with when troubleshooting, and so on.

I assume this will be distributed to other people and used only once, otherwise the instructions on enabling repositories become tedious after you added repositories five or six logins ago.

In direct rendering, you need to escape the quotation marks:

```
echo "If the field below says \"direct rendering: Yes\" then you already have 3D acceleration enabled!"
```

Have you tried running the script to make sure it all works?

---

### Post by Motoxrdude on 2007-08-01
Yeah ill help you out. Give me about an hour to work through it all.

---

### Post by Motoxrdude on 2007-08-01
Here it is!  This is how you can improve!
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
df -h /home/tea4all #Don't use your home directory, instead use "~" as this will work as                          everyone's home directory

echo "left of space."
sleep 1.5
echo "You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work."
echo
echo "You MUST execute this script from the $HOME folder!"  #Why tell us and not give us an option to quit? Also, this is uneccesary as you have an if/then later on.
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
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<control><alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
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
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs 
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
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
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
```
 Your program looks pretty good for a first timer. You might want to make it so you can select all your programs then at the end install them all. This just makes it more pleasent for the person using the program so i dont have to wait for the program to install before it asks to install again. If you want i can add to your script and make it a little more polished. Also i can add a GUI to make it more user friendly ;)

O and try and make the script more readable. By simply adding a paragraph between each if/then it would make it a lot more pleasent to read.

I basicly added a gui to your program. I tried to not mess with it too much. I just made it a little easier to read and used zenity to see what programs you want to install.
```

#!/bin/sh
# This is a script to install commonly used applications.
# To allow this to execute, type sudo chmod 775 "The Feature Installer.sh"
clear 
gksudo apt-get update
#Is zenity installed?
if [ ! -e "/usr/bin/zenity" ]; then
	gksudo apt-get install -y zenity
fi

#Getting accuainted with the script
zenity --info --title="The Feature Installer" --text="Hello $USERNAME. This is a script to install commonly used applications. Today is `date`."
zenity --info --title="The Feature Installer" --text="`df -h ~`"
zenity --info --title="The Feature Installer" --text="You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work."
zenity --info --title="The Feature Installer" --text="You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work. To enable the Commercial repository, go to System > Administration > Software Sources.  Then go to the Third Party Software tab and click add. Copy and paste    deb http://archive.canonical.com/ubuntu feisty-commercial main."
zenity --info --title="The Feature Installer" --text="Also you may want to check things on this program! Especially the feisty-backports!"

if [ ! `pwd` = $HOME ]; then
echo zenity --info --title="The Feature Installer" --text="You're in the `pwd` folder! You must execute this script from the $HOME folder!"
exit
fi 

sudo apt-get install -y nautilus-open-terminal
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<control><alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

zenity --question --title="The Feature Installer" --text="Do you want to enable the Medibuntu repository?"
if [ $? = 0 ]; then 
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
fi

zenity --question --title="The Feature Installer" --text="Do you want to enable the wine repository? (for latest version wine)"
if [ $? = 0 ]; then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
fi

zenity --question --title="The Feature Installer" --text="Do you want to update your computer now?"
if [ $? = 0 ]; then 
sudo apt-get -y upgrade
fi

zenity --question --title="The Feature Installer" --text="Do you want to enable encrypted DVD support?"
if [ $? = 0 ]; then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
fi


zenity --question --title="The Feature Installer" --text="Do you want to install all ripping codacs (for Sound Juicer and movie rippers)?"
if [ $? = 0 ]; then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox   
zenity --info --title="The Feature Installer" --text="To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
fi

zenity --question --title="The Feature Installer" --text="Do you want to install all gstreamer plugins $USERNAME ?"
if [ $? = 0 ]; then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs 
else echo "OK"
fi

zenity --question --title="The Feature Installer" --text="Do you want to install all xine plugins?"
if [ $? = 0 ]; then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
fi


zenity --question --title="The Feature Installer" --text="Do you want to install all Linux Compression Formats?"
if [ $? = 0 ]; then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace 
fi

zenity --question --title="The Feature Installer" --text="Do you wish to install the Wine windows emulator? (to run windows programs) (command line)"
if [ $? = 0 ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
zenity --info --title="The Feature Installer" --text="For information about getting programs to work, go to http://appdb.winehq.org/ or http://frankscorner.org/ For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
fi


# This installs the Sun Java 6 package, and overwrites it with Sun Java 6 Update 2
zenity --question --title="The Feature Installer" --text="Do you wish to enable sun-java 6?"
if [ $? = 0 ]; then
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
fi

zenity --question --title="The Feature Installer" --text="Do you want to install the Adobe Flashplayer?"
if [ $? = 0 ]; then
sudo apt-get install -y flashplugin-nonfree
fi 

glxinfo=`glxinfo | grep direct`
zenity --info --title="The Feature Installer" --text=" If the field below says ''direct rendering: Yes'' then you already have 3D acceleration enabled:      $glxinfo" 
zenity --question --title="The Feature Installer" --text="Do you wish to enable 3D acceleration?"
if [ $? = 0 ]; then
zenity --info --title="The Feature Installer" --text="You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sudo restricted-manager
fi


zenity --question --title="The Feature Installer" --text="Do you want to install java 3D? (You must have 3D enabled and Java installed!)"
if [ $? = 0 ];then
wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
unzip java3d.zip
rm -r java3d.zip
cd /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
sudo unzip $HOME/java3d-1_5_1-linux-i586/j3d-jre.zip
cd lib/i386/
sudo ln libj3dcore-ogl.so /usr/lib/firefox/plugins/
cd $HOME
rm -r java3d-1_5_1-linux-i586
fi


zenity --question --title="The Feature Installer" --text="Do you want to install alien (for RPM packages)"
if [ $? = 0 ]; then
sudo apt-get install -y alien
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
else echo "OK"
fi

zenity --question --title="The Feature Installer" --text="Do you want to install gDesklets? (for really cool effects like the mac bar)"

if [ $? = 0 ]; then
sudo apt-get install -y gdesklets
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
fi 

zenity --question --title="The Feature Installer" --text="Would you want to install a firewall?"
if [ $? = 0 ]; then
sudo apt-get install -y firestarter
fi 


zenity --question --title="The Feature Installer" --text="Remove unused dependencies? This will free some extra space. Don't worry it is completely safe"
if [ $? = 0 ]; then 
sudo apt-get autoremove
fi

zenity --info --title="The Feature Installer" --text="Thanks for using this program! It is advised that you do a restart if you installed a driver via restricted-drivers-managment."

zenity --question --title="The Feature Installer" --text="Reboot now?"
if [ $? = 0 ]
then
sudo shutdown -r now
fi

exit

```

---

### Post by Tea4all on 2007-08-06
```
#!/bin/sh
# This is a script to install commonly used applications.
# To allow this to execute, type sudo chmod ugo+x "The Feature Installer.sh"
clear 
echo "Hello $USERNAME."
sleep 3
echo
echo "This is a script to install commonly used applications."
sleep 5
echo
echo "Today is `date`."
sleep 5
echo
echo "You have"
df -h ~
echo "left of space."
sleep 5
echo
echo "You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work."
echo
sleep 6
echo
echo
echo "An exit status of 0 means everything was OK. Otherwise there was a error."
sleep 6
echo
echo
echo
#sudo apt-get install -y nautilus-open-terminal
#gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<control><alt>Delete"
#gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
echo
echo "Do you want to enable the extra repositories?"
read a17
if [ $a17 = y ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space
if [ $a17 = Y ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space
if [ $a17 = Yes ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi 
# space
if [ $a17 = yes ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space
if [ $a17 = yEs ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space 
if [ $a17 = YeS ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space
if [ $a17 = YES ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space 
if [ $a17 = yeS ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
# space 
if [ $a17 = 1 ]
then 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
echo "exit code $?"
clear
echo "To enable the Commercial repository, Go to the Third Party Software tab and click add. Copy and paste"
echo
echo "deb http://archive.canonical.com/ubuntu feisty-commercial main"
echo
echo "Also you may want to check things on this program! Especially the feisty-backports!"
sleep 10
echo
sudo /usr/bin/software-properties-gtk
echo
else sleep 0
echo
fi
echo "Do you want to enable the wine respository? (for latest wine)"
read a51
if [ $a51 = 1 ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a51 = y ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a51 = Y ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a51 = Yes ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a51 = yes ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a51 = YES ]
then
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
echo "exit code $?"
sudo apt-get update
echo "exit code $?"
echo
else sleep 0
echo
fi
echo "Do you want to enable encrypted DVD support?"
read a1
if [ $a1 = 1 ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a1 = y ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a1 = Y ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a1 = yes ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a1 = Yes ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
if [ $a1 = YES ]
then 
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs 
echo "exit code $?"
echo
else sleep 0
echo
fi
# space
echo "Do you want to install all ripping codacs (for Sound Juicer and movie rippers)?"
read a2
if [ $a2 = 1 ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
if [ $a2 = y ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
if [ $a2 = Y ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
if [ $a2 = yes ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
if [ $a2 = Yes ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
if [ $a2 = YES ]
then 
sudo apt-get install -y lame faac toolame mencoder wavpack sox
echo "exit code $?"   
sleep 2
echo
echo
echo "To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
# space
echo "Do you want to install all gstreamer plugins $USERNAME ?"
read a3
if [ $a3 = 1 ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a3 = y ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a3 = Y ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a3 = yes ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a3 = Yes ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a3 = YES ]
then
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
echo "exit code $?"
echo 
else sleep 0
fi
# space
echo "Do you want to install all xine plugins?"
read a50
if [ $a50 = 1 ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
if [ $a50 = y ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
if [ $a50 = Y ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
if [ $a50 = Yes ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
if [ $a50 = yes ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
if [ $a50 = YES ]
then sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs
echo "exit code $?"
echo
else sleep 0
fi
# space
echo "Do you want to install all Linux Compression Formats?"
read a10
if [ $a10 = 1 ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a10 = y ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a10 = Y ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a10 = Yes ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a10 = yes ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
if [ $a10 = YES ]
then 
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace
echo "exit code $?"
echo 
else sleep 0
fi
# space
echo "Do you wish to install the Wine windows emulator? (to run windows programs) (command line)"
read a12
if [ $a12 = 1 ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
if [ $a12 = y ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
if [ $a12 = Y ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
if [ $a12 = Yes ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
if [ $a12 = yes ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
if [ $a12 = YES ]
then
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title
echo "exit code $?"
echo
clear 
echo "For information about getting programs to work, go to http://appdb.winehq.org/"
echo
echo "or http://frankscorner.org/"
echo
sleep 11
echo
echo "For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index"
echo
sleep 6
echo
echo "Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
echo
sleep 10
echo
else sleep 0
fi
# space
# This installs the Sun Java 6 package, and overwrites it with Sun Java 6 Update 2
echo "Do you wish to enable sun-java 6?"
read a4
if [ $a4 = 1 ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
if [ $a4 = y ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
if [ $a4 = Y ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
if [ $a4 = Yes ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
if [ $a4 = yes ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
if [ $a4 = YES ]
then
sudo apt-get install -y sun-java6-jre sun-java6-plugin
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284"
echo "exit code $?"
sudo chmod ugo+x jre6.bin
echo "exit code $?"
./jre6.bin
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/
echo "exit code $?"
sudo rm -r jre6.bin
echo "exit code $?"
sudo rm -r jre1.6.0_02
echo "exit code $?"
echo
java -version
echo
else sleep 0
fi
# space
echo "Do you want to install the Adobe Flashplayer?"
read b20
if [ $b20 = 1 ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
elif [ $b20 = y ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
elif [ $b20 = Y ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
elif [ $b20 = Yes ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
elif [ $b20 = yes ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
elif [ $b20 = YES ]
then sudo apt-get install -y flashplugin-nonfree
echo "exit code $?"
echo
else sleep 0
fi 
# space
echo "If the field below says direct rendering: Yes then you already have 3D acceleration enabled!" 
echo
glxinfo | grep render
echo
echo "Do you wish to enable 3D acceleration?"
read a6
if [ $a6 = 1 ]
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
elif [ $a6 = y ] 
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
elif [ $a6 = Y ] 
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
elif [ $a6 = Yes ] 
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
elif [ $a6 = yes ] 
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
elif [ $a6 = YES ] 
then echo "You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sleep 5
sudo restricted-manager
echo
else sleep 0
fi
echo "Do you want to install Java 3D? (You must have 3D enabled and Java installed!)"
read a55
if [ $a55 = 1 ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
elif [ $a55 = y ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
elif [ $a55 = Y ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
elif [ $a55 = Yes ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
elif [ $a55 = yes ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
elif [ $a55 = YES ]
then wget --output-document=java3d.zip http://download.java.net/media/java3d/builds/release/1.5.1/java3d-1_5_1-linux-i586.zip
echo "exit code $?"
unzip java3d.zip
echo "exit code $?"
rm -r java3d.zip
echo "exit code $?"
sudo unzip $PWD/java3d-1_5_1-linux-i586/j3d-jre.zip /usr/lib/jvm/java-6-sun-1.6.0.00/jre/
echo "exit code $?"
sudo ln /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so /usr/lib/firefox/plugins/
echo "exit code $?"
rm -r java3d-1_5_1-linux-i586
echo "exit code $?"
echo
else sleep 0
echo
fi
echo "Do you want to install alien (for RPM packages)"
read b1
if [ $b1 = 1 ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
elif [ $b1 = y  ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
elif [ $b1 = Y  ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
elif [ $b1 = Yes  ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
elif [ $b1 = yes  ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
elif [ $b1 = YES  ]
then sudo apt-get install -y alien
echo "exit code $?"
echo
echo "To install RPMs type sudo alien -i nameofrpm.rpm"
sleep 4
echo
else sleep 0
echo
fi
echo "Do you want to install gDesklets? (for really cool effects like the mac bar)"
read d1  
if [ $d1 = 1 ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
elif [ $d1 = y ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
elif [ $d1 = Y ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
elif [ $d1 = Yes ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
elif [ $d1 = yes ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
elif [ $d1 = YES ]
then sudo apt-get install -y gdesklets
echo "exit code $?"
echo "Add the command gdesklets to startup!"
sleep 4
gnome-session-properties
echo
else sleep 0
echo
fi 
echo "Would you want to install a firewall?"
read f1 
if [ $f1 = 1 ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
elif [ $f1 = y ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
elif [ $f1 = Y ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
elif [ $f1 = Yes ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
elif [ $f1 = yes ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
elif [ $f1 = YES ]
then sudo apt-get install -y firestarter
echo "exit code $?"
echo
else sleep 0
echo
fi 
echo "Remove unused applications?"
read a7
if [ $a7 = 1 ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
elif [ $a7 = y ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
elif [ $a7 = Y ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
elif [ $a7 = Yes ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
elif [ $a7 = yes ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
elif [ $a7 = YES ]
then 
sudo apt-get autoremove
echo "exit code $?"
echo
else sleep 0
echo
fi
echo "Do you want to update your computer now?"
read a9
if [ $a9 = 1 ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
elif [ $a9 = y ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
elif [ $a9 = Y ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
elif [ $a9 = Yes ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
elif [ $a9 = yes ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
elif [ $a9 = YES ]
then 
sudo apt-get -y upgrade
echo "exit code $?"
echo
else sleep 0
echo
fi
echo "To complete these actions your computer must be restarted. Reboot now?"
read a8
if [ $a8 = 1 ]
then
echo "goodbye!"
sleep 6
sudo reboot 
elif [ $a8 = y ]
then
echo "goodbye!"
sleep 6
sudo reboot
elif [ $a8 = Y ]
then
echo "goodbye!"
sleep 6
sudo reboot
elif [ $a8 = Yes ]
then
echo "goodbye!"
sleep 6
sudo reboot
elif [ $a8 = yes ]
then
echo "goodbye!"
sleep 6
sudo reboot
elif [ $a8 = YES ]
then
echo "goodbye!"
sleep 6
sudo reboot
else echo "goodbye!"
sleep 6
fi
exit 0 

```

---

### Post by Tea4all on 2007-08-06
Now I just need help with that GUI please:lolflag:

---

### Post by Tea4all on 2007-08-06
Here is the finished product! ```
#!/bin/sh
# This is a script to install commonly used applications.
# To allow this to execute, type sudo chmod ugo+x "The Feature Installer.sh"
clear 
#Is zenity installed?
if [ ! -e "/usr/bin/zenity" ]; then
	gksudo apt-get install -y zenity
fi

zenity --info --title="The Feature Installer" --text "Hello $USERNAME. This is a script to install commonly used applications. Today is `date`. You must add the Medibuntu and the Commercial repositories and have Internet access for this script to work."
#sudo apt-get install -y nautilus-open-terminal
#gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<control><alt>Delete"
#gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
zenity --question --title="The Feature Installer" --text "Do you want to enable the extra repositories?"
if [ $? = 0 ]
then 
gnome-terminal -x sudo echo "OK"
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig | zenity --progress --pulsate --auto-close  
echo "exit code $?"
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list | zenity --progress --pulsate --auto-close 
echo "exit code $?"
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list | zenity --progress --pulsate --auto-close
echo "exit code $?"
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update | zenity --progress --pulsate --auto-close 
echo "exit code $?"
zenity --info --title="The Feature Installer" --text="To enable the Commercial repository, Go to System > Administration > Software Sources. Then go to the Third Party Software tab and click add. Copy and paste deb http://archive.canonical.com/ubuntu feisty-commercial main  Also you may want to check things on this program! Especially the feisty-backports"
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to enable the wine respository? (for latest wine)"
if [ $? = 0 ]
then
gnome-terminal -x sudo echo "OK"
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - | zenity --progress --pulsate --auto-close 
echo "exit code $?"
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo apt-get update | zenity --progress --pulsate --auto-close
echo "exit code $?"
echo
else sleep 0
echo
fi
zenity --question --title="The Feature Installer" --text="Do you want to enable encrypted DVD support?"
if [ $? = 0 ]
then 
gnome-terminal -x sudo echo "OK"
sudo apt-get install -y totem-xine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 libxine1-plugins w32codecs libxine-extracodecs | zenity --progress --pulsate --auto-close 
echo "exit code $?"
echo
else sleep 0
echo
fi
zenity --question --title="The Feature Installer" --text="Do you want to install all gstreamer plugins $USERNAME ?"
if [ $? = 0 ]
then
gnome-terminal -x sudo echo "OK"
sudo apt-get install -y gstreamer0.8-plugins w32codecs gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs | zenity --progress --pulsate --auto-close 
echo "exit code $?"
echo 
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to install all ripping codacs (for Sound Juicer and movie rippers)?"
if [ $? = 0 ]
then 
gnome-terminal -x sudo echo "OK"
sudo apt-get install -y lame faac toolame mencoder wavpack sox | zenity --progress --pulsate --auto-close 
echo "exit code $?"   
echo
echo
zenity --info --title="The Feature Installer" --text="To rip mp3 files in Sound Juicer, go to Edit > Preferences. Change output format to CD Quality, MP3 (MP3 audio)"     
else sleep 0
echo
fi
zenity --question --title="The Feature Installer" --text="Do you want to install all xine plugins?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y libxine1-plugins w32codecs libxine-extracodecs | zenity --progress --pulsate --auto-close 
echo "exit code $?"
echo
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to install all Linux Compression Formats?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y rar unrar unzoo zoo p7zip-full zip unzip rpm bzip2 gzip unace | zenity --progress --pulsate --auto-close 
echo "exit code $?"
echo 
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you wish to install the Wine windows emulator? (to run windows programs) (command line)"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y wine msttcorefonts ttf-ubuntu-title | zenity --progress --pulsate --auto-close
echo "exit code $?"
echo
zenity --info --title="The Feature Installer" --text="For information about getting programs to work, go to http://appdb.winehq.org/ or http://frankscorner.org/ For info about wine, go to http://winehq.org/site/docs/wineusr-guide/index	Remember Wine is command line! To run go to Applications> Accessories> Terminal, type cd /media/cdrom0 or where ever your .exe file is located (my example is the cd drive), type ls to tell you the name and type wine nameofexefile.exe"
else sleep 0
fi
# This installs the Sun Java 6 package, and overwrites it with Sun Java 6 Update 2
zenity --question --title="The Feature Installer" --text="Do you wish to enable sun-java 6 update 2?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y sun-java6-jre sun-java6-plugin | zenity --progress --pulsate --auto-close
echo "exit code $?"
wget --output-document=jre6.bin -c "http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284" | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo chmod ugo+x jre6.bin | zenity --progress --pulsate --auto-close 
echo "exit code $?"
./jre6.bin | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/bin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/lib /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/man /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/plugin /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/COPYRIGHT /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/LICENSE /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/README /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/THIRDPARTYLICENSEREADME.txt /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/Welcome.html /usr/lib/jvm/java-6-sun-1.6.0.00/jre/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo cp -r $PWD/jre1.6.0_02/javaws/javaws /usr/lib/jvm/java-6-sun-1.6.0.00/jre/javaws/ | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo rm -r jre6.bin | zenity --progress --pulsate --auto-close
echo "exit code $?"
sudo rm -r jre1.6.0_02 | zenity --progress --pulsate --auto-close
echo "exit code $?"
echo
zenity --info --title="The Feature Installer" --text="`java -version`"
echo
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to install the Adobe Flashplayer?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y flashplugin-nonfree | zenity --progress --pulsate --auto-close
echo "exit code $?"
echo
else sleep 0
fi 

glxinfo=`glxinfo | grep direct`
zenity --info --title="The Feature Installer" --text=" If the field below says ''direct rendering: Yes'' then you already have 3D acceleration enabled:      $glxinfo" 
zenity --question --title="The Feature Installer" --text="Do you wish to enable 3D acceleration?"
if [ $? = 0 ]; then gnome-terminal -x sudo echo "OK"
zenity --info --title="The Feature Installer" --text="You can enable it just by checking it in the window that pops up! Then X out of it to continue."
sudo restricted-manager
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to install alien (for RPM packages)?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y alien | zenity --progress --pulsate --auto-close
echo "exit code $?"
echo
zenity --info --title="The Feature Installer" --text="To install RPMs type sudo alien -i nameofrpm.rpm into a terminal"
echo
else sleep 0
fi
zenity --question --title="The Feature Installer" --text="Do you want to install gDesklets? (for really cool effects like the mac bar)"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo apt-get install -y gdesklets | zenity --progress --pulsate --auto-close
echo "exit code $?"
zenity --warning --title="The Feature Installer" --text="Add the command gdesklets to startup"
gnome-session-properties
echo
else sleep 0
echo
fi 

zenity --question --title="The Feature Installer" --text="Do you want to install a firewall?"
if [ $? = 0 ]; then gnome-terminal -x sudo echo "OK" 
sudo apt-get install -y firestarter | zenity --progress --pulsate --auto-close
fi 

zenity --question --title="The Feature Installer" --text="Remove unused dependencies? This will free some extra space. Don't worry it is completely safe"
if [ $? = 0 ]; then
gnome-terminal -x sudo echo "OK"
sudo apt-get autoremove | zenity --progress --pulsate --auto-close
fi

zenity --question --title="The Feature Installer" --text="Do you want to update your computer now?"
if [ $? = 0 ]; then gnome-terminal -x sudo echo "OK"
sudo apt-get -y upgrade | zenity --progress --pulsate --auto-close
fi

zenity --info --title="The Feature Installer" --text="Thanks for using this program! It is advised that you do a restart if you installed a driver via restricted-drivers-managment."

zenity --question --title="The Feature Installer" --text="Reboot now?"
if [ $? = 0 ]
then gnome-terminal -x sudo echo "OK"
sudo shutdown -r now
fi
exit 

```

---

### Post by Motoxrdude on 2007-08-11
Looking good. Do you want me to make it so it's a menu instead of having to go one at a time?

---

### Post by Tea4all on 2007-08-13
Sure! E-mail me at [email]trevorschauls@gmail.com[/email] with the finnished prodect!  I mostly use this script to configure Ubuntu computers I sell. Here is my webpage [http://www.freewebs.com/tea4all]("http://www.freewebs.com/tea4all") :)

---

