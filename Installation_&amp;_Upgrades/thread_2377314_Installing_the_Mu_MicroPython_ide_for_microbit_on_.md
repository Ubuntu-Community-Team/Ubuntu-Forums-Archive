---
title: "Installing the Mu MicroPython ide for micro:bit on ubuntu"
date: 2017-11-11
forum: Installation &amp; Upgrades
---

### Post by rhubarbdog on 2017-11-11
There is no simple command that works this is what i've done i still have slight issues, but i'm up running and coding my micro:bit.
Firstly download the zip from this GitHub page [https://github.com/mu-editor/mu](https://github.com/mu-editor/mu)
Now open a terminal move to the downloads directory and unzip it
```
cd ~/Downloads
unzip mu-master.zip
```

This install requires pip3 and python setup tools.  Those are installed from a terminal typing ```
sudo apt install python3-pip
sudo apt-get install python3-setuptool
sudo apt-get install python3-dev
```

We're now ready to go pip3 doesn't like being ran with sudo so in a terminal type the following ```
cd ~/Downloads/mu-master
sudo su
pip3 install -r requirements.txt
make clean
exit
```

All users who want to use the full functionality of the Mu ide need to be in group dialout. In a terminal type ```
sudo usermod -a -Gdialout user-name
```
you need to logout and log back in for new groups to take effect.

Test the installation typing ```
cd ~/Downloads/mu-master
./run.py
```

finally move the whole lot  to /usr and put an executable on your path ```
sudo mv ~/Dowloads/mu-master /usr/local/bin
cd /usr/local/bin
sudo ln -s mu-master/run.py Mu
```

I haven't called it mu as there is already a linux command mu.

Hope this helps other users

---

### Post by rhubarbdog on 2017-11-14
Hi on further research i have missed these 3 steps
```

sudo apt-get install python3-pyqt5
sudo apt-get install python3-pyqt5.qsci
sudo apt-get install python3-pyqt5.qtserialport

```

---

