---
title: "[urgent] Help with server."
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Mohanish on 2007-11-29
Hey,
Thanks to you for watching this thread and helping me.
Yesterday i bought a linux server . I wanted to install vnc on it. Therefore i installed Debian but in vain . Therefore, i went for centos and managed to get vnc work but when i logged in , there was a weird picture there.[[CLICK HERE TO VIEW]("http://xs121.xs.to/xs121/07484/errorwithvnc.JPG")]

Today , a friend told me to install ubuntu rather than the others. Yes it was really easy to install. I was googleing and found this great site. but well i can neither install freenx or vnc. Im pretty noobish at these so i am asking for a detailed explanation. 
I found some articles 
```
As always, let's start off by making sure your server is up to date and that you have the required ssh server:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install openssh-server

Once your packages and updates, if any, have been downloaded and installed, visit these pages from NoMachine to grab their free NX Server packages. You will need 3 packages to install NX Server:

   1. NX Node
   2. NX Client
   3. NX Server

In each case there will be multiple choices. Make sure you download the version that says DEB else you'll end up with something that won't work as easily on Ubuntu.

Now that you have all the packages it's time to install. Open up your terminal and cd into the directory where you downloaded the above files. We're going to install them in the same order they were downloaded. In each case, make sure you use the name of your file as opposed to what I type here as you may have downloaded a more recent version than what I did.

sudo dpkg -i nxnode_2.0.0-100_i386.deb
sudo dpkg -i nxclient_2.0.0-98_i386.deb
sudo dpkg -i nxserver_2.0.0-76_i386.deb

You should now have the latest version of NX Server installed! I'm not sure if version 1.5 of the client will work with v2.0 of Server but why not just grab the latest client anyway?
```

```

Once your packages and updates, if any, have been downloaded and installed, visit these pages from NoMachine to grab their free NX Server packages. You will need 3 packages to install NX Server:

   1. NX Node
   2. NX Client
   3. NX Server
```

How do i install these 3 packages?is there ia code like apt-get install stuff?
Help 

Thanks,
Mohanish

---

### Post by daflame on 2007-11-29
> **Mohanish said:**
> Hey,
Thanks to you for watching this thread and helping me.
Yesterday i bought a linux server . I wanted to install vnc on it. Therefore i installed Debian but in vain . Therefore, i went for centos and managed to get vnc work but when i logged in , there was a weird picture there.[[CLICK HERE TO VIEW]("http://xs121.xs.to/xs121/07484/errorwithvnc.JPG")]

Today , a friend told me to install ubuntu rather than the others. Yes it was really easy to install. I was googleing and found this great site. but well i can neither install freenx or vnc. Im pretty noobish at these so i am asking for a detailed explanation. 
I found some articles 
```
As always, let's start off by making sure your server is up to date and that you have the required ssh server:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install openssh-server

Once your packages and updates, if any, have been downloaded and installed, visit these pages from NoMachine to grab their free NX Server packages. You will need 3 packages to install NX Server:

   1. NX Node
   2. NX Client
   3. NX Server

In each case there will be multiple choices. Make sure you download the version that says DEB else you'll end up with something that won't work as easily on Ubuntu.

Now that you have all the packages it's time to install. Open up your terminal and cd into the directory where you downloaded the above files. We're going to install them in the same order they were downloaded. In each case, make sure you use the name of your file as opposed to what I type here as you may have downloaded a more recent version than what I did.

sudo dpkg -i nxnode_2.0.0-100_i386.deb
sudo dpkg -i nxclient_2.0.0-98_i386.deb
sudo dpkg -i nxserver_2.0.0-76_i386.deb

You should now have the latest version of NX Server installed! I'm not sure if version 1.5 of the client will work with v2.0 of Server but why not just grab the latest client anyway?
```

```

Once your packages and updates, if any, have been downloaded and installed, visit these pages from NoMachine to grab their free NX Server packages. You will need 3 packages to install NX Server:

   1. NX Node
   2. NX Client
   3. NX Server
```

How do i install these 3 packages?is there ia code like apt-get install stuff?
Help 

Thanks,
Mohanish

First things first, which version of Ubuntu do you have?  If it is Gutsy, go to my site about FreeNX.  The packages you have are NOT FreeNX, they might be NX Free Edition from nomachine.com.  Even NoMachine wants everyone to realize that they are not the same.  My site is here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

Before you follow the instructions on that page REMOVE ALL NX packages first and make sure you don't have any stray VNC packages lying around either.

---

### Post by Mohanish on 2007-11-29
it is ubuntu-6.06-i386-minimal

---

### Post by daflame on 2007-11-30
> **Mohanish said:**
> it is ubuntu-6.06-i386-minimal

You might want to upgrade to Gutsy first.  Also, without a graphical desktop environment freenx doesn't do anything.  Make sure kubuntu-desktop or ubuntu-desktop or xubuntu-desktop are installed first, then upgrade to Gutsy using the update manager.  Then go to my forums to install the server.

---

