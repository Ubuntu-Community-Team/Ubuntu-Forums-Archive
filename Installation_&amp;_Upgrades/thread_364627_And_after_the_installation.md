---
title: "And after the installation???"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by stenci on 2007-02-18
Friday I got a new computer to install Ubuntu, and after almost 2 days of attempts the frustration level is high and I'm ready to give up.
The graphic is slow, the modem doesn't work, the wireless internet doesn't work, and I'm not finding any help here in the forum.

I assumed I was part of a large group of beginners with Windows experience trying to install Ubuntu in a new computer, but apparently I was wrong.
Nobody here refers to Windows terminology, neither tries to help the beginners. 
As a beginner I would very much appreciate some reference to the well known Windows (more people in the world know Windows that Linux, and most of the people approaching Linux already know Windows).
Instead I feel like there is a wall against people that know about Windows. For example [this ]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")step-by-step guide uses terms like "managed mode" or "ESSID" that I don't understand. 
Is there any step-by-step guide telling you "here is how to do in Windows, and here is how to do the same in Linux"?

I also assumed I was part of a large group of beginners that the first thing after the installation configures the network in order to have access to all the available internet resources, but apparently I was wrong again.
All the posts that I found assume you already are able to browse the network. 
How can you do that without configuration?
It didn't work to me. What's wrong with me?

What's wrong with my assumptions?
Do I need to give up and go back to :( Windows?
Or do I need to try in another way (please tell me the good way)?

Thanks,
Stefano

---

### Post by teaker1s on 2007-02-18
firstly is your wireless up and running but you don't know how to connect?
essid is what you called your wireless on your router
If you have ethernet access then terminal
[COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]
will make wireless a point and click logon provided your wireless is running and ethernet cable is removed

---

### Post by stenci on 2007-02-18
> firstly is your wireless up and running but you don't know how to connect?In Windows it works, in Ubuntu id doesn't. I posted [this ]("http://www.ubuntuforums.org/showthread.php?t=364328")in the Networking & Wireless forum with some more details.
> essid is what you called your wireless on your router
Thank you.
> If you have ethernet access then terminal
My problem is that I don't have ethernet access.
> sudo apt-get install network-manager-gnome
will make wireless a point and click logon provided your wireless is running and ethernet cable is removed
sudo apt-get ... never works to me. I think because I miss something, but I don't know what.
__________________
> First place to look if new at ubuntu
broadcom wireless ndiswrapper the easy wayI already went through them (and many others), but it didn't help.
> ubuntu packages without internet access
I will go through this and I hope it will help.
> politeness costs nothing, so when requesting help it pays to be polite I didn't want to be rude. I didn't say "you didn't even make a guide for Windows users", I asked if that guide exists.

---

### Post by tesuki on 2007-02-18
to get the graphics speed up you need to install the drivers for your graphic card.
if you have a nvidia graphics card you should install "nvida-glx" or if you have an older nvidia card try the "nvidia-glx-legacy", to install them you need to enable some Repositories, you do that by starting up synaptic you'll find it in System -> administration -> synaptic package manager
now you need to type in the your password.
from here go to the menu "settings -> Repositories" now a dialog window opens press the "add"-button and one more dilog popsup now mark all the for check boxes and press "Add" then in the previous dialog press "Close". now you need to update the repositories by pressing the "Reload" button. now all you need to do is search for "nvidia" and you will find se some items int the list to the right. "Nvidia-glx" right click that item and press "mark for installalation" and "apply". part one done.
now you need to tell Xorg to use the driver this is a bit trickier (X is the screen manager in windows I have no clue what they callit there)
You need to open upp the terminal and write:
```
sudo gedit /etc/X11/xorg.conf
```
now you need to find the line: Section "Device"
in that section you will se the: Driver "nv"
change that line to: Driver "nvidia"
and save the file.
done restart X by pressing ctrl + alt + backspace
if you have a ati card. don't search for nvida search for fglrx. i think...
backup the xorg.conf file before editing it.

---

### Post by stenci on 2007-02-18
Thank you tesuki, I already found this info in the documentation and in the forum.
But again it refers to an installation with internet access. 
I don't have internet access. 

I think it is possible to find out what files I need, download them with another computer, burn a CD, copy them and install them in Ubuntu.
Or perhaps it's better to to this in order to have internet up and running before, and then use the repositories.

---

### Post by teaker1s on 2007-02-18
okay looking at your wireless post it appears your wireless is natively supported in ubuntu and your issue is configuring it. I'm just looking for some info 
brb

---

### Post by benson444 on 2007-02-18
I can't answer your question as I have no experience of the problem. But don't give up. Take your time and learn about the OS. It's not Windows and there's little point comparing the different ways of doing things. In Windows you download a file and double click it. You don't know what it does, but it seems to work... In Linux you have to at least be slightly interested in learning about what's going on. You have to hack config files (probably), learn a few commands and you'll come across more technical terms. It's easy to learn some basics though. Web searches are helpful. If you want to know about something just Google it. I'd recommend dual booting and when you've had enough for a while just go back to Windows. Over time you'll probably find that you use Windows less and less. Just spend some time with it. You aren't going to learn much in a couple of days.

---

### Post by teaker1s on 2007-02-18
are you using 6.06lts or 6.10edgy

---

### Post by tesuki on 2007-02-18
ohh sorry didn't take that in account. it is possible to install without internet access. all you need is a free USB slot, and a USB memory. venture to the adress: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
and download the packages from there.
the packages have a .deb extension.
to isntall:
```
dpkg --install package_name.deb
```
if it say somthing about dependencies missing search for the package at the site and downlaod taht and install that first. and do that untill you have installed the package you needed which is for the nvidia card "nvidia-glx". you can also se needed packages on the site.
when you have isntalled it it saies you should type the command:
```
sudo nvidia-glx-config enable
```
if it works you don't need to use gedit to edit xorg.conf

---

### Post by teaker1s on 2007-02-18
or burn to cd
**regarding wireless**
you want to download and burn alternate.iso 
burn iso image to cd
boot ubuntu
terminal type [COLOR="Red"]gksudo synaptic[/COLOR]
hit edit tab and select "Add CD-ROM" and insert alternate iso when it asks for cd
hit reload tab
search and install [COLOR="Red"]network-manager-gnome[/COLOR]

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by mikewhatever on 2007-02-18
Hi Stenci,
let me begin from the end of your initial post. What's wrong is that you have too many Windows based assumptions, and Ubuntu is not Windows. This is the way it seems to be, and probably not going to change for better or worse. I'd suggest taking things easy, learning gradually and gaining experience. A great part of learning anything new is getting yourself familiar with the terminology. Wikipedia and Google have been very helpful on this.
[http://en.wikipedia.org/wiki/ESSID](http://en.wikipedia.org/wiki/ESSID)
I think you get frustrated too easily, probably because you feel you know Windows, so Ubuntu should be easy. The howtos and instructions are not written specially for Windows users and not even with Windows in mind.
Perhaps [this tread]("http://ubuntuforums.org/showthread.php?t=63315&highlight=is+ubuntu+for+you") will help you decide whether or not to go back to Windows. Contrary to many here, I have nothing against that OS. You should use it if you are happy with it. Finally, there seems to be so many other Linux distros, that I really hope you'll find one that suits you. It's a good idea to dual boot too, at least until you feel more experienced and confident in Linux.

Good Luck and of cause welcome.

---

### Post by TheWizzard on 2007-02-18
first, stop complaining. i'm very sorry you didn't find the perfect manual for you, but complaining doesn't help anyone. if you feel a certain manual is missing, write it yourself! 
and read this: [http://www.ubuntuforums.org/showthread.php?p=1488521#post1488521](http://www.ubuntuforums.org/showthread.php?p=1488521#post1488521)

second, buy an ethernet cable and connect your computer to your router. 

third, ask for help differently.  your quest for help here ([http://www.ubuntuforums.org/showthread.php?t=364328](http://www.ubuntuforums.org/showthread.php?t=364328)) won't get you further because all you do is telling you followed a guide that didn't solve your problem. if you have trouble with a specific guide, post there. 
if you want to be helped in general, make a new post with sufficient information about your system and with usable information: 
- does your router work with other (windows) pc's? 
- is your wifi card usb or pci? 
- what is the chipset of your wifi card?

good luck

---

### Post by Maimonides on 2007-02-18
LOL... just for the record, I know Stenci... and just talked to him about his manners. Apparently someone told him how to partition his brand new HDD incorrectly (not me) in the forums and now his brand new Vista doesnt work. Spent 3 hrs on the phone with HP and they said he needed to buy new Vista...   I'd be pissed at everything and everyone if that happened to me (it's happened... don't buy DELL)... he says he's sorry

---

### Post by mikewhatever on 2007-02-18
Doesn't HP provide a recovery tool for Vista?

---

### Post by stenci on 2007-02-18
mikewhatever,
I've been system administrator for a Unix network for 10 years before 1998. I know that using vi to configure /etc/hosts and /etc/passwd as I used to is not going to help me much now (but makes me feel 15 year younger :)).
And I think it is normal feeling some frustration after spending 10+ hours trying to configure a wireless card and failing only because of lack of documentation.

Perhaps my wrong assumption was that other people install Ubuntu in computer without the ethernet cable.
I not going to give up. I just need help to get started with the wireless connection. Then I will get rid of 15 years of rust and perhaps in a few months I will be able to contribute and help other people.

teaker1s,
Thanks for the help. I'm downloading now an alternate.iso, hopefully the right one.
In 40 min I will try and see if I can finally start.

TheWizard, 
I'm not complaining, I'm asking for help.
I already read the post about the fisherman, and I agree with that.
And I don't agree that "complaining doesn't help anyone". How can you fix bugs if nobody "complains" or reports them? 
And also looking at my post I think my tone wasn't bad, I can only see technical deatils useful to whoever wants to help me.
I put all the information I had, including the fact that I use USB, I didn't say the router works with Windows (sorry, I considered it obvious), I don't know the what chipset I have. I found 4-5 posts telling how to find it out, no one was clear enough for me to find it out. Now I don't remember all the commands I used, but I redirected the output of all the commands I found in the doc and the posts to a file, then I searched for the word chipset (and similar) in the file. Now I have a 97 lines file containing all the info about the vendor, the manufacturer, etc., nothing about the chipset.
Perhaps this mean I'm a little retarded, perhaps the documentation is not clear enough.
My opinion is that it is not clear for a first time installer without internet access.

---

### Post by mikewhatever on 2007-02-18
I may be too late, but there is another way of getting gnome network manager. Someone here put together a package with dependencies and all
[http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945](http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945)

if the link doesn't work, I have the package and can upload it. You'll need removable media though.

I have to say, that I've written the above based on something that applies to many users including myself. Just like you, I had no internet connection and had to reboot to Windows every time I was asked to type a command. That was kind of frustrating.

The link does work. Checked just now.

---

### Post by stenci on 2007-02-18
Using the edgy eft alternate.iso I was able to install the network manager.
Now system - administration - networking shows 3 connections in the dialog box:
- wireless connection
- wired connection
- modem connection
I think this means that my USB wireless card is working and visible.

I'm getting close!

This is my working Windows configuration:
- Network name (SSID): my network name, selected from a list of available networks
- Network Authentication: Open
- Data Encryption: WEP
- Network key: my 10 digit password
- Key index (advanced): 1
- Enable IEEE 802.1x authentication for this network: unchecked

This is my not yet working Ubuntu configuration:
- Enable this connection: checked
- Network name (ESSID): my network name, manually typed
- Password type: I tried both hexadecimal and Plain
- Network password: my 10 digit password
- Configuration: Automatic Configuration (DHCP)

The DNS page is empty.
The Hosts page contains the usual local IPs.

What is my next step? What do I miss?
Does anybody know how to/if it is possible to copy the Windows configuration?
Is there a "view available wireless networks" button here?

---

### Post by TheWizzard on 2007-02-19
for the chipset, post the output of ```
lsusb
```

for the network settings, post the output of ```
cat /etc/network/interfaces
```
and ```
iwconfig
```

---

### Post by teaker1s on 2007-02-19
**your wireless appears natively supported**

**specifically type exactly as below and install**
[COLOR="Red"]network-manager-gnome[/COLOR]


**now on your desktop panel you want to click system administration networking**

[B]it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key
[/B]

---

### Post by stenci on 2007-02-19
I was able to get this:
- iwlist scan shows a list of available networks
- iwconfig says signal level zero.

The I gave it up trying to configure the wireless without an internet connection, so I moved all my stuff close to the router and I used a wired connection to install graphic card driver and other stuff.

Then I followed [these]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") steps. Now when I click on the icon next to the volume I see the list of available networks, but they all have empty signal bar.

Then I installed Wifi-radar. Same problem: The list of available networks appears, but the signal bars are all empy.

This are the command outputs after all this process:
> stefano@StefanoLinux:~$ lsusb
Bus 002 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

stefano@StefanoLinux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
#
#
#iface eth0 inet dhcp
#
#auto eth1
#iface eth1 inet dhcp
#
#
#iface eth2 inet dhcp
#wireless-essid think3
#wireless-key s:3124989731
#
#auto ath0
#iface ath0 inet dhcp
#
#
#auto eth2

stefano@StefanoLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"think3"  
          Mode:Managed  Channel=11  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by teaker1s on 2007-02-19
I'm at a loss of what to suggest it appears wireless is working but poor signal, have you tried clicking on the networks to logon?

---

### Post by stenci on 2007-02-19
Yes.
If I click on the network asks for the passphrase. The default is WEP 128-bit passphrase and Open System. I tried all the 6 combinations but it never works.
This morning I'm the only available network. Yesterday there were 4 more networks, and if I'm not mistaken some of them gave different defaults (not sure, I can't try now).

It does what Windows does when there is no signal.
And does the same with all the networks, not just with mine.

Is there any diagnostic tool to use to better understand what's going on?

---

### Post by teaker1s on 2007-02-19
I'm stumped as what to suggest next, you could try ndiswrapper and the windows drivers-if nobody else knows how to resolve this

---

### Post by TheWizzard on 2007-02-20
> **stenci said:**
> 

#iface eth2 inet dhcp
#wireless-essid think3
#wireless-key s:3124989731
#
#auto ath0
#iface ath0 inet dhcp
#
#
#auto eth2



ok, your wireless interface seems to be eth2 (from iwconfig)

edit /etc/network/interfaces
```
sodu nano -B /etc/network/interfaces
```

remove the "#" before the eth2 entries and (i thin) the"s:" before your wep key. make the eth2 entry look like this: 
> auto eth2
iface eth2 inet dhcp
wireless-essid think3
wireless-key 3124989731
save the file and reboot.

---

