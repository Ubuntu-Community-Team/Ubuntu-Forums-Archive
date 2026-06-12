---
title: "Dial-up Modem?  Which brand &amp; model can be used? Where available?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by C. Slawski on 2008-10-20
I have just been able to install Ubuntu for the first time.  One of the books said that I must use an external serial port type.  My 52K US Robotics Model 0525, has capability to use USB or serial, which might mean that it is really only a USB non-hardware type, thus not usable by Linux.  My older external modem, a Hayes Accura 5901US, ver. 7.20 is still functioning.  I tried to dial with both.  The AT&T ISP local number was dialed but no connection was ever made by either modem and I was disconnected every time.  The book says this may indicate that the modems are incompatible with Ubuntu.
   Does anyone out there have an external modem for dial-up use that is still available commercially and will actually connect with Ubuntu?
   My phone service in this area is Verizon.  AT&T is my long distance carrier, but they do not give DSL service to my neck of the woods, perhaps because I am in a canyon which makes it difficult to hear many radio stations, which may be why AT&T does not give DSL service to this zip code, 91320.  
   Neither AT&T nor AT&T gets good ratings for reliability and service.  I do not have cable or satellite service either.  My needs seem to be served satisfactorily with dial-up, and I would just as soon keep it that way, saving half the monthly cost of DSL or broadband service.
 Again the main question is: What external dial-up modem currently available at stores or web sellers will work with Linux Ubuntu?
Thanks from Carl S.

---

### Post by robert shearer on 2008-10-20
Hi. here are a couple of links to read...
[http://ubuntuforums.org/showthread.php?t=948788](http://ubuntuforums.org/showthread.php?t=948788)
[http://ubuntuforums.org/showthread.php?t=779213](http://ubuntuforums.org/showthread.php?t=779213)
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
[https://help.ubuntu.com/8.04/internet/C/modem.html](https://help.ubuntu.com/8.04/internet/C/modem.html)
If you need help with kppp then let me know.:)

---

### Post by C. Slawski on 2008-10-22
> **robert shearer said:**
> Hi. here are a couple of links to read...
[http://ubuntuforums.org/showthread.php?t=948788](http://ubuntuforums.org/showthread.php?t=948788)
[http://ubuntuforums.org/showthread.php?t=779213](http://ubuntuforums.org/showthread.php?t=779213)
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
[https://help.ubuntu.com/8.04/internet/C/modem.html](https://help.ubuntu.com/8.04/internet/C/modem.html)
If you need help with kppp then let me know.:)
Thanks Robert S. for the references.
   I had previously looked into a couple of your URL's.  The one with "technion" in it did not connect or respond for me.
   I did s web search and found several longish pieces on KPPP, but was unable to get a valid response, or puzzled about which one I could trust for a currently valid download.  Any recommendations for the best current KPPP download site?
   It does look a bit obscure and technical.
   Hope all is well and peaceful, even economically, in New Zealand these days!
BEST from Carl S.

---

### Post by robert shearer on 2008-10-22
Hi Carl,
The kppp package is available through the Ubuntu package manager.
On your computer...System=>Administration=>Synaptic package manager.

When it opens...Settings=>Repositories.... and when the window opens put a tick in the first four boxes. 
Close and you will be prompted to reload.

Then use Synaptics search box to find and install kppp.
This is the easiest way to satisfy all the dependencies needed.

Of course this needs to be done with an internet connection and if that is what you are trying to get with Ubuntu it is self defeating!:(

Because of the kde libraries needed as dependencies it is a big download and difficult to configure manually from another machine if all you want is the packages to burn to a cd and take home to install on your machine.

EDIT) this application may allow you to download/update from another machine.It has been designed with dial-up users in mind...
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

On occasion I have found that booting the live Ubuntu cd with my modem connected caused the connection to be made automatically but I could never get it to persist once installed.(other than installing and configuring kppp)
 
However if this happens for you you may want to download the kpp app and dependencies (check the download only option on the final window in Synaptic once you have chosen to install these.) while using the live cd.

Then burn these to cd  reboot without the live cd and load the burnt cd.
Synaptic will recognise it, and ask if you want to open it with the package manager.

Click yes and wait.Once the cd is loaded then open Synaptic and click the reload button.
Search for kppp and it should be available.Click to install and it should be downloaded from your burnt cd.

Of course this needs a computer with two disc drives.:(

By far the easiest way is to get a Kubuntu install cd as kppp comes with Kubuntu and so do the libraries needed to run it.

You can then choose to install Kubuntu instead of Ubuntu or (my preferred option) add the Kubuntu cd to your Repositories in Synaptic and install kppp and libraries to Ubuntu from the Kubuntu cd.

You can download Kubuntu on another machine and burn to disc or order the official  Kubuntu cd The first is recommended for speed.

I got round this by ordering a copy of Kubuntu on cd (making sure that it was the same release as the Ubuntu I had installed) and adding this to my synaptic repository.

System=>Administration=>Synaptic Package manager
Then Settings=>Repositories=>Third party software=>add cdrom

This adds the information on packages on the Kubuntu disc and then search for kppp in synaptic and mark it for installation.
The package/s will be downloaded from the disc.

Sorry about the length of this post, hope it is of use and Yes ,life is well and peaceful other than the usual froth that goes with an election.(Both ours and yours):)

---

