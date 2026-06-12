---
title: "Services"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Satendra.kohli on 2009-12-04
I am using ubuntu 9.10, in menu system --> administration 
there is no service menu. i want to know about, how to install GUI service manager in ubuntu 9.10

---

### Post by phillw on 2009-12-04
> **Satendra.kohli said:**
> I am using ubuntu 9.10, in menu system --> administration 
there is no service menu. i want to know about, how to install GUI service manager in ubuntu 9.10

Hi,

What do you mean by 'Service' ? What are you looking to be able to do ?

Regards,

Phill.

---

### Post by Satendra.kohli on 2009-12-04
> **phillw said:**
> Hi,

What do you mean by 'Service' ? What are you looking to be able to do ?

Regards,

Phill.

We are looking how to start and stop services using GUI tool

---

### Post by phillw on 2009-12-04
What Services are you referring to ? I think you are thinking of the background processes that Win runs - Ubuntu does not work that way.

Regards,

Phill

---

### Post by dhavalbbhatt on 2009-12-04
Unlike Windows, Linux does not have "Services". If you want to find out what processes are running on your computer, use the following command in a terminal -

ps -x

---

### Post by mkvnmtr on 2009-12-04
I believe it is there under Administration on my 9.10. You might look under menu to see if yours in not enabled.

---

### Post by scottuss on 2009-12-04
> **phillw said:**
> What Services are you referring to ? I think you are thinking of the background processes that Win runs - Ubuntu does not work that way.

Regards,

Phill

> **dhavalbbhatt said:**
> Unlike Windows, Linux does not have "Services". If you want to find out what processes are running on your computer, use the following command in a terminal -

ps -x

Ubuntu does use background processes, and certainly does run services (more commonly known as daemons)

For an easy GUI way, download Ubuntu Tweak and check the Autostart tab to edit services that start up with Ubuntu.

---

### Post by phillw on 2009-12-04
> **scottuss said:**
> Ubuntu does use background processes, and certainly does run services (more commonly known as daemons)

For an easy GUI way, download Ubuntu Tweak and check the Autostart tab to edit services that start up with Ubuntu.

The difference between Services & daemons and processes between the two O/S's is quite a lot. A lot of 'Services are built into the kernel - Getting a new-comer to re-complies their own kernel is not to be advised.

Killing processes willy nilly within Ubuntu is not recommended either. If you wish to stop a process, you can issue the stop command from the Terminal. 

> Uninstalling the service is quite unnecessary. There are always ways to stop them and keep them from starting up on boot. I admit that in Ubuntu I haven't found an easy way to do this since the Services GUI is quite useless, it will not go into Admin mode (for me). In Fedora, there is chkconfig which is quite easy to use and does not require uninstalling the programs. In truth , uninstalling software manually under linux is not a good idea unless you are absolutely sure of what you are doing. 
 
What chkconfig really does is get rid of the script in the corresponding folder (depending on the run level you are at) which is usually /etc/rc5.d. When you shut down, then the scripts in that folder will be shut down. The ones that will startup up begin with a capital S, the ones to shut down with a capital K. 
 
Don't mess too much with this stuff if you don't know what you are doing. 
 
I have to add though, that bluetooth, etc is NOT part of the kernel, they are daemons that you CAN prevent from starting up and indeed you should if you do not need them. 
 
For bluetooth specifically, you can delete this script from /etc/rc5.d:
 
S25bluez-utils 
 
it is only a softlink to another script in /etc/init.d/bluez-utils. Make sure you do not delete the ones in /etc/init.d, just the links in the /etc/rc5.d. That way you can always get them back by creating another soft link. 
 
Now, I'm new to ubuntu (but I checked all this that I am saying before posting and indeed it is the same as in Fedora) and would like to know if there is a gui or command line tool to manage services. Having to delete the links manually is quite a chore. 
 

> sudo apt-get install sysv-rc-conf
 
this is to get the software, then you run it with this: sudo sysv-rc-conf
 
It looks a lot like chkconfig. Will allow you to start and stop services at boot. You probably want to stay with the number 5 where it says services, this is the run level with a graphical interface, leave the rest as is. 
 
Cheers
      [IMG]http://www.linuxforums.org/forum/linux2/statusicon/user_offline.gif[/IMG]   						 		 		 		 		  	     [[IMG]http://www.linuxforums.org/forum/linux2/buttons/quote-new.gif[/IMG]]("http://www.linuxforums.org/forum/newreply.php?do=newreply&p=364171")

Regards,

Phill.

---

### Post by scottuss on 2009-12-04
> **phillw said:**
> The difference between Services & daemons and processes between the two O/S's is quite a lot. A lot of 'Services are built into the kernel - Getting a new-comer to re-complies their own kernel is not to be advised.

Killing processes willy nilly within Ubuntu is not recommended either. If you wish to stop a process, you can issue the stop command from the Terminal. 





Regards,

Phill.


Who said anything about re-compiling kernels?

Most things that people would want to enable/disable can easily and safely be done through a tool like Ubuntu Tweak.

We don't need to make things so complicated!

---

### Post by Ordes on 2010-01-02
In Jaunty there was in System > Admin > Services

In was a GUI to enable services at boot (not startup applications), e.g u have ssh server, u could easily turn it on or off at boot... This is gone now. I dont like it neither... It was an easy and fast way to manage your init.d ....

Now the only GUI u have left is startup applications, which is not the same as services.. 

[http://ubuntuforums.org/showthread.php?t=1301543](http://ubuntuforums.org/showthread.php?t=1301543)

But i am not sure how to solve this now, as i always did it the GUI.
Perhaps someone here knows, e.g for open-ssh

How i can enable/ disbale it at boot....

---

### Post by karmic-koala on 2010-01-27
No body's mentioned the Boot Up Manaager. You can install bum by

sudo apt-get update
sudo apt-get install bum

Bum displays all your daemons in a wee box where you can select /deselect / start/stop/restart daemons.

---

### Post by scottuss on 2010-01-27
I love Linux package names. Bum and GIMP have to be two of my favourites.

Yes, I realise it's slightly immature ;p

---

### Post by Ordes on 2010-01-27
... i am not talking about the boot manager. but in jaunty there was a tool called service that enabled u to enabled/ disable services. However as services run in the background, as daemons, they are mostly all started at boot...

anyways...

if by start & stop, u just mean start & stop (e.g ssh):
$ sudo /etc/init.d/ssh start
$ sudo /etc/init.d/ssh stop

if by start and stop u mean stopping from booting up

$ sudo update-rc.d ssh enable
$ sudo update-rc.d ssh disable

>> if u want to remove them completly
$ sudo update-rc.d ssh remove

>> if u want to see all running processes (either system monitor, or in terminal)
$ ps -e 
or
ps -e | sort -k4    (sort k4 will sort the by their name, which is column four >> k4)

---

