---
title: "Toshiba Install NB505-N508 and L305-S5919"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by tlcstat on 2011-02-14
Greetings,
Just wanted to let everyone know that the Maverick 10.10 will install on these two computers with no problems. I did need to use this driver install code for the Netbook wifi, found elsewhere on this forum. This is for the Netbook Realtek Wifi 8176. 

> sudo add-apt-repository ppa:lexical/hwe-wireless
apt-get update
apt-get install rtl8192ce-dkms
For some reason Toshiba doesn't tell you the card brand in their specs but I downloaded their drivers from their site and got the wifi card info from their inf files. 

I wanted to put the Unity Desktop on my 15" L305 Laptop so that I would know how to use it when my Wife's new Netbook arrived and I did that install. I liked Unity until I found its limitations, such as "no Wine launcher", freeze ups, misbehaving file and folder display etc. Not specifically problems for me, but not good for my wife. 
Switching to the Gnome Desktop was easy though. System/Admin/Login Screen and select the Gnome Desktop and restart. 

Gnome on the 10.10 Ubuntu is a different story. It is extremely smooth and fast even on the Netbook with only 1Gig of RAM. In fact I will go so far as to say that this is the best operating system that I have used in the 20+ years that I have been using computers. 

I don't do upgrades since I don't like the potential for migrating problems to the new system. However transferring Email and other settings was not a problem. I did have to reinstall my Wine programs instead of just copying over the directory. 

At first I thought that the Netbook was using a bit more battery than expected but the time estimation kept increasing as time went on. I think Lithium Ion batteries gain strength with time when they are new. Right now it is giving about seven hours on a charge estimated. 
Regarding new features in Ubuntu with 10.10, I just installed this weekend so I don't really know, but I do know this is the best so far. Big thumbs up from me and wife.
Have fun and do a clean install. 
tlcstat

---

### Post by mörgæs on 2011-02-15
Thanks. Do you feel like adding your findings in [http://www.linuxhcl.com/](http://www.linuxhcl.com/) ? 

Agreeing on the clean install. If only more people would do that...

---

### Post by oceanfirehawk on 2011-04-14
Hello,

I have the Toshiba NB505-N508 with 10.10 netbook ubuntu. can you please walk me through the wifi driver process?

---

### Post by docfreed on 2011-04-16
> **tlcstat said:**
> Greetings,
Just wanted to let everyone know that the Maverick 10.10 will install on these two computers with no problems.  I did need to use this driver install code for the Netbook wifi, found elsewhere on this forum. This is for the Netbook Realtek Wifi 8176. 

For some reason Toshiba doesn't tell you the card brand in their specs  but I downloaded their drivers from their site and got the wifi card  info from their inf files. 

I wanted to put the Unity Desktop on my 15" L305 Laptop so that I would know how to use it when my Wife's new Netbook arrived and I did that install.  I liked Unity until I found its limitations, such as "no Wine launcher", freeze ups, misbehaving file and folder display etc. Not specifically problems for me, but not good for my wife. 
Switching to the Gnome Desktop was easy though. System/Admin/Login Screen and select the Gnome Desktop and restart. 

Gnome on the 10.10 Ubuntu is a different story. It is extremely smooth and fast even on the Netbook with only 1Gig of RAM. In fact I will go so far as to say that this is the best operating system that I have used in the 20+ years that I have been using computers. 

I don't do upgrades since I don't like the potential for migrating problems to the new system. However transferring Email and other settings was not a problem. I did have to reinstall my Wine programs instead of just copying over the directory. 

At first I thought that the Netbook was using a bit more battery than expected but the time estimation kept increasing as  time went on.  I think Lithium Ion batteries gain strength with time when they are new. Right now it is giving about seven hours on a charge estimated. 
Regarding new features in Ubuntu with 10.10, I just installed this weekend so I don't really know, but I do know this is the best so far. Big thumbs up from me and wife.
Have fun and do a clean install. 
tlcstat
I have installed the RTL8192CE-dkms but I but my NB505 still does not see any wireless networks.  Could you also walk me through how you got the WiFi working.  I have actually installed the lexical package, Ubuntu tells me that the driver is installed, etc...  

I am dual booting w/Win 7 and have no problems with WiFi on the Windows 7 side

TIA

---

### Post by tlcstat on 2011-04-16
Greetings,
If you are showing the driver installed. You can open your network manager and make sure that WIFI is enabled and the card should respond to a FN F8 to toggle the card on and off. It is quite possible that the card is turned off. I take it that you have an active router for testing this system. 
tlcstat

---

### Post by docfreed on 2011-04-16
> **tlcstat said:**
> Greetings,
If you are showing the driver installed. You can open your network manager and make sure that WIFI is enabled and the card should respond to a FN F8 to toggle the card on and off. It is quite possible that the card is turned off. I take it that you have an active router for testing this system. 
tlcstat
Thanks for the quick reply - WiFi is enabled in Win7 and I can connect to the web - does that mean it would automatically be enabled in Ubuntu?  If so, then I will try the FN-F8 and report back. And, yes I have an active router and all my other machines are working well.

As an aside, I have a Toshiba L305 Satellite dual booting between Vista and Ubuntu and Ubuntu found its NIC perfectly and WiFi worked on startup with no mods.

---

### Post by tlcstat on 2011-04-16
Greetings,
If you are showing the driver installed. You can open your network manager and make sure that WIFI is enabled and the card should respond to a FN F8 to toggle the card on and off. It is quite possible that the card is turned off. I take it that you have an active router for testing this system. 
tlcstat

Greetings,
One more thing. When the card is active you should have a continuous orange light on the right edge of your computer. It doesn't blink with activity as would be expected. Also, You need to "right" click on the network icon in your top panel and make sure there is a check next to Wireless. I checked the net for the function key that toggles wireless and there seems to be no standard for the wifi toggle. It depends on what keyboard is installed and how it gets mapped. This goes beyond my expertise. 

tlcstat

---

### Post by docfreed on 2011-04-16
Thanks - yes the orange light is always steady - I may just wind up returning the netbook and getting an Asus if this doesn't work.

---

### Post by tlcstat on 2011-04-16
Greetings,
What is the state of the wireless in the network manager? If it is checked you can open the terminal and type "ifconfig" without the quotes. It should show your wifi cards mac number and identify it as WLAN0 which would be usual but could be something else. 
tlcstat

---

### Post by docfreed on 2011-04-16
> **tlcstat said:**
> Greetings,
What is the state of the wireless in the network manager? If it is checked you can open the terminal and type "ifconfig" without the quotes. It should show your wifi cards mac number and identify it as WLAN0 which would be usual but could be something else. 
tlcstat
So: (sending from the Win7 side of the netbook)
a) thanks for sticking with me on this - here is where I am:

1.  I can get a wired connection to my router - no sweat
2. downloaded and installed Realtek 8192ce driver - Ubuntu confirms this and says it's active
3. orange light is always on and steady
4. network connections is checked
5. nothing on WiFi - doesn't even see any networks and network tools won't open

I'm going to Win7 device manager to see if this is really a Realtek Card - could be it's Atheros in which case what would I do?

EDIT: It's a realtek and Win7 said the latest driver is installed

---

### Post by docfreed on 2011-04-16
[SIZE=3]OH FRABJOUS JOY - it now works:[/SIZE]

[SIZE=4]In Win 7 device manager, it showed that the 801.x was disabled on the card so I enabled it AND it also showed that power saving was enabled!!  I disabled power saving, rebooted and lo and behold I now have WiFi

THANKS A MILLION FOR YOUR HELP
[/SIZE]

---

### Post by tlcstat on 2011-04-16
Greetings,
I would be interested in a cut and paste of the results of two commands executed in the Gnome Terminal.

ifconfig
iwconfig

The terminal can be found in applications/accessaries/Terminal.

I suspect that you have the realtek card. The best way that I know to find out is to give a lspci command in the terminal and see what it lists for wireless ethernet. 
tlcstat

Greetings,
Congratulations! Just remember that in Linux in general the terminal is going to be your first destination for trouble shooting. To identify devices you will use lsusb and lspci, to check your network you will use ifconfig and iwconfig. This is no big deal for us old guy Windows users since we started out at the command prompt anyway, but some of you younger guys may not have had the joy of experiencing that. 
Welcome to Linux, the fun begins.
tlcstat

Greetings,
> [SIZE=4]it showed that the 801.x was disabled on the card so I enabled it AND it also showed that power saving was enabled[/SIZE]

Thanks for your help!, this may explain some of the quirky results different users have had with that card. Some users have had low transmit power with that card and your post explains the possible reason and solution to that. 
tlcstat

---

### Post by docfreed on 2011-04-16
[SIZE=2]Your command is my wish!!!


djf@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:7d:a7:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9500 (9.5 KB)  TX bytes:9500 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 88:25:2c:ca:b2:df  
          inet addr:10.0.0.20  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8a25:2cff:feca:b2df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4523812 (4.5 MB)  TX bytes:574953 (574.9 KB)
          Interrupt:17 Memory:ffffc900001f8000-ffffc900001f8100 


  Here's iwconfig:

wlan0     802.11bgn  ESSID:"dolphinlane"  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.437 GHz  Access Point: C0:3F:0E:69:72:A0   
          Bit Rate=43.5 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=79/100  Signal level=0 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/SIZE]

[SIZE=2]What do these results indicate to you[/SIZE]?

---

### Post by tlcstat on 2011-04-16
Greetings,
The iwconfig certainly indicates that you have a working card. Do you have internet access?
tlcstat

---

### Post by docfreed on 2011-04-16
> **tlcstat said:**
> Greetings,
The iwconfig certainly indicates that you have a working card. Do you have internet access?
tlcstat
Absolutely - I have INTERNET access!  Now, has anything that I discovered of use t - o others - the Toshiba NB505 is a great netbook and now on sale at Best Buy and Amazon for $279 is a great value and now that I can dual boot it even more so.

---

### Post by mörgæs on 2011-04-17
Good that you guys got it solved. If you mark the thread 'solved', more people will find it.

Would also be good if you could add a very brief description of the process in this thread:
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by docfreed on 2011-04-17
> **mörgæs said:**
> Good that you guys got it solved. If you mark the thread 'solved', more people will find it.

Would also be good if you could add a very brief description of the process in this thread:
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)
Will do.  How do I mark the thread as "solved"

---

### Post by tlcstat on 2011-04-17
Greetings,
> Good that you guys got it solved. If you mark the thread 'solved', more people will find it.

Would also be good if you could add a very brief description of the process in this thread:
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

Thread has been marked solved. I will try to write a description that attempts to solve some of the problems with this driver. I will also post the Laptop on the link given.
Thanks
tlcstat

Realtek 8192CE driver install procedure. Procedure may be incomplete. This post is specifically for the NB505-N508 Toshiba Netbook but should work on other models using the same card. 

You should know the MAC id number of your device. This will usually be on a tag on the bottom of the computer or with your purchase documentation. Knowing your device mac id is always helpful for diagnostic purposes.

You should have an active router in the area during the installation. You don't need to be able to access it, only to see it. 

Install driver. Following commands to be run in terminal.....

sudo add-apt-repository ppa:lexical/hwe-wireless
apt-get update
apt-get install rtl8192ce-dkms 

If the driver install completes ....reboot computer.

After reboot.

If the card is active you should have a solid orange light on your Wifi activity light. You will not have a blinking for activity or none for off light. It will be a continuous light if the card is active.

Open the network applet in the top panel bar. Can you see a wireless router listed. If yes, you are probably done. 

If not!
In terminal type iwconfig
You should be able to see your card as active (usually wlan0). If your wifi is identified as anything else (such as wlan1..2 make a notation for future reference.

"Right" click on your network applet in the top panel bar. There should be a check mark by "wireless" if not then put it there. 

Open the network applet in normal mode and assure that you can see your router. 
If you can see your router you should be done.

If not!
Do you have a duel boot with Windows?
If yes... Boot Windows, go to your wireless device properties in the Device Manager, Turn "Power management" off and turn 802.x on. 
Reboot into Ubuntu and you should now have a working card. 

If you don't dual boot Windows.
You can turn power management off with the terminal command 'sudo iwconfig wlan0 power off" The "wlan0" should be replaced with your own wlan designation.

I'm not sure how to turn on 802.x with the linux driver. You can try "sudo iwconfig wlan0 modu auto" if that doesn't work, post the results since I don't have a machine to duplicate the problem. 

For troubleshooting requests you should be able to post the results of the following terminal commands. You can cut and paste them into a text file or past them directly into your post.

lsmod
lspci
iwconfig
ifconfig
iwlist is also a command that you may be asked to use. The instructions for the usage of any of these commands can be found by typing in a terminal "man" plus the command or the command plus "--help" or "--longhelp"

With out posting the information from those commands you are wasting a lot of time. 

Please be advised that I have extensive career based Windows experience but I am just a Linux noobie myself. I will try to give followup support on this driver if possible. 

tlcstat

---

### Post by jrbenito on 2011-07-20
Hi,

First of all thanks for posting this information. 

I just want to inform that I have downloaded and installed the Ubuntu 11.04 Natty Narwhal (through USB stick) with success in the Toshiba NB505-N508. The wireless is a Realtek also but it worked in Natty just out of the box.

So far no issues found. I bring new information as soon as I get it.

Regards,
Benito

---

### Post by natkill on 2011-10-01
Is there an issue with putting 11.04 on the NB505? I installed natty on my new netbook, and it keeps crashing about a minute after booting. It will go through the installation stuff, then show the welcome to Natty Narwhal window, then crash.

---

### Post by kuric on 2011-11-04
Toshiba NB500-108 and Ubuntu 11.10 here. There was no need to install rlt8192ce driver, wifi was automatically detected.

However... I've noticed that the signal strength of the wireless networking card is lower than in windows. 

Eg., I often travel to places where I have access to public unprotected networks ( [http://en.wikipedia.org/wiki/FON](http://en.wikipedia.org/wiki/FON) ) with windows, while ubuntu tries to reach them but the connection always fails in the end.

---

