---
title: "Help! Can't install Cupswrapper for my Printer"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by BeyondAwesome on 2012-03-18
Hi,

I am a noob to both Linux and Ubuntu. I went to the brother website and downloaded the .deb drivers for my printer. The lpr file installed fine, but the cupswrapper wouldn't install. I tried and tried to find a solution, and then I found out about alien. I tried to use alien to convert the .rpm file they also have into a deb, but that won't install.

The reason I tried to convert the .rpm to .deb is because the file ended with -2 instead of -1 like the lpr file, and I thought that may have been causing problems. When I converted the file, the "-" became "_" instead, so maybe that's the problem. I'm not sure.

Anyway, I have a brother intelliFax-2820 printer, and the drivers are up here under FAX-2820 [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#FAX-2820](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#FAX-2820)

I really need my printer to work out. If there is no way that I can get my printer to work on Ubuntu then I am going to try another Linux OS. I heard Fedora reads .rpm Should I get Fedora instead if I can't get this driver installed.

Oh, and when explaining something, please don't leave out any steps. I am a total noob, and if you leave out a step, chances are I will get lost.

Also, here is what I did to install alien to convert the .rpm file to deb 
sudo apt-get install alien
Entered my password
cd ~/Desktop
sudo alien -k cupswrapperFAX2820-2.0.1-1.i386.rpm

It then created a .deb file, but it also has a padlock symbol on the package. Why is this?
Sorry if I sound like an uber noob, but yesterday was the first time I even used the terminal.

---

### Post by BeyondAwesome on 2012-03-18
Hey, I just wanted to let you know, I got my printer to work. I googled up to how install from the terminal, and I installed the package from the terminal and my printer now works! Man, I feel smart. :guitar:

---

