---
title: "Need Help installing the (server) base version of ubuntu"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by John.Michael.Kane on 2005-09-08
I'm trying to install the base version of ubuntu and using these guides.

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

sudo apt-get install fluxbox x-window-system-core xdm mozilla-firefox synaptic

following this [http://ubuntuforums.org/showthread.php?t=42873&page=1](http://ubuntuforums.org/showthread.php?t=42873&page=1)
and i got know where..

running in  the mode the server install gives me i have no net access so i need to know exactly how it is done, and if im missing any steps? 

Thanks

---

### Post by Strider on 2005-09-08
Does the system recognizes your network card?  Do you have DHCP running on your network?

---

### Post by John.Michael.Kane on 2005-09-08
What network i have a single laptop with ppoe dsl access.

---

### Post by az on 2005-09-08
How do you usually get on the net?

---

### Post by az on 2005-09-08
[QUOTE=SD-Plissken]What network i have a single laptop with ppoe dsl access.[/QUOTE]
From a console, do

sudo pppoeconf

---

### Post by Strider on 2005-09-08
[QUOTE=SD-Plissken]What network i have a single laptop with ppoe dsl access.[/QUOTE]

Take a look at ubuntuguide.org ([http://ubuntuguide.org/)](http://ubuntuguide.org/)).  They have a section on getting PPoE working.

You will probably have to disable the network during the install and once install is completed follow the directions on getting PPoE working, or get yourself a router at home.  Makes life easier. :)

---

### Post by John.Michael.Kane on 2005-09-08
@ azz i use sudo pon dsl-provider to log on...

---

### Post by az on 2005-09-08
I would forget about the script and sources list, too.  Just edit your default list and uncomment all the deb repositories (universe and so forth)

sudo nano /etc/apt/sources.list


sudo apt-get update
sudo apt-get install x-window-system-core xdm mozilla-firefox fluxbox menu synaptic.

---

### Post by John.Michael.Kane on 2005-09-08
@Strider your telling mei have to buy a router to use these guides listed here come on. not everyone here has routers.. i would think theres some here who still use dial up..

---

### Post by John.Michael.Kane on 2005-09-08
@azz thanks will try that...

one more thing can this be run from the server install i did not think there was a termal or anything installed. or should i try to get pppoeconf running

---

### Post by az on 2005-09-08
[QUOTE=SD-Plissken]@azz thanks will try that...

one more thing can this be run from the server install i did not think there was a termal or anything installed. or should i try to get pppoeconf running[/QUOTE]


Terminal or console.  Same thing.  I should have said command line.

---

### Post by Strider on 2005-09-08
[QUOTE=SD-Plissken]@Strider your telling mei have to buy a router to use these guides listed here come on. not everyone here has routers.. i would think theres some here who still use dial up..[/QUOTE]

Just making a recommendation.

Try what azz said to get the ppoe working.  There's no GUI installed when you have the server installed, you just get a text based console which you can type the apt-get commands and run ppoeconf/etc.

Hope it works.

---

### Post by John.Michael.Kane on 2005-09-08
will try it thanks....

---

### Post by John.Michael.Kane on 2005-09-08
one more question. my network card is seen during the set up.. will i have to activate it in the console? or thats not a problem..

---

### Post by az on 2005-09-08
If your card is detected by the installer that means that the driver is loaded into the kernel.  You do not need to activate the card.  You need to activate the conection by either Static, dhcp or pppoe, depending on your Internet service provider.  You use pppoe.

---

### Post by John.Michael.Kane on 2005-09-08
Thanks.. for all the info..

---

### Post by John.Michael.Kane on 2005-09-08
Thanks azz and Strider however after many installs no go.. fluxbox dont like my laptop firefox gives an error synaptic dont work ect. so looks like im stuck with gnome for a desktop. thanks again.

Also maybe theres a more stable way to switch gui's so i can get rid of gnome oh well.. Thanks

---

### Post by wvslkr on 2005-09-08
Did you not read the other thread you had in Other Applications?  You can still run other wms even if Gnome is installed.  Flux is just plain buggy in Ubuntu.

Anyway GL.

---

### Post by John.Michael.Kane on 2005-09-08
wvslkr Thanks. i dont want gnome on the machine at all. i was looking for a replacement. and flux did not work. i was looking to find out what is stable and lite gui, and who installed it and how. you could have atleast told me what your using and how you installed and if it's stable. thanks..

---

### Post by wvslkr on 2005-09-08
I use all of the ones I mentioned and have had no stability problems with any other than Flux as I said.  If you don't want Gnome you can uninstall it with Synaptic.  For ease of use Xfce is probably the easiest on a fresh install.  That is why I suggested installing more than one.  Only you can decide which you like the best.

---

### Post by John.Michael.Kane on 2005-09-08
wvslkr thanks... I will be doing the install using the base install of ubuntu which is the server install..

---

### Post by az on 2005-09-08
Try icewm.  It is rock solid.

It has pretty much the same features as fluxbox.

sudo apt-get install icewm menu

You need the menu package, too.


Try out xfce4, too.  It has more stuff, but less than gnome.  It does use GTK, like gnome.

---

### Post by John.Michael.Kane on 2005-09-08
Thanks

---

### Post by John.Michael.Kane on 2005-09-09
Update: I have xfc4 installed using the way listed below. only issues are theres no icon or access to synaptic or
 software update program bothof which used to be listed in gnome. i just wondered how i can get these programs back.  please let me know if i did something wrong or if i missed a step. Thanks..


Here's how i installed xfce4 
sudo apt-get install wdm x-window-system-core xfce4 mozilla-firefox acpi acpid powermanagement-interface synaptic


Edit: I have looked this over. it was seem that all these files are needed to get update and synaptic to work.. if im wrong please explain thanks..
[http://packages.ubuntu.com/hoary/admin/synaptic](http://packages.ubuntu.com/hoary/admin/synaptic)
[http://packages.ubuntu.com/hoary/gnome/update-manager](http://packages.ubuntu.com/hoary/gnome/update-manager)
[http://packages.ubuntu.com/hoary/gnome/update-notifier](http://packages.ubuntu.com/hoary/gnome/update-notifier)

---

### Post by wvslkr on 2005-09-09
It appears you allready installed synaptic, open a terminal and type in sudo synaptic,  it
should run then.  You can find the other programs and mark them for install.  You don't have to hunt the dependencies they will be installed along with the program.  Just make sure all of the repositories are enabled.

Have Fun.

---

### Post by John.Michael.Kane on 2005-09-09
wvslkr Thank you very much now i have to figure out how to set up the icons and menu ect..

---

### Post by wvslkr on 2005-09-09
Check the extra packages for xfce in synaptic.  Search xfce.  They are helper apps to manipulate configs.  The titles are pretty much self explanatory and you will get a brief description of each one if you highlight it.

---

### Post by xequence on 2005-09-09
[QUOTE=SD-Plissken]Update: I have xfc4 installed using the way listed below. only issues are theres no icon or access to synaptic or
 software update program bothof which used to be listed in gnome. i just wondered how i can get these programs back.  please let me know if i did something wrong or if i missed a step. Thanks..[/quote]

I only know one thing, sorry :P

You say there are no icons on the desktop? It is supposed to be that way I think.

---

