---
title: "Installing VMWare Player on 9.10"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Kezza69 on 2009-11-21
I have registered and downloaded a .bundle file for VMWare player. Can anyone provide the install steps I need to perform. I can find help for 8.xx and 9.04. Are the steps the same?  Is there a .deb file I can use to make this easier?

thanks

---

### Post by dooglo on 2009-11-21
I'm wondering about the same.  I've got the VMware Player 3.0 downloaded and saved, how do you install it.  I'm a total newbie here as well. 


This is on 9.10 as well

Oh ya,   bump.


D.

---

### Post by stav1953 on 2009-11-22
Same here,
Have no idea how to use the command line and commands to "manually" install it. Tried Add/Remove software but it doesn't show in the drop down list.
This is the last step before totally switching from Windows to Linux.
Thax for helping,
Stav

---

### Post by darco on 2009-11-22
cd to the directory where you downloaded VMWare, then
```
sudo sh vmwarexxxx.bundle
```


darco

---

### Post by NJC on 2009-11-24
I download the VMware file and ran the following:

```
sudo chmod +x ./VMware-Player-3.0.0-203739.i386.bundle
gksudo bash ./VMware-Player-3.0.0-203739.i386.bundle

```

I am running Ubuntu 9.10 as well. The installation was VERY painless and smooth. I copied the code from a tutorial somewhere.

---

### Post by stav1953 on 2009-11-25
It works great. Thanks for sharing

---

### Post by mmino on 2010-01-04
I followed your instructions but for the 64 bit version and the player 3.0 did not install successfully.

Copy of results from terminal window follows:
 michel@michel-desktop:~$ sudo chmod +x ./VMware-Player-3.0.0-203739.x86_64[1]
michel@michel-desktop:~$ gksudo bash ./VMware-Player-3.0.0-203739.x86_64[1]
Extracting VMware Installer...done.

The VMware installer 1 launches and installs the VMware 3.0 files.
But then it continues and Rolls back the VMware Player 3.0 installation and removes all configuration information and indicates the installation was unsuccessful.

Any idea what I may be doing wrong?

Thanks

---

### Post by whiliq on 2010-01-18
I have the same result. "Installation was unsuccessful."

I hope there is a solution for this.

---

### Post by roedorpi on 2010-01-19
Hi all, 
I've just installed vmplayer 3 on ubuntu 9.10 64 bits, with no problems using: 

```
gksudo bash ./VMware-Player-3.0.0-203739.x86_64.bundle
```

You just have to make sure that the file you download from VMware has the correct MD5SUM, the first time I downloaded the file it was wrong!!

```
md5sum VMware-Player-3.0.0-203739.x86_64.bundle
```

The output of this command should correspond to the MD5SUM posted on the VMware download page.

Greetings
roedorpi

---

### Post by Elisabete on 2010-02-10
This worked like a charm! 

I summoned up the courage to make a full switch over to Ubuntu, under the notion that I could still run windows via a virtual machine. I've just spent the last few hours trying to figure out how to install vmplayer and virtualbox. Neither was working for me and I was starting to get a little anxious. 

This worked on the first try. Wow! Much appreciation! 



> **NJC said:**
> I download the VMware file and ran the following:

```
sudo chmod +x ./VMware-Player-3.0.0-203739.i386.bundle
gksudo bash ./VMware-Player-3.0.0-203739.i386.bundle

```I am running Ubuntu 9.10 as well. The installation was VERY painless and smooth. I copied the code from a tutorial somewhere.

---

### Post by MadBillyGoat on 2010-03-21
> **darco said:**
> cd to the directory where you downloaded VMWare, then
```
sudo sh vmwarexxxx.bundle
```


darco
This worked great for me as well thanks.

---

### Post by jbumgar on 2010-03-26
i type cd /Downloads from home and it says no directory.  How do I change directory to Downloads?  Newbie BTW. lol

---

### Post by jbumgar on 2010-03-26
Thanks for the help.  Finally installed it.

---

### Post by Stercus accidit on 2010-10-27
I just used instructions from: 
[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

It worked perfectly. :idea:

---

### Post by Stercus accidit on 2010-10-27
Or if it's easier for you you can just download it from 
[https://www.vmware.com/](https://www.vmware.com/)  
and follow the instructions from 
[http://www.youtube.com/watch?v=jE9TgMS7r78](http://www.youtube.com/watch?v=jE9TgMS7r78).

---

### Post by braikar on 2011-10-16
If someone has "Installation was unsuccessful." at some point, check /var/log/vmware-installer (or vmware-install depending on the version)

Mine showed for example that the unsuccesful install was due to a corrupted file, that could not be deleted/overwritten...
```

2011-10-16 14:48:35,167] [vmware-player-app 4.0.0] Failed to copy file from lib/help/player/wwhelp/wwhimpl/js/images/spc_top.gif to /usr/lib/vmware/help/player/wwhelp/wwhimpl/js/images/spc_top.gif
Traceback (most recent call last):
  File "/tmp/vmis.8rNED2/install/vmware-installer/vmis/core/component.py", line 190, in doit
    with open(dest, 'wb') as write:
IOError: [Errno 1] Operation not permitted: path('/usr/lib/vmware/help/player/wwhelp/wwhimpl/js/images/spc_top.gif')

```
So I tried deleting it, didn't work, I had to use
```
sudo chattr -a /locationoffile.../spc_top.gif
``` to change a flag to allow the file to be erased (I'm curious as to how such things can happen??)
Anyway then I could remove the entire folder /usr/lib/vmware... It shouldn't exist in the first place if VMware is not installed.

And install went flawlessly :)

---

