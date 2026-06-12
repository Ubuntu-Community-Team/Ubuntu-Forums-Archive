---
title: "Completely newbie guide for installing in an old machine and sharing internet"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by daigorobr on 2005-07-22
These are two subjects that seem to create most confusion on newbies like me.
Happily, with some nice friends and 5 minutes of googling, I got to go over both problems and will share the solutions here.

1. Old computer Linux
I am using a K6-233 with 64 megs RAM and a cheap and old Cyrix PCI graphics adapter. I thought the [Mini-RAM Howto](http://ubuntuforums.org/showthread.php?t=9670) is very good but have to say that the **only** window manager that could show things properly here was XFCE4, so I think that instead of

```
$ sudo su -
# vi /etc/apt/sources.list
(If you are not familiar with vi you can use nano or any other texteditor instead.)
Enable the universe-repository by removing the Hashmarks (=# (2 times))
# apt-get update
# apt-get install icewm
# apt-get install xserver-xfree86
# apt-get install x-window-system-core
# apt-get install xdm
# apt-get install numlockx
# apt-get install xterm 
```

I would use

```
$ sudo su -
# vi /etc/apt/sources.list
(If you are not familiar with vi you can use nano or any other texteditor instead.)
Enable the universe-repository by removing the Hashmarks (=# (2 times))
# apt-get update
# apt-get install xfce4
# apt-get install xserver-xfree86
# apt-get install x-window-system-core
# apt-get install xdm
# apt-get install numlockx
# apt-get install xterm 
```

I got to install and use Firefox and Gaim without problems with these settings.

2. Share internet connection
Okay, I know every case is different, but most people helping in the forums seem to forget that newbies sometimes are **completely** clueless.
My main computer is a fairly fast Kubuntu machine with eth1 linking to the ADSL modem and eth0 to the client computer via a crossover cable.

For the server machine I edited /etc/network/options and set
```
ip_forward=yes
```
and later ran
```
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
echo "1" > /proc/sys/net/ipv4/ip_forward
```

For the client, I had to write a /etc/resolv.conf file saying
```
nameserver "server ip"
```

And voilà, the machines are alright now!

---

### Post by SamSung on 2005-07-24
Thanks for the newbie guide, I have a problem when trying to get this to work so any help would be good. 

I have installed the base system of ubuntu

I have followed the instructions and have managed to successfully install xserver and xwindows but cannot install the following

XDM
NUMLOCKX
XTERM
ICEWM or XFCE4

when I try do do so using the commands as suggested by your guide the error I get is the following

Couldnot stat source package list.
You may want to run apt-get update to correct these problems.
Could not find package PACKAGENAME

I did run the apt-get update succesfully the first time, but if I run the command now I get this message

Temporary failure resolving and then a web address.

I have not configured a web address so far on this machine so if this process is supposed to use the web it will not work.

Any help that you can give to help a newbie would be gratefully recieved.

Cheers

Sam

---

### Post by daigorobr on 2005-07-24
[QUOTE=SamSung]Thanks for the newbie guide, I have a problem when trying to get this to work so any help would be good. 

I have installed the base system of ubuntu

I have followed the instructions and have managed to successfully install xserver and xwindows but cannot install the following

XDM
NUMLOCKX
XTERM
ICEWM or XFCE4

when I try do do so using the commands as suggested by your guide the error I get is the following

Couldnot stat source package list.
You may want to run apt-get update to correct these problems.
Could not find package PACKAGENAME

I did run the apt-get update succesfully the first time, but if I run the command now I get this message

Temporary failure resolving and then a web address.

I have not configured a web address so far on this machine so if this process is supposed to use the web it will not work.

Any help that you can give to help a newbie would be gratefully recieved.

Cheers

Sam[/QUOTE]
 Oopsie. That's because i forgot to tell you to use the universe and multiverse repositories.
You have to edit your apt sources (sudo nano /etc/apt/sources.list) and uncomment (remove the # mark) all the lines that start with "deb".
And you should also add
> ## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
to it.

Now it should work perfectly.

---

### Post by SamSung on 2005-07-25
Thanks for the quick reply I had already uncommented the universe repositories in the sources list. But I had not uncommented ALL the lines begining with deb and neither had I added the two lines suggested in your last post.

I have now uncommented ALL the lines in the sources list begining with deb and added the other two lines.

I have run the commands agian to install

XDM
NUMLOCKX
XTERM
ICEWM or XFCE4

Still no joy and still the same message

Couldnot stat source package list.
You may want to run apt-get update to correct these problems.
Could not find package PACKAGENAME

As I mentioned last time I have no Internet connection on this machine and would not know how to set one up without a graphical interface. DOES THE PC NEED TO HAVE AN INTERNET CONNECTION.

OK where do we go from here again thanks for the help so far please help me a bit more.

Cheers

Sam

---

### Post by ingo.lists@vum.at on 2005-07-25
Hi Samsung,
let me sumerize your problem: You want to install some packages to get the GUI. Therefore you need an internetconnection. In order to get the internetconnection you need the GUI. So called "Deadlock". Is this correct?

Ingo.

---

### Post by daigorobr on 2005-07-25
[QUOTE=SamSung]Thanks for the quick reply I had already uncommented the universe repositories in the sources list. But I had not uncommented ALL the lines begining with deb and neither had I added the two lines suggested in your last post.

I have now uncommented ALL the lines in the sources list begining with deb and added the other two lines.

I have run the commands agian to install

XDM
NUMLOCKX
XTERM
ICEWM or XFCE4

Still no joy and still the same message

Couldnot stat source package list.
You may want to run apt-get update to correct these problems.
Could not find package PACKAGENAME

As I mentioned last time I have no Internet connection on this machine and would not know how to set one up without a graphical interface. DOES THE PC NEED TO HAVE AN INTERNET CONNECTION.

OK where do we go from here again thanks for the help so far please help me a bit more.

Cheers

Sam[/QUOTE]
 Oooops. I think I overlooked the internet portion.
Yes, you have to have internet to download these files.

Which connection is yours? Can't you **really** configure it from console?

---

### Post by SamSung on 2005-07-25
Yes Ingo

i am in need of installing the packages and need the GUI to do so.

What do I do ?

Sam

---

### Post by SamSung on 2005-07-25
OK Maybe I can configure it from the console if I knew what I was doing is there a how to to enable me to do that. I have a DSL connection via ethernet

---

### Post by ingo.lists@vum.at on 2005-07-25
[QUOTE=SamSung]Yes Ingo

i am in need of installing the packages and need the GUI to do so.

What do I do ?

Sam[/QUOTE]
Two ways to brake the deadlock:
1. Installing the packages w/o Internet: Its possible, if you can download them elsewhere, and transfer them on CD, USB-Stick or whatever to that machine. Using the dpkg-family of commands, you can then install the packages. It may be, that these packages require you to install others - so called dependency.
2. Configering the internetconnection via commandprompt: Well, this depends a lot on your provider. Commands you should learn:
ifconfig
route ("route add default")
pppd
dhclient (or may be different on Ubuntu)

HTH, Ingo.

P.S. You know this group? [email]ubuntu_lite@googlegroups.com[/email]

---

### Post by daigorobr on 2005-07-25
[QUOTE=SamSung]OK Maybe I can configure it from the console if I knew what I was doing is there a how to to enable me to do that. I have a DSL connection via ethernet[/QUOTE]
 It's DSL thru a router or thru a PPPoX?

If it is thru router, just letting it online on installation would do the job for you. With the exception of the DNS server (that is the modem ip) that you should add manually by

sudo nano /etc/resolv.conf

> nameserver router-ip

And you are good to go.

---

### Post by SamSung on 2005-07-26
Hi Again

Thanks for the information Ingo I will try and use dpkg to resolve this I have found a howto at [https://wiki.ubuntu.com/PackageManagementHowTo](https://wiki.ubuntu.com/PackageManagementHowTo) which will allow me to start at least.

Cheers

Sam

---

