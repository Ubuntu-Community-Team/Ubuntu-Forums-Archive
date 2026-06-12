---
title: "Help"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Waxo on 2005-06-22
Hello,
I have this problem, when i install my ubuntu linux everything goes OK but when it finishes and is loading something suddenly the screen shows that the computer turned off but it didn't, then i press the ON botton, when i press the botton it appears a black screan and it says tu put my user and when i try to put the user the keyboard doesn't work and after 10 seconds the computer just shuts off...


Please i need help please...i really want ubuntu on my computer and not windows..

Waxo,
Regards

---

### Post by az on 2005-06-22
It sounds like a video card problem.

Can you boot into recovery mode?

If you can, type 
lspci
and loof for the line that has "VGA controller" or anything else relevant to your video card.  Come back and post that information.

It may be something else, but let's start with that...

---

### Post by Waxo on 2005-06-22
Here is what it shows when i put lspci...

[IMG]http://img262.echo.cx/img262/24/dsc016050ux.jpg[/IMG]

---

### Post by az on 2005-06-22
Hmm..  You have an S3 video card so that should nto be a problem.  Did the install go fine?

If you boot normally, wait a minute after the screen goes blank and see if you can switch into the terminal by hitting CTRL-ALt-F1.

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]Hmm..  You have an S3 video card so that should nto be a problem.  Did the install go fine?

If you boot normally, wait a minute after the screen goes blank and see if you can switch into the terminal by hitting CTRL-ALt-F1.[/QUOTE]
 thanks, now i can type, but now it shows me this...

[img]http://img178.echo.cx/img178/8092/dsc016094jg.jpg[/img]

---

### Post by az on 2005-06-22
1-  try:
sudo apt-get -f install
and then
sudo apt-get install ubuntu-desktop

2-  Try 
sudo /etc/init.d/gdm stop
startx

and it will display the x error messages (if any) on the console (switch back to it if you need to)

3-  type dmesg
and hit right-SHIFT-PAGEUP to scroll up to display those errors that are on the top of the page in your last photo...

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]1-  try:
sudo apt-get -f install
and then
sudo apt-get install ubuntu-desktop

2-  Try 
sudo /etc/init.d/gdm stop
startx

and it will display the x error messages (if any) on the console (switch back to it if you need to)

3-  type dmesg
and hit right-SHIFT-PAGEUP to scroll up to display those errors that are on the top of the page in your last photo...[/QUOTE]
 here are the errors...

[img]http://img174.echo.cx/img174/2051/dsc016105it.jpg[/img]

---

### Post by az on 2005-06-22
Hmm.. Nothing unusual there.  Does it take you to a blank screen or dump you back into the console?

Are there any lines that start with (EE)?

When gdm starts, you should heard sounds (drums).   Do you head anything?

Try 
sudo dpkg-reconfigure xserver-xorg

and  make sure you are using the S3 driver for X.  Also, perhaps change the color depth to 15 bit?

I do not know what else to tell you...  I am assuming that it is an X (display) problem.  The fact that you are able to get back into the console, as well as having ubuntu-desktop properly installed means that you have a working system. 

How old is your machine and have you installed other distributions?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]Hmm.. Nothing unusual there.  Does it take you to a blank screen or dump you back into the console?

Are there any lines that start with (EE)?

When gdm starts, you should heard sounds (drums).   Do you head anything?

Try 
sudo dpkg-reconfigure xserver-xorg

and  make sure you are using the S3 driver for X.  Also, perhaps change the color depth to 15 bit?

I do not know what else to tell you...  I am assuming that it is an X (display) problem.  The fact that you are able to get back into the console, as well as having ubuntu-desktop properly installed means that you have a working system. 

How old is your machine and have you installed other distributions?[/QUOTE]
 here an screen after reconfiguring the x

[IMG]http://img51.echo.cx/img51/4868/dsc016113fq.jpg[/IMG]

---

### Post by az on 2005-06-22
That's fine...

---

### Post by az on 2005-06-22
I have an old machine with an S3 video chip.  It has 1 meg of vram.  It can only handle 15-bit.

try 15 bit.


How old is your machine?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]That's fine...[/QUOTE]
 ok...i'm in now, now when i try to install something this happens...

[img]http://img95.echo.cx/img95/2893/dsc016123qb.jpg[/img]

---

### Post by az on 2005-06-22
So, was the problem the color depth?  It would be helpful to others if you answered.


Also, it would seem that you are trying to run an exe file.  

This is not windows.  Linux does not use exe files.

What software do you need?  The is surely an ubuntu equivalent that you can install.  Use synaptic.  Are you on the net in ubuntu?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]So, was the problem the color depth?  It would be helpful to others if you answered.


Also, it would seem that you are trying to run an exe file.  

This is not windows.  Linux does not use exe files.

What software do you need?  The is surely an ubuntu equivalent that you can install.  Use synaptic.  Are you on the net in ubuntu?[/QUOTE]
 yes, it was the color depth, and i'm trying to install the router so i can go to the internet in that computer, and i'm not in the net using linux, i'm with windows in this computer

---

### Post by az on 2005-06-22
Once you are no the net in ubuntu (should be a snap with your router) you can searchsynaptic for software that you need.  If there is not enough choice in the main repositories, you can add the universe repositories and that pulls in more than 10 000 more packages for you to chose from....


What software do you need?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]Once you are no the net in ubuntu (should be a snap with your router) you can searchsynaptic for software that you need.  If there is not enough choice in the main repositories, you can add the universe repositories and that pulls in more than 10 000 more packages for you to chose from....


What software do you need?[/QUOTE]
 i dont exactly know what software, but the router is a D-Link

---

### Post by az on 2005-06-22
[QUOTE=Waxo]i dont exactly know what software, but the router is a D-Link[/QUOTE]
I meant that you were trying to install an exe in linux....


You should be able to configure your router from firefox

192.168.0.1
?

---

### Post by Waxo on 2005-06-22
i tried to put 192.168.0.1 on firefox but it could not connect to it

---

### Post by az on 2005-06-22
You have two ethernet cards, yes?  Are you using the right one?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]You have two ethernet cards, yes?  Are you using the right one?[/QUOTE]
 i have a router on this computer, this is the main one and this one has windows xp, and the other one has a wireless card for the router

---

### Post by az on 2005-06-22
Okay, the output from lspci from your first screenshot shows two ethernet controllers:

A realtek and a Marvell.

When you say you have a router on this computer, you mean that it is connected to this computer, right? Am I correct that you have two ethernet cards?  Was your ethernet card detected during the installation?

Show the output of

sudo ifconfig

---

### Post by Waxo on 2005-06-22
the ethernet card is the realtek....how do i check the sudo ifconfig when i'm in linux?

---

### Post by az on 2005-06-22
Open up a terminal.  Applications, system tools:

---

### Post by Waxo on 2005-06-22
this is what appears when i do that...

[img]http://img226.echo.cx/img226/1244/dsc016132xj.jpg[/img]

---

### Post by az on 2005-06-22
Use the networking tool in the administration menu.  Setup an ethernet interface.  Use dhcp.

You should be able to reach your router that way....

Then try 192.168.0.1 in firefox again.

---

### Post by Waxo on 2005-06-22
This is what i've done in the networking tool...

[img]http://img157.echo.cx/img157/74/dsc016158la.jpg[/img]

[img]http://img157.echo.cx/img157/8855/dsc016147yz.jpg[/img]

---

### Post by az on 2005-06-22
Sudo ifconfig should now show you that you have an eth0 interface.

---

### Post by Waxo on 2005-06-22
now what should i do?...it showd me that i have an eth0 interface but it doesn't open the 192.168.0.1

---

### Post by az on 2005-06-22
I don't know.  You are connected to your router by dhcp.

What does ifconfig say is your ip address?

---

### Post by Waxo on 2005-06-22
[QUOTE=azz]I don't know.  You are connected to your router by dhcp.

What does ifconfig say is your ip address?[/QUOTE]
 this...
[img]http://img291.echo.cx/img291/5958/dsc016163ho.jpg[/img]

---

### Post by az on 2005-06-22
Try:

sudo dhclient eth0


( I will no longer be able to answer you as rapidly anymore today, sorry...  I'll be back tomorrow...  Perhaps someone else could jump in too?)

---

### Post by Waxo on 2005-06-22
this is what appears when i put that....

[img]http://img212.echo.cx/img212/1984/dsc016189ia.jpg[/img]

---

### Post by az on 2005-06-22
Is your router set up to accept dhcp connections?

Can you get through to it from your other box through a wired connection?

---

### Post by mingus on 2005-06-22
Your NIC is loaded, but you are not receiving an IP address from the router.

Try to ping the router.  In the terminal -

$ping -c 4 192.168.0.1

you should get 4 replies that look something like -

64 bytes from 192.168.0.1: . . . . . .

if you do not, make sure of the router's address.  Some use 192.168.1.0 (instead of .0.1)

also, now that the NIC is configured, reboot the computer and again do

$sudo ifconfig

on the second line you should see something like:

inet addr:  192.168.0.xxx   Bcast:  192.168.0.xxx   Mask:  255.255.255.xxx

---

### Post by FLeiXiuS on 2005-06-23
[QUOTE=mingus]
if you do not, make sure of the router's address.  Some use **192.168.1.0** (instead of .0.1)
[/QUOTE]
That would be a network address for a /24 network.  

D-Link by default uses 192.168.1.1.  Of course the best way to trouble shoot this would be to ask if your ethernet port on the router interface has a green lights.  

If so, awesome, your sending and receiving packets to and from the router.  If not, well then you should test the ethernet cable / router configurations.  Just to make sure the router isn't blocking access to that port.  

So the lights are green and things are great, well...obviously something is wrong here, right?  Do you have windows on this computer?  If so, do you pick up an IP address via DHCP automatically?  If this is the case then your missing  a module for your ethernet port.  If not, well then it's all about the routers settings.

Perhaps DHCP is disable or just not functional!  Well I have only one more recommendation which you can try.  This is setting a static IP address on eth0.  

**Setting a Static IP**
Click _System_ then navigate to _Administration_ then to _Networking._  Then click on eth0, and then properties.  From the drop down menu select static IP.  Enter the following: 

IP Address: 192.168.1.200
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

Press OK then OK again.  And your settings should now be set.  Ok so now that everything is set.  Lets test out some pings.  Open a terminal(Applications>System Tools>Terminal) and enter the following:
$ ping -c 3 192.168.1.1

Did any packets return with a message saying received?  If so, awesome!  That just told us your router is not running DHCP.  Now you should beable to browse to: [http://192.168.1.1](http://192.168.1.1) and change your configurations.  From here you can then enable DHCP.  Consult your routers manual / website help boards for more answers.

I have only a couple more idea's for you to try.  Perhaps your /etc/hosts file is not configured properly.  Which would completely block all interfaces from working.  :-P.  Easy fix.  Open a terminal again following the directions above.  Enter the following:
$ sudo echo "127.0.0.1     localhost.localdomain localhost `hostname`" > /etc/hosts

Other then this I would like to know what router do you have exactly?  And if DHCP worked with windows.  Is this at home, or at work?  Was the router given to you or did you purcahse it band new?  It's the little things that matter.  

If you want to really get tricky, you could download and install ethereal.  Ethereal is a packet capturing device.  What this will allow you to do is see if your ethernet interface is receiving packets and from where they are coming.  This way you could gain information about your network whether it's DHCP or static.  Also, the IP addressing scheme.  


Anyways, GOODLUCK!  I hope this was any of help.

---

### Post by mingus on 2005-06-23
[QUOTE=FLeiXiuS]That would be a network address for a /24 network.  

D-Link by default uses 192.168.1.1.  Of course the best way to trouble shoot this would be to ask if your ethernet port on the router interface has a green lights.  [/QUOTE]

My D-Link's is 192.168.0.1 and my Linksys's is 192.168.1.0 - these are the factory defaults.  The router's IP and NAT range can be changed by the user.

Waxo, checking the lights can be helpful.  Your D-Link probably has at least several green lights (mine has 8).  The WLAN indicates the router is communicating with your ISP, the LAN light indicates the router has activated the local network, and the numbered lights (1 for each wireline port) indicate communication with the computer connected to that port.

---

### Post by Waxo on 2005-06-23
the router green lights, and 0 packages where received when i did the ping thing,, 100% were lost

[IMG]http://img71.echo.cx/img71/1402/dsc016190cs.jpg[/IMG]

---

### Post by az on 2005-06-23
On your other computer which is connected to the router, when you go to the router configuration page, what does it say about dhcp?

---

### Post by Waxo on 2005-06-23
in this computer there is no configuration for the router, the only router is the one i took picture of and is for this computer and the other one has a wireless cable that connects to this router

---

### Post by mingus on 2005-06-23
azz . . . thought I'd pitch in a bit . . .

Waxo, looks like a DI-524 . . . the default IP is 192.168.0.1 (and assuming that wasn't changed) . . . 

the page in your router configuration that azz is referring to is this one . . . 
[http://support.dlink.com/emulators/di524/h_dhcp.html](http://support.dlink.com/emulators/di524/h_dhcp.html)

also check the log here, look for a connection attempt from your computer's network MAC address (in your ifconfig picture, that's the 12 character alpha/numeric in the upper right corner)
[http://support.dlink.com/emulators/di524/st_log.html](http://support.dlink.com/emulators/di524/st_log.html)
be sure that the log is set up under "Log Settings" to log everything (check all boxes)
[http://support.dlink.com/emulators/di524/st_log_settings.html](http://support.dlink.com/emulators/di524/st_log_settings.html)

if this doesn't tell you anything, then reboot the router here,
[http://support.dlink.com/emulators/di524/tools_misc.html](http://support.dlink.com/emulators/di524/tools_misc.html)
and then look at the log again.  You should see the router making the connection again with your ISP and then re-connecting to your wireless computer and trying to connect to your wireline Ubuntu

If you cannot access the router from your other wireless computer, then there is a router problem.  It may be locked up.  Instructions to reset are at:
[http://support.dlink.com/SupportFAQ/default.asp?model=DI%2D524](http://support.dlink.com/SupportFAQ/default.asp?model=DI%2D524)

---

### Post by mingus on 2005-06-23
[QUOTE=Waxo]in this computer there is no configuration for the router, the only router is the one i took picture of and is for this computer and the other one has a wireless cable that connects to this router[/QUOTE]

Isn't that a DI-524????

---

### Post by Waxo on 2005-06-23
it is a DI-524 :)

---

### Post by mingus on 2005-06-23
[QUOTE=Waxo]in this computer there is no configuration for the router, the only router is the one i took picture of and is for this computer and the other one has a wireless cable that connects to this router

it is a DI-524 :)[/QUOTE]

OK.  Let's just be sure we are all talking about the same thing.

There is one router.  Two computers, one physically connected to the router with a cable and the other that uses a wireless connection.  This router has a configuration utility that can be used from a web browser on *either* of these computers.  The configuration utility is not tied to one computer or another; it is only in the router itself.  Both computers are set up with this utility.

We are suggesting you go to the second computer connected to the router with wireless, open whatever browser you use on it, and do 192.168.0.1.  There you should see the screens that I linked in my previous post.

---

### Post by Waxo on 2005-06-25
[QUOTE=mingus]OK.  Let's just be sure we are all talking about the same thing.

There is one router.  Two computers, one physically connected to the router with a cable and the other that uses a wireless connection.  This router has a configuration utility that can be used from a web browser on *either* of these computers.  The configuration utility is not tied to one computer or another; it is only in the router itself.  Both computers are set up with this utility.

We are suggesting you go to the second computer connected to the router with wireless, open whatever browser you use on it, and do 192.168.0.1.  There you should see the screens that I linked in my previous post.[/QUOTE]
 this computer from where i'm posting is the one that has the router, this one has windows xp, the other computer has the wireless and has ubuntu and i'm trying to get internet there :)

---

### Post by mingus on 2005-06-25
[QUOTE=Waxo]this computer from where i'm posting is the one that has the router, this one has windows xp, the other computer has the wireless and has ubuntu and i'm trying to get internet there :)[/QUOTE]

From your post and reading back through this thread, maybe we had a communication problem . . . let's try one more time . . .

Is the computer that you are *now* posting from physically connected to the router with a cable?  And that computer is running XP?  And when you type 192.168.0.1 in the XP computer's browser do you see the router interface?

And the computer that you installed Ubuntu on has two ethernet devices?   One is a *wireless* card?  And the Ubuntu computer also have a *second* ethernet device that uses a *cable* connection?  And so with the Ubuntu computer, *which*  ethernet device are you trying to communicate to the router with - the cable or the wireless?  

I think you may have the cable ethernet configured (the realtek) but not the wireless (the Marvell).  But you want to use the wireless, right?

---

### Post by az on 2005-06-25
I did not realize that the Marvell was a wireless nic.

If you are trying to use wireless, you need ndiswrapper:

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

Again, this whole problem seems to be a useability one...  A user is not given intuitive options in such a situation....

---

### Post by mingus on 2005-06-25
[QUOTE=azz]I did not realize that the Marvell was a wireless nic.

If you are trying to use wireless, you need ndiswrapper:

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

Again, this whole problem seems to be a useability one...  A user is not given intuitive options in such a situation....[/QUOTE]

azz, it's the Marvell W8300 chipset.  Waxo, some wireless have their own driver, but only I could find was ndiswrapper ("wraps" the Windows driver, so not actually a Linux driver).   Note that modprobe parms may be needed depending on the card it's in.  Take a look at:

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)

Also found this ref re the 2.6.12 kernel:
[http://www.linuxhq.com/kernel/v2.6/12-rc1-bk6/drivers/pci/pci.ids](http://www.linuxhq.com/kernel/v2.6/12-rc1-bk6/drivers/pci/pci.ids)
Does this mean the chipset now has support in this kernel version?

---

### Post by Waxo on 2005-06-25
the other one with ubuntu i want to use the wireless one that is communicating with the calbe router in this computer with xp

---

### Post by mingus on 2005-06-25
As I posted before, it looks like this wireless chipset is only supported now with ndiswrapper.  Azz linked to the procedure for setting this up.  You may need your Windows driver.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

And again, before you do that, check this

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)

Search the page for "Marvell W8300" looking for your particular wireless card make/model.  When you do the modprobe command described in the wiki howto, you may need to add parameters specific to your card.

---

### Post by FLeiXiuS on 2005-06-25
Gracias mingus for handling the situation, sorry but i've been busy from wednesday till now (saturday).  They should get him started.

---

