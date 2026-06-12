---
title: "How to return to Gnome desktop"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by redmon on 2011-10-15
I have seen two recommendations for returning to the Gnome desktop:  gnome-session-fallback or gnome shell.  What is the difference?  Is one preferable to the other?

---

### Post by MAFoElffen on 2011-10-15
> **redmon said:**
> I have seen two recommendations for returning to the Gnome desktop:  gnome-session-fallback or gnome shell.  What is the difference?  Is one preferable to the other?
Welcome to Ubuntu!

I've answered on how to get your gnome panels going:
[http://ubuntuforums.org/showpost.php?p=11348567&postcount=2](http://ubuntuforums.org/showpost.php?p=11348567&postcount=2)

I'm not sure what the difference is.  I know I install the "GNOME Desktop environment with extra components."  That is what is in the Ubuntu Software Center.  

Ubuntu's gnome-session-fallback? What are the differences?
[URL="http://www.ubuntuupdates.org/packages/show/320617"]
[/URL]

---

### Post by redmon on 2011-10-15
Thanks for your reply, MAFoElffen.

I tried installing "GNOME Desktop environment with extra components" and received this error message:

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:
gnome: Depends: gnome-core (= 1:3.0+1ubuntu1) but 1:3.0+1ubuntu1 is to be installed

---

### Post by Jesuswashomeless on 2011-10-26
I have been trying to get the Gnome desktop running and the best I have right now is that it is on the log on screen but when choose it strange things happen I.E. the menu bar canges on it's own to what looks like a file menu bar then the whole desktop becomes unresponsive I can't even shut it down. The cursor moves but nothing. I have tried installing both gnome-session-common and gnome-session-fallback as advised but I am getting dependency error messages:

newbie@newbie-OptiPlex-GX270:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree
Reading state information... Done
gnome-shell is already the newest version.
The following packages were automatically installed and are no longer required:
 libpanel-applet-4-0 alacarte gnome-applets python-gmenu gnome-panel
 gnome-applets-data gir1.2-panelapplet-4.0 gnome-panel-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
newbie@newbie-OptiPlex-GX270:~$ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-session-fallback : Depends: gnome-session-common (= 3.2.0-0ubuntu2) but 3.2.0-0ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.


Please help I am stuck in unity!
I am new to posting so please forgive any faux pas and I welcome help in that area as well.

---

### Post by redmon on 2011-10-27
> **Jesuswashomeless said:**
>  I have tried installing both gnome-session-common and gnome-session-fallback 

I am not an expert at this, but do not think you should install both gnome shell and gnome fallback.  I cannot use Unity3D, do not care for Unity2D, and get top menu bar and unusable black screen below bar with GNOME3.  In looking for how to revert to previous version of gnome, I found recommendations for installing either, but not both, gnome shell or gnome-session-fallback - that was the reason for my original question with this thread.  I decided on gnome shell.  Now on my login screen, I have choices for GNOME (3?), GNOME Classic (gnome shell), and Unity 2D.

---

### Post by Frogs Hair on 2011-10-27
After installing the Gnome Shell pkg. on 11.10 from the software center my login options appear as below .

Gnome
Gnome Classic 
Gnome Classic (no effects)
Ubuntu 
Unity 2D

I don't know what the Gnome 3 option is . :confused:

---

### Post by redmon on 2011-10-27
> **Frogs Hair said:**
> I don't know what the Gnome 3 option is . :confused:

Gnome 3 is the "Gnome" login option.  My computer does not have the graphic resources to run Gnome 3, so that is why I installed gnome shell and use Gnome Classic.

---

### Post by Frogs Hair on 2011-10-27
11.10 runs unity or the Gnome Shell if installed on top of Gnome 3 , so even if you can't run Unity 3D or the shell you are still using Gnome 3 . Any release  before 11.10 runs on Gnome 2.xx .

---

### Post by redmon on 2011-10-27
> **Frogs Hair said:**
> 11.10 runs unity or the Gnome Shell if installed on top of Gnome 3 , so even if you can't run Unity 3D or the shell you are still using Gnome 3 . Any release  before 11.10 runs on Gnome 2.xx .

Thank you for clarifying!  I was hoping someone who knew what they were doing would jump in on this.

So the Gnome Shell changes the appearance of Gnome 3? I installed gnome shell because I cannot run the "Gnome" login option.  I get a top menu bar with Activities and a blank black screen below.  If I try to open anything, it does not appear in the black screen.  The "Gnome" option is completely useless for me. After installing gnome shell, I got the "Gnome Classic" login option, which gives me a layout similar to what I had in 11.04 - which would be Gnome 2?

Can you answer my original question - what is the difference between gnome shell and gnome-session-fallback?  And which is preferable?

---

### Post by cbowman57 on 2011-10-27
gnome-session-fallback is what gives you that "classic" Gnome desktop. gnome-shell is just a different DE.

I prefer gnome-shell, but a lot of people prefer the classic desktop because it's more familiar.

---

### Post by kurt18947 on 2011-10-27
> **redmon said:**
> Thank you for clarifying!  I was hoping someone who knew what they were doing would jump in on this.

So the Gnome Shell changes the appearance of Gnome 3? I installed gnome shell because I cannot run the "Gnome" login option.  I get a top menu bar with Activities and a blank black screen below.  If I try to open anything, it does not appear in the black screen.  The "Gnome" option is completely useless for me. After installing gnome shell, I got the "Gnome Classic" login option, which gives me a layout similar to what I had in 11.04 - which would be Gnome 2?

Can you answer my original question - what is the difference between gnome shell and gnome-session-fallback?  And which is preferable?

With the "useless black bar"showing, does anything happen when you either press the left "windows" key or poke the mouse cursor in the upper left corner of the screen? If not, your graphics subsystem won't support Gnome-shell or Unity. As others have said, Gnome-classic or Gnome-classic no effects is least demanding of the graphics subsystem. Gnome-classic may look sort of like Gnome 2's screen but many functions and most add-ons found in Gnome2 are not available in Gnome-classic. If I were you, I might try an Xubuntu or Lubuntu live CD/USB. If the graphics work there, you could install the distro of your choice.  You might also be able install Xfce4-desktop which I've done and it works pretty well. This however was on a system that will run both Unity & Shell so I don't know if that would work for you. 

It seems a fair number of people that don't care for Unity or gnome-shell have moved to Xfce or Xubuntu. The advantage of Xfce-desktop over Xubuntu to me is that I kept the Gnome apps like Libre Office & FireFox. Xubuntu would have given me Abi Word, Chromium etc. There are alternatives available.

---

### Post by redmon on 2011-10-27
> **kurt18947 said:**
> With the "useless black bar"showing, does anything happen when you either press the left "windows" key or poke the mouse cursor in the upper left corner of the screen?

The top bar has Activities and a few icons.  When I select Activities, I see a dim desktop with a bar on the left.  Selecting any of the programs on the left bar results in a black screen below the top menu bar.  That is as far as I can go with it.

I do have Xfce desktop installed and it works well.  That is probably the direction to go with this computer.  I have also tried Mint 11, based on 11.04.

Unfortunately, I have a bigger problem, the subject of a different thread, with 11.10 unable to detect my Brother usb printer/scanner.  Installation of an updated kernel has solved the problem for some, but not me.

---

### Post by kurt18947 on 2011-10-27
It does indeed sound like the all-singing-all-dancing interfaces are a bit much for your machine.  I have two Brother Multi-function machines. Check the FAQs at Brother's Linux pages.  There is a problem with the 64 bit scanner driver, the printer has functioned as expected.  I don't think the scanner fix is required for 32 bit O.S.s but the FAQ is pretty clear I think.  There is also editing necessary to a file,  it's talked about on the Brother pages,  there's a link about USB installation.  I have it in another places if you need it.

---

