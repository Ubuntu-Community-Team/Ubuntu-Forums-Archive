---
title: "Unable to download Broadcom STA Wireless Driver"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-01-20
Hi. First tuxGuitar sound and now this driver. 
The additional driver feature loads the drivers needed to be activated as usual. 
I downloaded and installed graphics driver, but can't get through downloading this wireless driver. 
Any help would be very generous of u guys....
when trying to download and activate the wireless driver, i get the following error: (please refer to the pic i attached):D

ThankYou
Regards,WinuxUser

---

### Post by snowpine on 2012-01-20
/var/log/jockey.log is a text file. You can open it with your favorite text editor and copy & paste the relevant info for us to see. :)

If you are a terminal nerd like me you can use:

```
tail /var/log/jockey.log
```

Common errors would be: not connected to internet (you'll need a temporary wired connection) or your hardware does not match the list. But those are just guesses until we read the log file. :)

---

### Post by nipunshakya on 2012-01-20
Sir, Currently im connected to internet via wired connection. Here's my jockey.log file attached.

---

### Post by nipunshakya on 2012-01-20
also, ```
lspci -vnn | grep 14e4
``` gave the following:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

---

### Post by snowpine on 2012-01-20
According to the [Broadcom page in the Ubuntu wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers"), if you are using 11.04 or newer, you can install the package **firmware-b43-lpphy-installer** for the BCM4312 LP-PHY chipset:

```
sudo apt-get install firmware-b43-lpphy-installer
```

I think STA was the correct driver for your card with 10.10 and older.

---

### Post by nipunshakya on 2012-01-20
yes indeed...it was the correct one. When i had freshly installed ubuntu 11.04 at its release, the download went without a pain. This error occurred after i downgraded from 11.10 to 11.04.. I'll give a try to your suggestion and keep you posted with results.

Thank You.
Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-20
Quick Update: i ran the code snowpine suggested, it went fine, extracted and everything, but still, not working man... :( my driver isn't working still....any  idea?

---

### Post by snowpine on 2012-01-20
First let's see if Linux recognizes your interface:

```
iwconfig
```

Do you see your wifi details (usually listed as wlan0)?

---

### Post by carl4926 on 2012-01-20
I have the same broadcom device and I needed the STA proprietary driver
11.10 works with b43
Kernel 3> has brought some great wireless improvements

Is your current install fully updated, including the kernel?

---

### Post by carl4926 on 2012-01-20
You could try manually
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by nipunshakya on 2012-01-21
> **snowpine said:**
> First let's see if Linux recognizes your interface:

```
iwconfig
```Do you see your wifi details (usually listed as wlan0)?
```
iwconfig
``` gave me the following :
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
Now i really don't know what all that means...getting this problem for the first time....:confused:

Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-21
> **carl4926 said:**
> I have the same broadcom device and I needed the STA proprietary driver
11.10 works with b43
Kernel 3> has brought some great wireless improvements

Is your current install fully updated, including the kernel?

There was no problem with my driver too back when i was in 11.10. The problem aroused when i downgraded to 11.04. However, The liveCD of the same ubuntu 11.04 from which i installed this OS would surf the internet using the wifi. 
I even tried to make another user account, tried from guest account, but all went in vain.:(

Btw, my current install is fully updated(did it las night only)
 However, doing ```
sudo apt-get upgrade && sudo apt-get update
```gave me the following:
```

winuxuser@MagicBox:~$ sudo apt-get upgrade && sudo apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Hit http://archive.canonical.com natty Release.gpg                            
Ign http://archive.ubuntu.com natty InRelease  
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Hit http://extras.ubuntu.com natty Release     
Hit http://archive.canonical.com natty Release 
Hit http://extras.ubuntu.com natty/main Sources                       
Hit http://archive.canonical.com natty/partner Sources
Ign http://archive.ubuntu.com natty-backports InRelease
Ign http://archive.ubuntu.com natty-proposed InRelease
Hit http://archive.ubuntu.com natty Release.gpg                      
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Hit http://archive.canonical.com natty/partner amd64 Packages        
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://archive.ubuntu.com natty-updates Release.gpg              
Hit http://archive.ubuntu.com natty-security Release.gpg             
Hit http://archive.ubuntu.com natty-backports Release.gpg            
Hit http://archive.ubuntu.com natty-proposed Release.gpg             
Hit http://archive.ubuntu.com natty Release                          
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://archive.ubuntu.com natty-security Release                           
Hit http://archive.ubuntu.com natty-backports Release                          
Hit http://archive.ubuntu.com natty-proposed Release                           
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/restricted Sources               
Hit http://archive.ubuntu.com natty/universe Sources                 
Hit http://archive.ubuntu.com natty/multiverse Sources               
Hit http://archive.ubuntu.com natty/main amd64 Packages              
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://archive.canonical.com natty/partner Translation-en_US     
Hit http://archive.ubuntu.com natty/restricted amd64 Packages
Hit http://archive.ubuntu.com natty/universe amd64 Packages          
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages        
Ign http://archive.ubuntu.com natty/main TranslationIndex            
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages                
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages          
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages            
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages          
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/main Sources                      
Hit http://archive.ubuntu.com natty-security/restricted Sources                
Hit http://archive.ubuntu.com natty-security/universe Sources                  
Hit http://archive.ubuntu.com natty-security/multiverse Sources                
Hit http://archive.ubuntu.com natty-security/main amd64 Packages               
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages         
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages           
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages         
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Hit http://archive.ubuntu.com natty-backports/restricted amd64 Packages        
Hit http://archive.ubuntu.com natty-backports/main amd64 Packages              
Hit http://archive.ubuntu.com natty-backports/multiverse amd64 Packages        
Hit http://archive.ubuntu.com natty-backports/universe amd64 Packages          
Ign http://archive.ubuntu.com natty-backports/main TranslationIndex            
Ign http://archive.ubuntu.com natty-backports/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/universe TranslationIndex        
Hit http://archive.ubuntu.com natty-proposed/restricted amd64 Packages         
Hit http://archive.ubuntu.com natty-proposed/main amd64 Packages               
Hit http://archive.ubuntu.com natty-proposed/multiverse amd64 Packages         
Hit http://archive.ubuntu.com natty-proposed/universe amd64 Packages           
Ign http://archive.ubuntu.com natty-proposed/main TranslationIndex             
Ign http://archive.ubuntu.com natty-proposed/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/universe TranslationIndex         
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://archive.ubuntu.com natty-backports/main Translation-en
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com natty-backports/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/main Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Fetched 72 B in 40s (2 B/s)
Reading package lists... Done
winuxuser@MagicBox:~$ 

```Can you tell me why there is ign before some of the sites? i guess that means it has ignored to fetch stuffs from there, is it? Why has this occurred?
Seeing this, do u think i should go and give a shot to try manual playing with the kernel stuff to embed my driver within it?? I am totally new to this driver related stuff so please don't mind me asking much questions. Thank You


Regards,WinuxUser

---

### Post by carl4926 on 2012-01-21
Have you checked with rfkill?

---

### Post by nipunshakya on 2012-01-21
> **carl4926 said:**
> Have you checked with rfkill?
```
rfkill list
```gave me the following:
```

winuxuser@MagicBox:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```and,```
sudo rfkill unblock wifi
```would give me nothing...when i hit enter, it just doesn't show any o/p

The whole thing is as:
```
winuxuser@MagicBox:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
winuxuser@MagicBox:~$ sudo rfkill unblock wifi
[sudo] password for winuxuser: 
winuxuser@MagicBox:~$ 

```

And, after i turn on my bluetooth, the ```
rfkill list
``` would output as:
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
winuxuser@MagicBox:~$ 

```

---

### Post by nipunshakya on 2012-01-21
One quick question please: While installing ubuntu, i didn't select "download updates while installing" and then just went on with an offline installation. Would that make any difference?

---

### Post by carl4926 on 2012-01-21
I can't begin to tell you the PITA I had with this.

Keep trying 
```
rfkill unblock all
```
Then turn the wireless off and shutdown

DO you have the option to boot windows?
Does the wireless work there
Because for me it would be down in windows too, until I managed to unblock it

Turn the wireless switch back on and power up

Keep trying this. Usually would take me about 4 times.

I put it down to b43
Don't even sniff at it until you are using kernel 3 >

---

### Post by carl4926 on 2012-01-21
> **WinuxUser said:**
> One quick question please: While installing ubuntu, i didn't select "download updates while installing" and then just went on with an offline installation. Would that make any difference?
In pre kernel 3 versions I turn wireless off on my broadcom machine
Do all the updates and install the proprietary driver.
Then reboot and turn wireless on

---

### Post by nipunshakya on 2012-01-21
> **carl4926 said:**
> In pre kernel 3 versions I turn wireless off on my broadcom machine
Do all the updates and install the proprietary driver.
Then reboot and turn wireless on

My current linux-header is 2.6.38. I remember that i have got only 2 updates of those headers. Back when i tried to repeatedly run the ```
rfkill unblock all
``` with my bluetooth once turned on and once turned off, it showed me a notification that i was trying to access a hardware which is proprietary and isn't supported by ubuntu and blah blah.... 

Now i assume that, when i had installed ubuntu 11.04, i should have enabled downloading updates when installing...Coz after that, i made upgrades to all the headers and all, but didn't take a look at my additional drivers stuff and didn't download them back. Now that my headers are all updated, this driver thing isn't getting inside my ubuntu to support wireless. This is my assumption.

---

### Post by nipunshakya on 2012-01-21
I tried a sequel of 12 boots consecutively, but still, no progress... :(

---

### Post by carl4926 on 2012-01-21
Was 11.10 a problem that you downgraded?

---

### Post by nipunshakya on 2012-01-21
oh yes...the startup time was not certain...sometimes 3 seconds to boot, and sometimes more than 4 minutes..... and most off all, i wanted to make a fresh installation of my system as my other OS(win 7) was in bad condition too. So, i did a fresh installation :)

---

### Post by snowpine on 2012-01-21
Your card is being recognized (it shows up as wlan0) so let's see which modules are in use:

```
lsmod | grep b43
lsmod | grep wl
```

---

### Post by nipunshakya on 2012-01-21
```

winuxuser@MagicBox:~$ lsmod | grep b43
b43                   318638  0 
mac80211              294370  1 b43
cfg80211              178528  2 b43,mac80211
ssb                    51945  1 b43
winuxuser@MagicBox:~$ lsmod | grep wl
winuxuser@MagicBox:~$ 

```

---

### Post by snowpine on 2012-01-21
That looks identical to what I see on my machine (and it works).

However, I am not an Ubuntu user, and it seems like there are frustrating differences in Broadcom support between the different releases, so maybe I am not in a position to say which is better for 11.04 specifically, b43 or wl (sorry). :(

---

### Post by nipunshakya on 2012-01-21
New update: I removed the additional driver thing from my machine. Now, the notification area where all networks are shown now shows me "wireless is disabled by hardware switch" in an uncheckable form. I switched the wi-fi switch from my keyboard, then notification area says "device not ready" in similar form. It stays the same for some time and again gives the previous message. I don't know why is this driver playing with me for so long now..... :(

---

### Post by carl4926 on 2012-01-21
> **WinuxUser said:**
> ```

winuxuser@MagicBox:~$ lsmod | grep b43
b43                   318638  0 
mac80211              294370  1 b43
cfg80211              178528  2 b43,mac80211
ssb                    51945  1 b43
winuxuser@MagicBox:~$ lsmod | grep wl
winuxuser@MagicBox:~$ 

```

b43 will not work for you until you are on kernel 3>

---

### Post by nipunshakya on 2012-01-21
> **carl4926 said:**
> b43 will not work for you until you are on kernel 3>
u mean i need to upgrade to 11.10 for that? or will ubuntu 11.04 provide the upgrade? kernel 3+ released 10 days ago...can't i have that on this very system? I digged [here]("http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/")
but don't know how much i can rely on it....Thanks.

Regards,WinuxUser
[]("http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/")

---

### Post by carl4926 on 2012-01-22
I don't know how to advise you in Ubuntu on a kernel upgrade. I can tell you it is not a move you should take lightly. And if you use a proprietary video driver Eg: nvidia/ati, you should know how to install it manually.

If you want to go this route. I advise you start a new thread. Something like: 'How to upgrade my kernel to 3> and be safe/stable'.

I would expect there to be a ppa or repo to provide such
Ubuntu seems to right out there setting the lead as a distro (and we have such a possibility at openSUSE) so I'm sure Ubuntu will too.

---

### Post by nipunshakya on 2012-01-22
> **carl4926 said:**
> I don't know how to advise you in Ubuntu on a kernel upgrade. I can tell you it is not a move you should take lightly. And if you use a proprietary video driver Eg: nvidia/ati, you should know how to install it manually.


I don't want that hard way either coz im still at intermediate level of using the linux thing and i don't want to mess up so soon. I guess i will wait for some other suggestions rather than give a manual update to my kernel. Afterall, Linus is Linus. Lol.


Thank you.
Regards,WinuxUser

---

### Post by carl4926 on 2012-01-22
In the additional drivers section
Does it not offer the Proprietary broadcom driver?

---

### Post by carl4926 on 2012-01-22
> **carl4926 said:**
> In the additional drivers section
Does it not offer the Proprietary broadcom driver?
Duh !
Sorry
Post 1. I see the error.

You need to find a way around that, why it is happening....?

---

### Post by carl4926 on 2012-01-22
> **WinuxUser said:**
> Sir, Currently im connected to internet via wired connection. Here's my jockey.log file attached.

I'm not clever enough to understand this.
I'd go the bug report route, see what you get there...

---

### Post by nipunshakya on 2012-01-22
i was saying that i an using a ADSL wired-line right now as because my wireless is not working. 
Im on this same machine that has the issue of wi-fi connection and so using ADSL line to connect to the internet.

---

### Post by carl4926 on 2012-01-22
> **carl4926 said:**
> I'm not clever enough to understand this.
I'd go the bug report route, see what you get there...

I mean I can't understand the log file you posted
That you should do a bug report and see if the devs can assist

---

### Post by nipunshakya on 2012-01-22
Ahh, i think i will do that soon, though haven't done that till now....Thanks for your help.

---

### Post by carl4926 on 2012-01-22
Please try this

```
sudo apt-get install linux-headers-$(uname -r)
```

Now try installing the driver from the additional drivers

---

### Post by carl4926 on 2012-01-22
Check this bug report
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

### Post by nipunshakya on 2012-01-22
Is the above code to install new linux-header? i don't know about that command. So please explain about what exactly will that do, then i could proceed without hesitations.

Thank You.
Regards,WinuxUser

---

### Post by carl4926 on 2012-01-22
> **WinuxUser said:**
> Is the above code to install new linux-header? i don't know about that command. So please explain about what exactly will that do, then i could proceed without hesitations.

Thank You.
Regards,WinuxUser

Read the bug report

It is to install the headers, yes.
In the bug report, this move didn't help everyone. But users there were also installing the driver manually.
And some found the headers already in place.
Another user reports manually using synaptic to force a re-installation of header and broadcom packages.

If necessary, tag on to that bug report yourself.

So, try the code for the headers. You may already have them.

---

### Post by nipunshakya on 2012-01-22
> **carl4926 said:**
> Please try this

```
sudo apt-get install linux-headers-$(uname -r)
```Now try installing the driver from the additional drivers
```

winuxuser@MagicBox:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-13-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
winuxuser@MagicBox:~$ 

```

Now it says its newest. So maybe badluck for me that it doesn't support my wifi drivers...Sad linuxing.:(

---

### Post by carl4926 on 2012-01-22
Have you tried downloading and building yourself?
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Note the read me
> Building this driver requires that your machine have the proper tools, packages, header files and libraries to build a standard a kernel module.   This usually is done by installing the kernel developer or kernel source  package and varies from distro to distro. Consult the documentation for your specific OS.  If you cannot successfully build a module that comes with your distro's  kernel developer or kernel source package, you will not be able to build  this module either.  If you try to build this module but get an error message that looks like  this:  make: *** /lib/modules/"release"/build: No such file or directory. Stop.  Then you do not have the proper packages installed, since installing the  proper packages will create /lib/modules/"release"/build on your system.  On Fedora install 'kernel-devel' (Development Package for building kernel modules to match the kernel) from the Package Manager (System-> Administration-> Add/Remove Software).  On Ubuntu, you will need headers and tools.  Try these commands: # apt-get install build-essential linux-headers-generic # apt-get build-dep linux

---

### Post by nipunshakya on 2012-01-23
Looking at that read-me stuff, i wouldn't like to try that out manually. i think it'd be better for me to pick up something else and keep using Ethernet for some days. Thanks for your help though. I really appreciate that...:)

---

