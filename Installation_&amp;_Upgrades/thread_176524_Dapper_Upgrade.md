---
title: "Dapper Upgrade"
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by majkmil on 2006-05-14
I am waiting for the official release of Daper to upgrade from Brezzy. I read the WIKI upgrade page at the top of this page. When I tried to upgrade from warty I used apt-get and I was not successful. I hope to have a better experience this time. What is the safest way to upgrade ( CD, Synaptic, apt-get)? Do I need to do anything about my propietary ATI drvers I am using? Any other issues I should look out for? What about unoficial packages like LimeWire? I really would like to upgrade without having to do a fresh install. I will be greatful for any help.      Mark

EDIT: Do you need to edit the sources.list file when using the cd to upgrade?

---

### Post by Dr. Nick on 2006-05-15
ifoyou use the cd it may update the list for you. Before upgrading install the package ubuntu-desktop so you are sure to get all the new files included in  dapper and not breezy for the best expierence.

I have had good luck using apt-get from recovery mode. For ati just make sure that  it gets updated, or that you know how to edit /etc/X11/xorg.conf to a suitable video vard to atleast get you a gui

And of course backup important data just in case

---

### Post by aysiu on 2006-05-15
The safest way is to follow these steps:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

It won't guarantee nothing will break, but it will minimize the likelihood that something will.

---

### Post by majkmil on 2006-05-15
Will I get a new kernel with the upgrade? And if so wont I just have to reinstall the ati driver (proprietary). I thuoght I already had ubuntu-desktop. Wht do the instructions say to install it? I think I will wait a little while after the update is released so the servers are not as busy.   Thanks
Will the printer and wifi drivers still work after upgrade?

---

### Post by aysiu on 2006-05-15
[QUOTE=majkmil]Will I get a new kernel with the upgrade?[/quote] Yes. > And if so wont I just have to reinstall the ati driver (proprietary). I don't know. >  I thuoght I already had ubuntu-desktop. You probably do. If you do, there's no harm in asking to install it--you'll just get the message that it's already the newest version. > Thanks
Will the printer and wifi drivers still work after upgrade? The printer drivers still work for me, but I didn't have to do anything special in the first place to get them to work. I don't have WiFi.

---

### Post by majkmil on 2006-05-15
I have heard a lot of people complaining they cannot start X after upgrade. Does this have to do with the video driver? Can I just reinstall the default fglrx driver in command mode? Also some have said they neede to edit there xorg.conf file, can you help me with this?
               Thanks

---

### Post by Dr. Nick on 2006-05-15
Most likely if X wont start its video related
You dont have to reinstall the fglrx driver, just edit xorg.conf to make it use it,

If X fails to start due to video and your left at command based login, then login as usual and when you have a prompt type 

sudo nano /etc/X11/xorg.conf

if nano command is not found then do the sudo apt-get install nano, Once Xorg.conf is open look for Device section and change the  driver to fglrx then hit ctrl+x to save and then either type "startx" or just reboot.

Concerning wifi it depends, How did you set it up origionally? Most likely it will still work if it was autodetected for you, or you are using ndiswrappper. But if you compiled them from a souce file (unlikely) you would just have to recompile. My wifi saw many an upgrade without issuse

---

### Post by majkmil on 2006-05-15
Thanks Nick, I have already upgraded to dapper with update manager. Unfortunatly it frze at the pcmcia probe. I cant get into my k7 kernel but I can get into i686 kernel with limited use. I do not have networking GUI. Do you know how to configure network interface in terminal? If that fails i am going to try the live cd with synaptic. Any ideas?  Thanks

---

### Post by Dr. Nick on 2006-05-15
[quote=majkmil]Thanks Nick, I have already upgraded to dapper with update manager. Unfortunatly it frze at the pcmcia probe. I cant get into my k7 kernel but I can get into i686 kernel with limited use. I do not have networking GUI. Do you know how to configure network interface in terminal? If that fails i am going to try the live cd with synaptic. Any ideas?  Thanks[/quote] 
I can give you some basics to configuring, Im not sure exactly what you need to do but here are sume commands
[COLOR=Red]
sudo ifup device_name[/COLOR] ex. eth0, wlan0 to enable the device
[COLOR=Red]sudo ifdown device_name[/COLOR] ex. eth0, wlan0 to disable the device
[COLOR=Red]sudo dhclient[/COLOR] to attempt to get an IP
[COLOR=Red]ifconfig [COLOR=Black]shows status of each device
the file /etc/network/interfaces has some various settings 

If the card isnt shouwing up you need to find out what module it uses and use 
sudo modprobe *module *to use it.

If you need more specific info ask and ill see what i can do
[/COLOR][/COLOR]

---

### Post by majkmil on 2006-05-16
ifup wlan0 shows no device, It worked before out of the box. My wired connection is being used by my windows comp to download the dapper iso. I think I will pause the download and try the wired. If I use the cd to upgrade with synaptic will I run into the same problem with the pcmcia probe thing. I dont understand this. I am on a desktop comp not a laptop.

---

### Post by Dr. Nick on 2006-05-16
before doing the ifconfig did you do the sudo ifup wlan0?

So you are on a desktop with a wireless pci or usb card and not a pcmcia? I dont know why pcmcia would mess it up then.

Not sure i teh cd upgrade would help or not.

---

### Post by majkmil on 2006-05-16
I did ifup wlan0 and it said no device. The cd is almost downloaded so I will wait and then switch to wired and try ifup etho0 or etho1 and see what happens. I have to switch my monitor from one computer to the other and it is time consuming. I am talking to you on a Ibook. I am all over the place and determined to fix this upgrade without having to do a fresh install. But if not I can live with it. I did do some backup.  Thanks for your time.  Mark

---

### Post by Dr. Nick on 2006-05-16
Have you seen the /etc/network file yet?

Here is mine
> 
drnick@Springfield:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys 


Its not much help, I would just check you have a entry for each card. And I hope those were just typos in your last replay on the etho0

iwconfig gives you some wireless info aswell, not much different from ifconfig though.

I am betting it didnt load your modules for the network cards up. the modules must be loaded before ifup will work. If you are downloading the live cd then you may be able to compare how it sets it all up with your current config.

Good luck, Its midnight here so it will be a few hours before i get back to the boards  :D

---

### Post by majkmil on 2006-05-16
Nick you have been great, ThankYou.  Believe it or not I got IT! I edit a network interface file, all I did was add DHCP to the end of the line that said eth0. Internet came up and I did dpkg --reconfigure -a and it finished the install! You were very helpful and I was very lucky. I have the2.6.15-22-k7 kernel running and all seems OK. Since this is probably the last beta before the final release will a upgrade bring me up to speed with anything that has changed after this release? Thanks again      Mark

---

### Post by Dr. Nick on 2006-05-16
[quote=majkmil]Nick you have been great, ThankYou.  Believe it or not I got IT! I edit a network interface file, all I did was add DHCP to the end of the line that said eth0. Internet came up and I did dpkg --reconfigure -a and it finished the install! You were very helpful and I was very lucky. I have the2.6.15-22-k7 kernel running and all seems OK. Since this is probably the last beta before the final release will a upgrade bring me up to speed with anything that has changed after this release? Thanks again      Mark[/quote]

Glad you got it!

Upgrades from now until the release date will be mainly to fix bugs. Once dapper is officially released, upgrading will bring you to the final stable release just as if you installed fresh off the final dapper cd. Further updates after that will again be any bug fixes and security updates.

You will not get new beta stuff for the next version once dapper is released without making changes to your repositories. 

I updated just today and still have the same kernel, you could upgrade again but probably wouldnt notice any difference. The big changes for dapper are over for the most part I would think

---

