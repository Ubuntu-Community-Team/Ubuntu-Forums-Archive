---
title: "Problem!!!...Can't install amsn on 7.10"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by popanik on 2007-11-21
Hey!
I am a new user if Ubuntu and i recently updated from 7.06 to 7.10.
I tried to install amsn through the Add/Remove application,but when i check the amsn package there's a pop-up window that says that the list of applications is not available and 
i can only choose refresh.
I tried everything,but it won't seem to install.The thing is that on my laptop,with Gutsy Gibbon on,i use amsn....

Please help me.....
Thank you.

---

### Post by Sef on 2007-11-21
You need to change the show setting (top right) to either 'All Open Source Applications' or 'All Available Applications'.   The former is only GPL software, while the latter also includes nonGPL software.

---

### Post by popanik on 2007-11-21
Well...i already did that,but as it seems my Add/Remove applications doesn't work properly,because it does that with every application......
I re-installed 7.10 but i have the same problem....:(

---

### Post by Biznarie on 2008-01-04
I have the same problem when installing Java, When I click on the application it needs to refresh every time therefore I cant choose to install it.

---

### Post by Sef on 2008-01-05
> Well...i already did that,but as it seems my Add/Remove applications doesn't work properly,because it does that with every application......
I re-installed 7.10 but i have the same problem....

1) Have you tried Synaptic?  System > Administration > Synaptic Package Manager

2) Since you have reinstalled and the same problems occurs, have you checked the disk for errors?  Instead of Start/Install Ubuntu, go down the list to Check Disk for Errors.

---

### Post by Victormd on 2008-01-05
The amsn is available in the Synaptic Package Manager. However, it is an out-dated version. The newest version is 0.97 ([www.amsn-project.net](www.amsn-project.net)).

Here comes my question...
I'm tried to install the autopackage option but get an error so I moved on to the source tarball. The only problem is that I've never compiled anything and the "instructions to install" don't really say much, simply to use three commands after the extracting the files:
./configure
make
su -c 'make install'

I ran the ./configure and everything seemed to work. When I went on to "make" it requires a bunch of parameters and I have no idea what to use. Could anyone help me?

Thanks

---

### Post by Victormd on 2008-01-05
Ok. after some digging I got it! Apparently even though I had installed the tcl8.4, I did not have all the necessary apps installed so here's a little How To if anyone else is having problems (this is only if the Autopackage does not work):
1. Go to [www.amsn-project.net](www.amsn-project.net) and download the amsn source tarball
2. Open the terminal and download necessary libraries and tcl using:
           sudo apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev
3. Unpack tarball file using (must be in the directory where you downloaded the file, e.g. /Desktop):
           tar -xvjf amsn-0.97.tar.bz2
4. A directory called "amsn-0.97" is now created, do: cd amsn-0.97
5. type          ./configure               (this will check if you have all necessary files)
6. once the above step is complete, do:       make
7. The final step is:         su -c 'make install'

On Step 7, you might get an authentication error (at least it happened to me). If this is the case:
a) go to System>Administration>Users and Groups
b) select 'root' and click on properties. Here you'll have to set the password (the password might have been generated randomly so just set it to what ever you'd like (even your current password). Click Ok and Close.

Now do Step 7 again and presto!
This worked for me. Hopefully you'll find it usefull as well

---

### Post by Ptero-4 on 2008-01-05
or you can use sudo make install instead.

---

### Post by Victormd on 2008-01-05
What's the difference between "su" and "sudo"? I'm used to using sudo but didn't work here... that's why I had to use su (saw it at another forum otherwise I would have been lost).

---

### Post by boboyo on 2008-01-05
i got the same problem when im trying to install amsn and java runtime.

victor, i did what u wrote but it doesnt work.....

id like to have amsn and java on my computer....

---

### Post by patrickfromspain on 2008-01-05
I would think you have a problem with your sources.list file.

gksudo gedit /etc/apt/sources.list

delete everything that's in there and paste the following:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

save and close.

sudo apt-get update and then, at last: sudo apt-get install amsn.

Anyway, as stated before, the amsn version in the repos is old, and worst, UGLY. I've made packages to install a pretty and newer aMsn:

[http://ubuntuforums.org/showthread.php?t=649364](http://ubuntuforums.org/showthread.php?t=649364)

---

### Post by Victormd on 2008-01-05
boboyo, when you ran the ./configure, did you get any errors?

I have Java on my computer, but I have an AMD64 and used the script here (for 32 bits) to install:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

At what point did your install stop?

---

### Post by Simonridesbikes on 2008-02-02
It all worked for me 
thanks victormd :)

---

