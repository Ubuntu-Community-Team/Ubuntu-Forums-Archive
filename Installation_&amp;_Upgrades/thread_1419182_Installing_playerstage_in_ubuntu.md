---
title: "Installing playerstage in ubuntu"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by Wushuki on 2010-03-01
I am trying to install playerstage in ubuntu and have some problems with this. So far I have followed the steps in the tutorial at [http://www.control.aau.dk/~tb/wiki/index.php?title=Installing_Player_and_Stage_in_Ubuntu]("http://www.control.aau.dk/%7Etb/wiki/index.php?title=Installing_Player_and_Stage_in_Ubuntu"), and can now succesfully start stage with the "stage simple.world" and "stage fasr.world" commands.

The player command "player simple.cfg" mentioned in the tutorial does not work yet however and I am not sure how to resolve this. When I run the command it gives the following output:

error   : Failed to load plugin stageplugin.
error   : libtool reports error: file not found
error   : plugin search path: /usr/bin:/home/bob/Downloads/Stage-3.2.2-Source/worlds:.:/usr/local/lib/
error   : failed to load plugin: stageplugin
error   : failed to parse config file simple.cfg driver blocks

It seems that plugin search path can be changed with the: "export PLAYERPATH='...'", but none of the directories that I have tried filling out here seem to make this go away, not even the one that actually contains the libtool file.

If you have any idea of what might cause this or how it might be resolved, I'd greatly appreciate the help. 

Thanks in advance.

---

### Post by prithvisekhar on 2010-07-09
i recommend removin what has been installed and reinstallin 


#Install the dependencies (do not know if all are necessary, but at least they are sufficient) can do this step through the synaptic package manager

sudo apt-get install autotools-dev build-essential cmake cpp libboost-signals1.40.0 libboost-signals1.40-dev libboost-thread1.40.0 libboost-thread1.40-dev libcv4 libcv-dev libgnomecanvas2-0 libgnomecanvas2-dev libgsl0-dev libgtk2.0-dev libjpeg62-dev libtool libxmu-dev swig python3-all-dev libcvaux-dev libhighgui-dev libdc1394-22-dev


#For stage
sudo apt-get install freeglut3 freeglut3-dev libfltk1.1 libfltk1.1-dev libltdl7 libltdl7-dev libpng12-0-dev libpng12-0 

#If the installation does not work, check that the above packages actually was installed. That you do not see a line like Could not find package ....


#Download the installation files
cd ~
mkdir playerstage_download
cd playerstage_download
wget [http://sourceforge.net/projects/playerstage/files/Player/3.0.2/player-3.0.2.tar.gz/download](http://sourceforge.net/projects/playerstage/files/Player/3.0.2/player-3.0.2.tar.gz/download)
wget [http://sourceforge.net/projects/playerstage/files/Stage/3.2.2/Stage-3.2.2-Source.tar.gz/download](http://sourceforge.net/projects/playerstage/files/Stage/3.2.2/Stage-3.2.2-Source.tar.gz/download)
#You might need to restart after this


#Extract the files
tar xzvf player-3.0.2.tar.gz
tar xzvf Stage-3.2.2-Source.tar.gz

#add the python in the bashrc file 
PHYTHON_INSTALL_DIR=/usr/local
echo "" >> ~/.bashrc 
echo "export PYTHONPATH=\"$PHYTHON_INSTALL_DIR/lib\"" >> ~/.bashrc
source ~/.bashrc

#### restart now to ensure that all the packages and chages are commited 
echo "Restart NOW to commit all changes "

Install Player

[LIST]
[*]unzip player
[*]inside  player directory mkdir build
[*]cd build
[*]cmake ../
[*]make
[*]sudo  make install
[/LIST]
check if player has been installed by run ' player pioneer.cfg' in the config of the player folder

Install Stage

[LIST]
[*]unzip stage
[*]inside  stage directory mkdir build
[*]cd  build
[*]cmake ../
[*]make
[*]sudo  make install
[/LIST]
Export  directories

[LIST]
[*]edit your  ~/.bashrc file by adding the following lines
[/LIST]

[LIST=1]
[*]export  PATH="$PATH:/usr/local/share/player/bin"
[*]export  LD_LIBRARY_PATH=/usr/local/lib
[*]export STAGEPATH=/usr/local/lib
[*]export  PLAYERPATH=/usr/local/lib
[/LIST]

[LIST]
[*]run "source ~/.bashrc" to  reload the shell
[/LIST]
now u can just run  ' player simple.cfg' in the world folder of the Stage

---

