---
title: "How to Install Software in Ubuntu without Internet Connection within the OS"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by linotechie on 2010-01-25
I recently installed the latest version of Ubuntu and I need to install software in it. I cannot connect to the internet through Ubuntu but I do have internet access through another OS. Where do I find the software for Ubuntu? How do I install them once I found?

I've spent 3 days with Ubuntu and have no other experience with the OS. So, simple and step-by-step guidance will be appreciated. (Whenever possible, please also explain the meaning of the command or step I'm gonna use; I don't want to enter commands without understanding their meaning.) Thanks in advance.

---

### Post by ajgreeny on 2010-01-25
I'm afraid you will find it a long hard grind to do much with ubuntu or any other distro without web access.  You can always try installing from files downloaded on to other computers, and if the other machine has ubuntu you can use aptoncd, but it will still not be straightforward, particularly if you are new to the system.

I suggest you try harder to get web access if you really want to continue, but otherwise come back with more details and it may be possible to help you more.

---

### Post by linotechie on 2010-01-25
Hi ajgreeny

Thanks for the response. Unfortunately I won't be able to get the system with Ubuntu connected to the internet. Also, I believe I should need to download anything only once. If I have downloaded something and saved it, why should I be required to go online again for the same thing? Therefore, if there's something I need to download to install a piece of software, I'll download it from another system and save it for the future installations. If this is not possible, please say so; due to a slow and temporary connection available only on one system, I won't be able to get the Ubuntu system online forever.

What more details are needed for installation via another computer which is connected to the internet at a different place? That machine has Windows XP SP3. The two machines cannot be connected in any way; I cannot take the Ubuntu system to that place and cannot bring the other machine to home either. I guess I'm stuck. If there's anything at all possible to get a software installed on Ubuntu with file/s downloaded elsewhere, please point me to that procedure. If not, please let me know. Thanks.

If the name of the specific software is needed as one of the details, I'm sorry to say I don't know the name but I wanna be able to play all the multimedia files (in the format MP3, AVI, MPG, VOB, and a whole lot of others). Currently Ubuntu asks me to install software for them and that's what I don't know how to do. But the procedure I wanna learn should be a general one, so that I could find and install all other software in a similar manner. I mean, guide me about a consistent and general approach that's applicable to installing any kind of software. Thanks again.

---

### Post by ajgreeny on 2010-01-26
Hi again, and sorry for being a bit unhelpful about how to do this.  I do think, however, that it will not be easy.

Firstly on your ubuntu machine use the package manager to try to install a package. I know it will not be possible, but bare with me at the moment.  The system will then tell you of any dependencies that also need to be installed, and you must make a note of all of those, or if using synaptic go to "file, save markings as" and a text file with all the info will be saved to your home folder, listing everything marked.

Now on your winxp machine go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and navigate to your version and eventually to each of the listed package files.  Download them all from there and copy them to ubuntu with a usb drive or other means.  Put them all into a folder in your home, open a terminal and cd to that folder, and then run ```
sudo dpkg -i *.deb
```As long as all the dependencies for everything are in that folder the whole lot should be installed in that one command.

For the various codecs you need start with all the gstreamer good, bad and ugly plugins, then the w32codecs which you can get from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) along with libdvdcss2.  Try that to start and then you may also find others that are needed as you go along.

I hope that is more what you were hoping for, and that it does work out for you.

---

### Post by linotechie on 2010-01-26
Thank you very much. I'll do that as soon as I get to the system. (It's 29 miles from the XP system.) The instructions look easy and straightforward. The only thing is I shouldn't be making a note of all those dependancies because I feel that's a work for the machine, not for the human. In other words, I'd want to know what synaptic is, how to get it (from another computer that is connected to the internet), and then how to install it.

But never mind you've already helped a great deal. I'll try to search and if a problem should appear, I'll post here again. Have a nice day.

---

### Post by ajgreeny on 2010-01-26
Synaptic is the ubuntu package manager, which is installed in all ubuntu OSs at the moment.  It will produce the text file I spoke of even when the computer is not attached to the web, ie your ubuntu machine that this query is all about will be able to produce that file.  

That list is very important as you will not be able to run the programs you install, and in fact not even install them, without all the dependencies packages being in the same home folder as I described, and from which you run the ```
sudo dpkg -i *.deb
``` command.

---

