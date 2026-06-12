---
title: "Problem Installing Matlab"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by ChuckleFox on 2013-01-30
Hello everyone, I am having trouble installing Matlab on my laptop. First about my computer, it a 64 bit system but I am running the 32 bit version of ubuntu 12.04. This is the process I am using to installing: First I download the MatlabR2012A-Linux-32bit.tar.gz from my schools network. Then I go to the command line and use tar zxf filename to unpack it. Then, I go into the unpacked folder, r2012a-linux-32-bit and use sudo ./install.
This brings me to an installation menu where I go about the process of signing in, activiating, etc. Ultimately, it brings me to a screen where it tells me to specify the installation folder and I choose the default which is /usr/local/MATLAB/R2012a. So the program installs and there is a matlab folder where it is supposed to be. So I go to the folder and it has a bunch of files including an install file (Why?). There is a matlab file in the bin folder but every time I click on it, a matlab window appears for a few seconds and then disappears. Does anyone know how I might be able to solve this problem?

---

### Post by aitatanit on 2013-01-30
clicking on it is the wrong way to launch it. You need a command line to launch it:

~$ /usr/local/MATLAB/R2012a/bin/matlab 

Now you need to keep the terminal open so that Matlab remains running.

---

### Post by ChuckleFox on 2013-01-30
Alright that works! How come when I navigate to the folder where the matlab file is held and then type matlab it doesn't start? Is it not a command because what you gave me a is a file path ending with the matlab file. What makes that different?

---

### Post by aitatanit on 2013-02-01
if you type ./matlab it should run from the directory where matlab (the executable) is. Better yet add that directory to your PATH variable in your .bashrc file. Every time you want to launch matlab, open a terminal window and just type matlab and that should launch Matlab. Here's how:

edit your .bashrc (located in your home folder but is hidden) file and go to the bottom and type this on a new line:
export PATH=/usr/local/Matlab2012a/bin:$PATH


Save the file, close the terminal window, open another, and type matlab on the command line and that should launch it for you

---

