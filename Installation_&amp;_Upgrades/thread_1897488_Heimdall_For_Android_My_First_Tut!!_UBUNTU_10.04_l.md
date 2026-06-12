---
title: "Heimdall For Android My First Tut!! UBUNTU 10.04 lts"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by G-RB-NS on 2011-12-19
so download the two packages from here  
[https://launchpad.net/~modycz/+archive/h...ld/2277388](https://launchpad.net/~modycz/+archive/h...ld/2277388)  
libusb-1.0-0-2:1.0.8-2~lucid1 
libusb-1.0-0-dev-2:1.0.8-2~lucid1 
dpkg -i libusb-1.0-0-2:1.0.8-2~lucid1 <--- This one needs to be first ! 
dpkg -i libusb-1.0-0-dev-2:1.0.8-2~lucid1  
If these don't work theres something else wrong.  
This is the libusb you need to continue  

now download the source for heimdall from here 
[https://github.com/Benjamin-Dobell/Heimdall/downloads](https://github.com/Benjamin-Dobell/Heimdall/downloads). 
hit the download as .tar.gz  go 
into libpit (there's no need for make install here) 
./configure && make && cd ..  
go into heimdall ./configure && make && sudo make install  
check to see if its worked properly  
sudo checkinstall --pkgversion  
Where  is the current Heimdall release e.g. 1.3.0  

*FRONTEND* install qmake (1.3gb file do download it whilst setting up the rest) 

[http://get.qt.nokia.com/qtsdk/Qt_SDK_Lin...1_4_en.run](http://get.qt.nokia.com/qtsdk/Qt_SDK_Lin...1_4_en.run) chmod u+x Qt_SDK_Lin32_offline_v1_1_4_en.run ./Qt_SDK_Lin32_offline_v1_1_4_en.run  
qmake is needed for the next step. 
now go into heimdall-frontend 
qmake heimdall-frontend.pro && make && sudo make install 
check to see if its worked  sudo checkinstall --pkgversion  
Where  is the current Heimdall release e.g. 1.3.0 
You might also have to install libqt4-dev so don't forget to do it. now you should have heimdall installed with the frontend. Enjoy

---

