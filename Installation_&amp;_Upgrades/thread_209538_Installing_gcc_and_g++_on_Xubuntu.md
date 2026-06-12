---
title: "Installing gcc and g++ on Xubuntu"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by rob_72 on 2006-07-05
Can someone help here please?
I was trying to install g++ and was working through the list of dependencies on the ubuntu website in order to install g++.
I have to do it this way as I do not have the ubuntu disk with me at the moment and would like to get g++ installed before I get the cd from a friend that I leant it to.
However I seem to have come across a circular dependancy for g++-4.0.

g++-4.0 depends on libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.
Clicking on the libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386 shows that it is in turn dependant on g++4.0

when I try to install libstdc++6-4.0 the details list of the dependencies lists itself AND g++-4.0.  If you continue with the installation it asks for the dapper drake Cd (which i don't have)
when installing g++-4.0 the same thing occurs with the circular dependancy.

Is there a way around this without the dapper drake disk?

---

### Post by taurus on 2006-07-05
```

sudo apt-get install build-essential

```

---

### Post by rob_72 on 2006-07-05
Sorry I should have mentioned also that I have no access to the Internet as the internal modem on my HP Omnibook XE2 is not detected by XUbuntu and I don't have an external modem or a Broadband connection here.  I a posting this via another PC.

However I will try the last suggestion

Update: the command posted kindly by taurus results in a request to insert the Xubuntu disk (which i haven't got)

---

### Post by taurus on 2006-07-05
You need to edit your /etc/apt/sources.list and command out the first two lines regarding the CD by placing a # in front of them...
```

sudo nano /etc/apt/sources.list

```

---

### Post by rob_72 on 2006-07-05
taurus
I tried commenting out the CD path in the sources.list file and I now get an error "E: Couldn't find package build-essential".

Any ideas?

Rob

BTW thanks very much for the help so far.

---

### Post by taurus on 2006-07-05
So, let me get this right.  You don't have network connection and currently don't have the CD but you need to install the gcc compiler because you need to compile something!  Then how in the world did you install Dapper at the first place?  Did somebody install it for you but didn't give you the CD?

Maybe you need to remove the # sign in front of all the lines for universe and multiverse in /etc/apt/sources.list.  Then update it before you try to install it again as

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by rob_72 on 2006-07-05
taurus
thanks for your help, I'm sure that i am being pretty frustrating here.

To answer some of your questions

So, let me get this right. You don't have network connection and currently don't have the CD but you need to install the gcc compiler because you need to compile something!  
/*Yes thats correct, I want to mess around on the gcc compiler so taht I can eventually (hopefully) contribute back to ubuntu. I am pretty new to Linux and very new to ubuntu, however I am a software engineer and have always wanted to get into Linux, just didn't have the chance */

Then how in the world did you install Dapper at the first place? 
/* I downloaded the software at work (My boss kindly let me do this) and burned the CD, installed it on an old laptop.  I then lent the CD to a friend and haven't got it back yet.  However in my current location I am unable to download the iso again otherwise I would have done so.  The network i am on blocks all attempts to download the iso file as its so large.  However i am able to download the smaller packages (*.deb)*/

Did somebody install it for you but didn't give you the CD? /*answered*/

Hence I am downloading the files on one PC, transferring them to a portable usb disk and trying to install them on my laptop.

---

### Post by rob_72 on 2006-07-05
0

---

### Post by rob_72 on 2006-07-05
The way I look at it here is why let people download packages from the net if there is no way of installing them without running into circular dependencies or needing to have the PC connected to the internet.

I was intending on trying to sort out the problem with my modem, but I have a sneaky feeling that I will need to do some coding of my own to get this working (hence trying to install gcc etc...).  With my luck I'll end up trying to write my own driver for the modem :-|.  And all for a measly dial up :-).

Thanks for the help anyway Taurus, I'll just have to wait until I get the CD.

---

### Post by rob_72 on 2006-07-06
taurus
Managed to get hold of the disk last night and eventually installed g++ etc...
thanks for the help.

however it still seems strange to me that there is no other way around this dependency.  never mind I am now up and running

---

### Post by dolby on 2006-07-06
ubuntu is not the right distro for userrs with no internet connection. u should turn into distros that like debian or fedora available in dvd(s) which have many more packages than the single cd ubuntu install

---

