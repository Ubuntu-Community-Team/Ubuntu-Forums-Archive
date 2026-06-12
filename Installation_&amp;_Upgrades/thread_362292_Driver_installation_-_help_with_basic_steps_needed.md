---
title: "Driver installation - help with basic steps needed"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Ethelbert2 on 2007-02-15
[FONT="Georgia"][SIZE="3"][COLOR="DarkOliveGreen"]I have installed Ubuntu 6.10 on a P111 with 500MBG RAM. I am experimenting iwth Linux to see how it goes. Installation was OK except I had to use the text based installation as the window one froze.
Now I need help installing a driver.
It is for a wireless card. From the network manager it is listed with a Realtek chipset (rtl8185) but does not work. I was going to install NDIS wrapper and find a windows driver but, after ages trawling around,, by chance I found an actuall Linux driver (!!) though hidden away on the Taiwan website of Realtek (I can give a link if anyone is interested.) 

A purpose made Linux driver would be better I suppose - it says it runs with Debian 3.1 among other distributions.

I used a WinXP computer to download the collection of files in it. This is one of two Win computers working on a wireless broadband link but I would really like to get the Linux machine linked too which would be a big step forwards.

The driver comes with various files including two files of commands, which help the installation, and instructions - but unfortunately I do not know how to get as far as those instructions.

So here is a bit of the readme file telling what is included:[/COLOR][/SIZE][/FONT]

[SIZE="1"][COLOR="Sienna"]The driver is composed of several parts:
(1)source code
r818x.tar.gz
stack.tar.gz

(2)Script ot build the modules
makedrv

(3)Script to load/unload modules
wlan0up
wlan0down

(4)Script and configuration for DHCP
wlan0dhcp
ifcfg-wlan0

(5)Supplicant source code
wpa_supplicant-0.3.8.tar.gz

(6)Example of supplicant configuration file
wpa1.conf[/COLOR][/SIZE]

[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]This is fairly clear I agree. As far as it goes. It goes on to tell you what to do, but presupposes some confidence with Linux - but I am an utter beginner and there are unanswered questions which prevent me getting to first base. 

It says:
[/FONT][/SIZE][/COLOR]
[SIZE="1"][COLOR="Sienna"]< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:[/COLOR][/SIZE]
[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]
So that means some of it is taken care of. The makedrv file contains a sequence of instructions for example which I assume takes care of the proper sequence of commands. Then instructions spell out some commands  ----[/FONT][/SIZE][/COLOR]

[SIZE="1"][COLOR="Sienna"](1)Build up the driver from the source code
**./makedrv**[/COLOR][/SIZE]

[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]But where and when do I enter this command? (In the command line window obviously but should I put all the files listed above in a particular place first (eg on a floppy)? 
If I do, do I have to navigate to that directory (and how do I do that?)
Do I enter that command as it is or do I have to tailor it for my own circumstance (the appropriate directory etc?)

The instructions continue:----[/FONT][/SIZE][/COLOR]

[SIZE="1"][COLOR="Sienna"](2)Load the driver module to kernel and start up nic
**./wlan0up**
(if "insmod: error inserting 'r8180.ko': -File exists." met,
[B]./wlan0rmv
./wlan0down
./wlan0up[/B]
should be OK.
)

[/COLOR][/SIZE]
[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]This seems clear but I am still unsure - again do I just enter ./wlan0rmv or must I modify it somehow?
The bit in brackets is possibly OK but I am not sure I understand it fully - I guess it is to do with what happens if certain error messages are received).

PLease excuse me labouring the points and demanding what might seem excessive handholding but it is the little missing bits that are important here.

There is more (another three or so sections) but if I can get through these first two bits, the rest might be self-explanatory (though I might have to come back!)

I do appreciate it if anyone takes the trouble to answer. Thank you
[/FONT][/SIZE][/COLOR]

---

### Post by solar george on 2007-02-17
> A purpose made Linux driver would be better I suppose 

I personally find that ndiswrapper works fine - if it works with your card you will have to do less work than to set it up using a source driver.

Install ndisgtk - it gives a graphical front end to ndiswrapper.

> where and when do I enter this command?

If you do decide to build the drivers your self then:

1. Put all of the files into the same directory - one that you will use just for this (e.g /home/yourname/driver)

2. open the terminal window and cd to that directory.
```
cd /home/yourname/driver
```

3. Enter
```
./makedrv
```
            and cross your fingers and hope.


Very good luck.

---

