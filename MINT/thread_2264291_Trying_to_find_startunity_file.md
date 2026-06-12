---
title: "Trying to find startunity file"
date: 2015-02-06
forum: MINT
---

### Post by Pocc on 2015-02-06
Hi all,

I'm trying to get Linux Mint to run on crouton, which is kind of difficult. I was using this guide [http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html](http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html) , and modified it to work with linux mint. Essentially, it uses a copy of startxfce4 in /usr/bin on the chroot to start elementary (mint). I can get mint to work -- if I install the ubuntu-desktop meta package. I'm looking for the file that xinit targets in unity (maybe xinitrc) that's similar that the chroot can look for to start cinnamon.

startxfce4 is in /usr/bin
startunity is in /usr/local/bin, but when I copy it and tell the chroot to look at it, the chroot doesn't recognize it. 

Any and all help is appreciated. I understand this a complicated question, so I realize I may have not included enough pertinent information. Thanks!

---

### Post by Pocc on 2015-02-06
Here's the guide I created that's based off his work. 

I couldn't find a guide to cinnamon, so I figured I'd create one. This is for chromebooks with intel processors only. If you have an ARM chromebook, buy an intel chromebook.


I followed [http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html](http://jeanlouisnguyen.blogspot.com/2014/01/guide-how-to-install-elementary-os-on.html) except we're working with cinnamon instead of elementary OS. Kudos to jeanlouisnguyen for making this possible.


(0) Make sure that you're in developer mode and have downloaded crouton.


1. From ChromeOS, type ctrl+alt+t
2. You should be presented with "crosh>". Type


        shell


3. Type
    
        sudo sh -e ~/Downloads/crouton -t xfce,keyboard,extension -n cinnamon
    
    You will have to wait anywhere from 10-30 minutes for the desktop environment to install.


4. You will be prompted for a username and password. Choose ones suitable to your needs (jeanlouisnguyen chose "user/user").


5. Type


        sudo enter-chroot -n cinnamon


    If you're familiar with linux, this is the same thing as opening up gnome-terminal, konsole, etc. Enter your ChromeOS password.


6. Type


        sudo apt-get install python-software-properties software-properties-common
        sudo add-apt-repository ppa:tsvetko.tsvetkov/cinnamon
        sudo apt-get update
        sudo apt-get install cinnamon


    †


7. Install ubuntu-desktop. Mint is dysfunctional if we don't install this.


      sudo apt-get install ubuntu-desktop


8. While we're at it, let's install sugar, spice, and everything nice! Feel free to skip if you already know what extras you want to install.


    I'm using this [http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html) and \([http://www.binarytides.com/better-linux-mint-17-cinnamon/](http://www.binarytides.com/better-linux-mint-17-cinnamon/) to get these goodies.


    Stuff you should install for basic functionality:


        sudo apt-get install chromium-browser firefox vlc ubuntu-restricted-extras libavcodec-extra pepperflashplugin-nonfree unace p7zip-rar sharutils rar arj lunzip lzip uget hardinfo nano


    Pretty Stuff:


        sudo apt-get install mint-backgrounds-*


    Dropbox:


        sudo apt-get install python-gpgme nautilus-dropbox


    Skype:


        sudo apt-get install skype


    Oracle Java:


        sudo add-apt-repository ppa:webupd8team/java
        sudo apt-get update
        sudo apt-get install oracle-java7-installer


9. Create a start script for cinnamon:


        cd /usr/bin
        sudo cp startxfce4 startcinnamon


10. Edit the start script:


        sudo nano startcinnamon


    Go down to the second to last line. It should look like this:


        exec $prog /etc/xdg/xfce4/xinitrc $CLIENTRC $SERVERRC


    Delete it and enter this instead:


        exec $prog /usr/bin/xinit_cinnamon


    ctrl+X, hit 'y' and enter to save.


11. Now create the xinit_cinnamon script you just referenced:


        sudo nano xinit_cinnamon


    And type


        #!/bin/sh
        /usr/bin/cinnamon-session


    ctrl+X,  hit 'y' and enter to save.


12. Make xinit_cinnamon executable


        sudo chmod +x xinit_cinnamon
        sudo chown root:root xinit_cinnamon


13. Type


        logout
    
    You should now be in ChromeOS' shell with a blue $.


14. I'm skipping using nano because I know vi. If you don't now vi, use the guide at the top for this step.


        cd /usr/local/bin
        sudo cp startxfce4 startcinnamon
        sudo vi startcinnamon
    
    Edit the last line from "exec startxfce4" to "exec startcinnamon", save and exit.


**You should now have a working cinnamon distribution.**


I'd love me some feedback if something is missing.


† Note 1: There are two unofficial cinnamon PPAs that I found [http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html](http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html). The first one is by Lester Carballo Pérez. His name has an accent, which didn't play nice with the installation process. So we're going with the second option by Tsvetkov.

---

### Post by oldos2er on 2015-02-07
Moved to Other OS Support & Projects.

---

