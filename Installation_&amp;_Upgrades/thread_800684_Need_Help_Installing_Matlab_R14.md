---
title: "Need Help Installing Matlab R14"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by aio85 on 2008-05-20
I'm a complete noob to linux. I just started reading books on the filesystem concepts I have a week's worth of experience with the terminal.

So, I'm trying to install MatlabR14 on Ubuntu Hardy and I managed to follow enough of the fragmented online advices. I have successfully installed matlab in my /usr/local/src/matlabr14 directory. I even copied the license.dat file to my /usr/local/src/matlabr14/etc directory. I can't seem to run matlab in the terminal. I type matlab in the terminal and tried ./lmstart which causes the following message on the terminal:

[B]Checking license file for local hostname and local hostid . . .
 
Taking down any existing license manager daemons . . .
 
    No license manager daemons running . . .
 
Starting license manager . . .
 
    Debug logfile = /var/tmp/lm_TMW.log[/B]


Please help because I know that I'm close. I followed the following online steps but I'm stuck in step 6:

[I]1) Create a matlab directory
$sudo mkdir /usr/local/matlab

2) Paste your license information into a license.dat file, and save
$cd /usr/local/matlab/ && sudo gedit license.dat

3) Copy the entire contents of the DVD into your /usr/local/matlab/ folder
$cd /media/cdrom/ && sudo cp * -R /usr/local/matlab/

4) Install matlab ...
$sudo /usr/local/matlab/./install_matlab

5) Answer yes to everything, and check off to install the symbolic link

6) When the installer finishes, you will have to start the license manager
$/usr/local/matlab/etc/./lmstart

7) Then change the ownership on your matlab directory
$sudo chmod a+rwx -R /usr/local/matlab/

8) Finally, you can launch matlab
$matlab[/I]

---

### Post by iaculallad on 2008-05-20
You could follow the steps mentioned in here to successfully install your MatLab R14.

[http://linuxexpert.wordpress.com/2007/06/18/how-to-install-matlab-7-r14-for-linux/](http://linuxexpert.wordpress.com/2007/06/18/how-to-install-matlab-7-r14-for-linux/)

Hope this could help.

---

### Post by aio85 on 2008-05-20
thanks for the help iaca! the instructions helped me settle the rest of the installation! cheers

---

