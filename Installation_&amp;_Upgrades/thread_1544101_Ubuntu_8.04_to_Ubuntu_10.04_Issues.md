---
title: "Ubuntu 8.04 to Ubuntu 10.04 Issues"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by carrickfergus on 2010-08-02
Hey Folks,

A while ago I posted that I was planning on installing Windows 7. Well, I ultimately decided against the idea because I decided that Ubuntu 10 offered all of the "design" features I was looking for and probably is better off in the long run. So after discovering that it worked with my webcam (seriously had me overjoyed that I could use it again) I installed it wiping out the older version of Ubuntu. Out with the old, in with the new. However, a concern still remains and that is what has brought me here...

In Ubuntu 8.04, the initial installation did not recognize my Broadcom modem but after updates, I was able to install the driver through a wired connection and it worked perfectly. I was happy and thought 10.04 would work the same way.

It kinda did. Allow me to explain. I updated the system and installed the driver like I did in 8.04 it didn't appear to connect any other way except through a wired connection. I thought if I refreshed it then maybe it would do something and I would be able to choose from one of our 3 house networks (yes 3! :p). I did this by turning off the wireless network and then turning it back on. Occasionally I have to do it with my desktop once in a rare while.

Big oops apparently!

Now I can't turn the wireless network back on. It's been grayed out and I cannot select it. I've tried restarting but to no avail. Any idea what I screwed up on? It still recognizes the drive, but it's not using it for some reason...

I just installed python and I'm going to see if that works after a reboot. I'll post whether it did or didn't work momentarily but I wanted to start this just in case it didn't - or if it did then other users could try it.

---

### Post by carrickfergus on 2010-08-02
So... um... yeah... nothing; won't even let me view the wireless settings... let alone enable. :(

I have faith in Ubuntu, though. I'm sure there is an answer out there somewhere. Help?

---

### Post by robsoles on 2010-08-02
I dealt with a laptop a while ago that made it look like it wasn't possible to re-enable the wireless adapter once you disabled it but much closer inspection of the keyboard found the key combination to press (something like [Fn]+[F3]) and the rotten thing turned back just as it ought - the owner had reinstalled Ubuntu three times, each time he screwed up and disabled the wifi!

Of course it's even nicer when Laptops have a toggle switch as opposed to key combo or other button - only a couple with actual toggle switches have strayed past my nose.

Please post back much much more detail on the Laptop and Wireless Adapter if nothing above helps in the slightest - Is it an inbuilt WiFi device? What kind of button/switch on Lappie if so? What manufacturer, make and model of Laptop is that? What m, m & m Wireless Adapter?

---

### Post by carrickfergus on 2010-08-02
> **robsoles said:**
> I dealt with a laptop a while ago that made it look like it wasn't possible to re-enable the wireless adapter once you disabled it but much closer inspection of the keyboard found the key combination to press (something like [Fn]+[F3]) and the rotten thing turned back just as it ought - the owner had reinstalled Ubuntu three times, each time he screwed up and disabled the wifi!

Of course it's even nicer when Laptops have a toggle switch as opposed  to key combo or other button - only a couple with actual toggle switches  have strayed past my nose.

Well these Fn+ keys are very interesting, but they don't appear to fix the problem. I can make my computer blink and go to sleep, but wireless still appears to be disabled and unable to re-enable.

> **robsoles said:**
> Please post back much much more detail on the Laptop and Wireless Adapter if nothing above helps in the slightest - Is it an inbuilt WiFi device? What kind of button/switch on Lappie if so? What manufacturer, make and model of Laptop is that? What m, m & m Wireless Adapter?

I just ran a system check and it detected the following:
Broadcom Corp. BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

I could run the system check again. The output was just so long and I wasn't exactly sure what I was looking for...

I also tried installing rfkill through the Ubuntu Software Center. By running it in the terminal I got the following:

> rcarrickfergus@MyLaptop:~$ rfkill help
Usage:    rfkill [options] command
Options:
    --version    show version (0.3)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps
carrickfergus@MyLaptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I'm a bit of a newbie, so I'm still trying to find out how I can get it off of the "hard blocked" list.

---

### Post by carrickfergus on 2010-08-02
I must be stupid. My computer and I have been having the following conversation:

> carrickfergus@MyLaptop:~$ unblock wireless LAN
unblock: command not found
carrickfergus@MyLaptop:~$ rfkill unblock Wireless LAN
Bogus unblock argument 'Wireless'.
carrickfergus@MyLaptop:~$ rfkill unblock 0
carrickfergus@MyLaptop:~$ rfkill unblockhead my Wireless Network
Usage:    rfkill [options] command
Options:
    --version    show version (0.3)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps
carrickfergus@MyLaptop:~$ rfkill unblock yes
Bogus unblock argument 'yes'.
carrickfergus@MyLaptop:~$ rfkill unblock phy0
Bogus unblock argument 'phy0'.
carrickfergus@MyLaptop:~$ rfkill unblock wireless
Bogus unblock argument 'wireless'.
carrickfergus@MyLaptop:~$ rfkill unblock 1
carrickfergus@MyLaptop:~$ rfkill unblock list
Bogus unblock argument 'list'.
carrickfergus@MyLaptop:~$ rfkill unblock <idx> all
bash: idx: No such file or directory
carrickfergus@MyLaptop:~$ rfkill unblock <all>
bash: syntax error near unexpected token `newline'
carrickfergus@MyLaptop:~$ rfkill unblock all
carrickfergus@MyLaptop:~$Nothing appears to have changed except that my computer thinks I've been throwing bogus arguments at it. Haha! :D

EDIT: I just used the command "rfkill event 1" and it killed my prompt.

---

### Post by robsoles on 2010-08-02
> **carrickfergus said:**
> ...

EDIT: I just used the command "rfkill event 1" and it killed my prompt.

Not sure it should have but very funny none the less.

What about
```
rfkill unblock wlan0
```

Unlikely I expect as what you want is 'enable' which doesn't appear to be provided by rfkill.

---

### Post by carrickfergus on 2010-08-02
> **robsoles said:**
> Not sure it should have but very funny none the less.

What about
```
rfkill unblock wlan0
```Unlikely I expect as what you want is 'enable' which doesn't appear to be provided by rfkill.
It says your argument was bogus too. Haha! :p

```
carrickfergus@MyLaptop:~$ rfkill unblock wlan0
Bogus unblock argument 'wlan0'.
```

Other ideas?

I'm going to check and see if it installed the wrong driver in the meantime. I let you all know if this solves the issue.

---

### Post by carrickfergus on 2010-08-02
Just found this: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

Thought I might follow it's instructions.

1. I am trying to get on a Wireless Network.

2. I am using Broadcom Corp. BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. It came with the Laptop and worked fine with Ubuntu 8.04.

3. My ISP is Qwest and I live in the States.

4. Using Ubuntu 10.04 Netbook Edition
I downloaded and burned the ISO file to a DVD from here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
5. I can get online using a wired connection.

6. I am getting online right now through my desktop computer which I will also soon be formatting with Ubuntu 10.04 Desktop Edition. It seems to work fine with my wireless modem on my desktop when I ran the demo version.

7. Output is as follows:
```
carrickfergus@MyLaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:35:33:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3281314 (3.2 MB)  TX bytes:459968 (459.9 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1356249 (1.3 MB)  TX bytes:1356249 (1.3 MB)

carrickfergus@MyLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
carrickfergus@MyLaptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
carrickfergus@MyLaptop:~$ ping -c 3 208.67.219.101
connect: Network is unreachable
carrickfergus@MyLaptop:~$ ping -c 3 www.opendns.com
ping: unknown host www.opendns.com

```It should be noted that at this time my laptop's wired connection is disconnected as I have it next to my desktop computer.

8. The wireless network setup is not pertinent since the issue is with my laptop and the inability to enable the wireless driver.

9. I do not have a dual boot system and I haven't for some time (Hallelujah!).

Hopefully this will maybe help a little more. I'm also including pictures so you can *really *understand what's going on... hopefully. :KS

Left click:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs224.snc4/38517_10150243222215347_786230346_14143850_7005003_n.jpg[/IMG]

Right click:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs271.snc4/39880_10150243222345347_786230346_14143852_6662325_n.jpg[/IMG]

I hope you can see and understand the dilemma.

EDIT: Additionally, the correct driver does appear to be installed. I imagine it says that no proprietary drivers are in use because the wireless is disabled...
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs115.ash2/39086_10150243227615347_786230346_14144011_1753614_n.jpg[/IMG]

---

### Post by robsoles on 2010-08-02
try```
iwconfig wlan0 txpower auto
```

Probably won't but if the physical button combo or switch isn't working we gotta try something - if we keep coming up with something to try and trying them eventually we should hit the problem and make it go away.

---

### Post by carrickfergus on 2010-08-02
> **robsoles said:**
> try```
iwconfig wlan0 txpower auto
```Probably won't but if the physical button combo or switch isn't working we gotta try something - if we keep coming up with something to try and trying them eventually we should hit the problem and make it go away.
I received the following response:
```
Error for wireless request "Set Tx Power" (8B26):
     Set failed on device wlan0 ; Operation not permitted.
```

I also tried reinstalling Ubuntu but to no avail. I didn't even touch the checkmark this time and I also consciously avoided the Fn and F1-12 buttons too just to be safe.

When I re-installed Ubuntu, after upgrading, I re-installed the hardware. It said that the "Device is not ready" so I decided to reboot rather than play around with it to see if that would set things in order.

I was stunned. :-?

Not only is it still not connecting but it reverted back to the "Wireless Connection" option being grayed out. Something is definitely askew here... :-s

---

### Post by robsoles on 2010-08-02
I can't tell from your description if this is an inbuilt or if it is pcmcia addition. Please specify.

---

### Post by carrickfergus on 2010-08-02
> **robsoles said:**
> I can't tell from your description if this is an inbuilt or if it is pcmcia addition. Please specify.
It's inbuilt.

---

### Post by carrickfergus on 2010-08-02
It's an Acer Aspire 3000. This is what I'm looking at:
[IMG]http://www.pcpartners.uk.com/lapimages/aceraspire3000.jpg[/IMG]

---

### Post by carrickfergus on 2010-08-03
> **robsoles said:**
> I can't tell from your description if this is an inbuilt or if it is pcmcia addition. Please specify.
Hey, Thanks for all of the help. I just finished fixing it.

Apparently I had to:
1. Insert the Installation Disc
2. Open the Synaptic Package Manager
3. Click on Settings > Repositories
4. Had to click the CD/DVD Rom Installation Option
5. Closed out of Synaptic Package Manager
6. Opened Hardware Drivers
7. Enabled "Modem" (a new option that was not previously there)
8. Closed out of the Hardware Drivers
9. Go back into the Synaptic Package Manager and remove the checkmark to install from the CD/DVD
10. Restarted my computer
11. Upon restarting, I was able to press one of the LED light buttons that I had previously been pressing but to no avail. It is clear that the Modem installation was the problem.

I must admit, my faith in the Ubuntu 10.04 Netbook OS is a quite shaken since I would have thought this would have been something that would be mentioned during the installation process or much easier to find rather than taking a day and a half to find through Google (one of the reasons I have reposted what I've done). But, I'm glad it's working now as it should.

I can only hope that others won't have to spend so long going through the same trouble I did. ;)

---

