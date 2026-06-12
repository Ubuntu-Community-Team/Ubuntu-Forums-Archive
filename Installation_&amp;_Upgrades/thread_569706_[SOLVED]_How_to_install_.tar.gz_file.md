---
title: "[SOLVED] How to install .tar.gz file"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by amitabhishek on 2007-10-07
I want to install .tar.gz file in Ubuntu 7.04. But in Synaptic Package manager it wont just show up. "Search" also is not of much help. Attached is the screenshot with 2 files I want to install. What do I do now.

Pls help

---

### Post by aashay on 2007-10-07
First extract the tar to a folder
Fire up a terminal and navigate to the folder
```
./configure
make
sudo make install
```
If ./configure fails for some reason, you dont have enough tools to compile the app. In this case, search for the name where the error occurs in synaptic and install it

---

### Post by aashay on 2007-10-07
More on that here: [http://htmldesign.dk/blog3/ubuntu/installing/#source]("http://htmldesign.dk/blog3/ubuntu/installing/#source")

---

### Post by Pumalite on 2007-10-07
Make sure you have this installed:

sudo apt-get install build-essential

---

### Post by amitabhishek on 2007-10-07
OK. To be very specific how do I install this file thats there on my desktop:

/home/amit/Desktop/thunderbird-2.0.0.6.tar.gz

---

### Post by Pumalite on 2007-10-07
You can double click on it and Ark (Kubuntu) or File Roller (Ubuntu) will take over. Extract where you want. Read the README file first. If you have to configure,etc; make sure you have build-essential installed.

---

### Post by aashay on 2007-10-07
try ```
sudo apt-get install thunderbird
```

---

### Post by rsambuca on 2007-10-07
Normally with a pre-configured system like Ubuntu, you only install programs from source code as a last resort.  In this case, it really isn't necessary as there are .deb packages for thunderbird.

Here is the [how to for installing Thunderbird 2.0]("https://help.ubuntu.com/community/ThunderbirdNewVersion") in Ubuntu.

---

### Post by amitabhishek on 2007-10-07
Thanks! I installed using an "ugly method". I knew the name of the binary file attached with thunderbird client. I simply added it in the Ubuntu's program menu.

---

