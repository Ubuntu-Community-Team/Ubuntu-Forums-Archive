---
title: "I need to install wine but have no internet connection"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by maeug on 2010-02-21
Hi, I have recently installed ubuntu in a pc and I need to install wine in order to be able to install my wireless antenna's software, which works only on Windows. The thing is I obviously do not have internet connection on such pc so as to follow the wine installation procedure.
I wanted to download the program on another computer and maybe install it via pendrive or cd/dvd installation.
Can anybody tell me if it is possible?
Please guide me step by step :S Thanks!

---

### Post by zvacet on 2010-02-22
You can use [Keryx]("http://keryxproject.org/") or you can download from [here.]("http://packages.ubuntu.com/karmic/wine") If you choose secon method the you have to download all packages marked with red ball(they are dependencies) and download ones marked with greeen and blue as well.At thee bottom of the page is wine package.Select your architecture and download it.Put all packages in one folder and with usb or something else put it in Ubuntu.Let say that your folder is named **folwin**.Put it in your home directory and then type in terminal

```
cd folwin

sudo dpkg -i *deb
```

---

### Post by maeug on 2010-02-22
Thank you for your help however I am yet without wine:
I downloaded Keryx and there I downloaded wine. However once I was running the program on ubuntu (installing it) it said it contained an error and could not be done. Is there any other way?

---

### Post by Thomas Garman on 2010-02-22
I would suggest downloading the deb Sun Virtual Box PUEL on a usb stick some place where you have an internet connection amd then installing it on your computer.

---

### Post by mac9416 on 2010-02-23
> **maeug said:**
> Thank you for your help however I am yet without wine:
I downloaded Keryx and there I downloaded wine. However once I was running the program on ubuntu (installing it) it said it contained an error and could not be done. Is there any other way?

Hi!

What version of Keryx did you use? Could you go into detail about what happened?

---

### Post by maeug on 2010-02-24
I used Keyrx version 0.92.4 I have used the karmic 32 architecture and the problem is: 
"Selecting previously deselected package wine.
(Reading database ... 114066 files and directories currently installed.)
Unpacking wine (from wine_1.0.1-0ubuntu8_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 wine"

---

### Post by mac9416 on 2010-02-24
OK, this is where a few of Keryx's shortcomings come to haunt her. With a package that depends on as many packages as Wine does, there is a fair chance that Keryx's dependency calculation will fail. What you have to do in these cases is to look at the installation output, see what package was missed, then download that with Keryx. After a few rounds of doing that, you will eventually get all the packages you need and the installation will be successful.

In this case you need to get libaudio2.

This is very irritating, but it's better than doing it all by hand. We plan to make dependency calculation as close as possible to perfect in Keryx 1.0. Until then, be patient and good luck!

---

### Post by maeug on 2010-02-25
Thanks for the tip. I was now able to install wine :) however I don't know how to use it.
For ex. I insert my sims 3 cd and it does not run. Can anybody explain?

---

### Post by mac9416 on 2010-02-25
Glad you got Wine installed!

Whenever you want to learn how to make a certain app work with Wine, search for it on appdb.winehq.org. Usually an app will have instructions on how to make it work properly.

Take a look at this page to see how to make Sims 3 work: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

If you have any trouble, you'll want to start a new thread in order to draw folks who know about that particular subject to it.  :)

Good luck!

---

### Post by LoloftheRings on 2010-02-25
Double clicking the .exe file should do it.

---

