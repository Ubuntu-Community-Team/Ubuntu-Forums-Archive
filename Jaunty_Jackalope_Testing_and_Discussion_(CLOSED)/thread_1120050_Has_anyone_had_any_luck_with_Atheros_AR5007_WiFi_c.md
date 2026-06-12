---
title: "Has anyone had any luck with Atheros AR5007 WiFi chipsets?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-04-08
Hello

It seems that somewhere between the time Intrepid was released and jaunty, the kernel, or something else updated that broke support for Atheros AR5007 chipset wifi cards.

I usually just get it working by compiling a 'special' branch of madwifi that supposedly has some weird version of HAL:

[http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6/](http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6/)

But when i was using jaunty, ath5k worked, although the speed was terrible...only 1mbps compared to the 54 i get in windows and using the compiled drivers above

Then, after some update, ath5k no longer worked, so i tried compiling the above drivers, and even those don't work

I tried installing arch and using those drivers as well (which worked less then a month ago) and now it doesn't work there either

Linux is useless to me if i cannot get wireless working, has anyone had any luck getting their AR5007 chipsets working recently?

---

### Post by mbott on 2009-04-08
> **Polygon said:**
> Hello

It seems that somewhere between the time Intrepid was released and jaunty, the kernel, or something else updated that broke support for Atheros AR5007 chipset wifi cards.

I usually just get it working by compiling a 'special' branch of madwifi that supposedly has some weird version of HAL:

[http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6/](http://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6/)

**But when i was using jaunty, ath5k worked, although the speed was terrible...only 1mbps compared to the 54 i get in windows and using the compiled drivers above**

<snip>



The **lack of speed** issue is the same issue I'm having, but I also experienced it with Mandriva and openSUSE this weekend before I installed 9.04.  I saw the same numbers that you indicate in your post.  Seemed to improve somewhat when I turned off the protected mode of my Belkin wireless router.

-- 
Mike

---

### Post by mykrob on 2009-04-08
works fine for me using the madwifi-hal driver.

Be sure to blacklist the ath5k driver, it is probably being loaded as well and the two drivers are conflicting.

---

### Post by mbott on 2009-04-08
The only driver I've been able to use with 9.04 is the ath5k driver.  Activating the alternate madwifi driver and I have no wireless at all.

-- 
Mike

---

### Post by Polygon on 2009-04-08
> **mykrob said:**
> works fine for me using the madwifi-hal driver.

Be sure to blacklist the ath5k driver, it is probably being loaded as well and the two drivers are conflicting.

i am blacklisting ath5k, and it seems to only not work  with WPA2 enterprise networks...which is the same problem ath5k was having....as both ath5k and ath_hal work fine on my wpa2 personal network...

---

### Post by Reiger on 2009-04-08
Funny I noticed a drop in speed as well: with the iwlagn driver I only get 1-24Mb/s and that used to be 36-45Mb/s (armoured concrete floors you see..)

---

### Post by mbott on 2009-04-09
> **Reiger said:**
> Funny I noticed a drop in speed as well: with the iwlagn driver I only get 1-24Mb/s and that used to be 36-45Mb/s (armoured concrete floors you see..)

I can be in the same room as the router with 96% signal strength and still only manage 1 to 2 Mb/s.  :(

-- 
Mike

---

### Post by Polygon on 2009-04-09
> **mbott said:**
> I can be in the same room as the router with 96% signal strength and still only manage 1 to 2 Mb/s.  :(

-- 
Mike

yeah same with me.

I'm planning on submitting a kernel.org bug report (as they want you submit reports there now instead of on madwifi-project.org now) so i will post it here when i do it

---

### Post by mykrob on 2009-04-09
ummm. did you guys use the madwifi-hal driver?

I know this bug exists in the built-in driver, but it seems that has always been the case. While I would love to see the built in one work, I am not a coder, and have opted to just install and use what works..

Happily using madwifi-hal and downloading at very comfortable speeds

```

myk@mobileOne:~$ sudo lshw -C network
[sudo] password for myk: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:7d:38:8e:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.131 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


myk@mobileOne:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"kingdomcomputer"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:A0:85:DF   
          Bit Rate:18 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/70  Signal level=-22 dBm  Noise level=-95 dBm
          Rx invalid nwid:5403  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by Polygon on 2009-04-09
both ath_hal (the real name of that driver) and ath5k exhibit the same problems...slow download speeds if you can even connect, and with some encryption types (like WPA2 Enterprise) it refuses to connect at all.

---

### Post by mykrob on 2009-04-09
Madwifi-hal uses the driver ath_pci. Am I the only one having good luck with this?

---

### Post by Polygon on 2009-04-09
before, ath5k used to not work at all with my card, only ath_hal or madwifi-hal or whatever its called

now ath5k does work with my card, but both ath5k and madwifi-hal now are super slow and don't connect with wpa2 enterprise...so i would have to say yes  you are the only one having good luck with it =/

---

### Post by paradigm2 on 2009-04-09
> **Polygon said:**
> before, ath5k used to not work at all with my card, only ath_hal or madwifi-hal or whatever its called

now ath5k does work with my card, but both ath5k and madwifi-hal now are super slow and don't connect with wpa2 enterprise...so i would have to say yes  you are the only one having good luck with it =/

I use the Ath5k driver with WPA2 Personal and it does work (though you use enterprise, a different beast).  Although I notice that the connection is about 9Mbps max and the router is only a room away (signal strength as measured in the connection manager is about 70%).

Before reading this I just assumed that there was some power saving feature in use that I have yet to disable.  I thought this because my max internet connection is no more than 6Mbps.

If a bug report is filed I too will post over there about my experience.

---

### Post by Polygon on 2009-04-09
i will do it this weekend. before i post one on kernel.org, are we positive that this is not a network manager bug? i cannot for the life of me get wpa-supplicant working, but can someone try getting a wireless connection with ifconfig and wpasupplicant and see if this slow speed issue is not related to network manager?

and i guess i will be reporting two bugs: ath5k has slow speeds on ar5007 chipsets, and ath5k does not connect to WPA2 enterprise networks on ar5007 chipsets

---

### Post by paradigm2 on 2009-04-09
> **Polygon said:**
> i will do it this weekend. before i post one on kernel.org, are we positive that this is not a network manager bug? i cannot for the life of me get wpa-supplicant working, but can someone try getting a wireless connection with ifconfig and wpasupplicant and see if this slow speed issue is not related to network manager?

and i guess i will be reporting two bugs: ath5k has slow speeds on ar5007 chipsets, and ath5k does not connect to WPA2 enterprise networks on ar5007 chipsets

If you want I will search for the slow speed bug first and then file that one since I am personally having that issue.  I'm hesitant to change my working config right now though.

---

### Post by mbott on 2009-04-10
> **Polygon said:**
> i will do it this weekend. before i post one on kernel.org, are we positive that this is not a network manager bug? 

I think the approach is correct as I saw the same slow networking under openSUSE and Mandriva this last weekend before I installed the beta.

-- 
Mike

---

### Post by krislogan on 2009-04-10
First time poster and new to linux so please be nice :)

With the ath5k driver I am not seeing my broadcast network so I have to connect to a "hidden" network every time I turn the machine on. If I use the madwifi driver I have no wireless at all, almost like its been turned off.  Any ideas?

---

### Post by mbott on 2009-04-18
> **paradigm2 said:**
> If you want I will search for the slow speed bug first and then file that one since I am personally having that issue.  I'm hesitant to change my working config right now though.

I've been able to get my best speed after issuing the following:

```
sudo iwconfig wlan0 rate 12M
```

Sometimes a rate of 24M works too, but anything over that and all traffic over the network stops.  :(

-- 
Mike

---

### Post by Polygon on 2009-04-18
point is, my card is capable of doing 54Mbps...not 12.

and also, supposedly there is a new version of network manager out, so i will try to see if that fixes anything, and then in my copious free time (lol) , i'll file a bug report

---

### Post by mbott on 2009-04-18
> **Polygon said:**
> point is, my card is capable of doing 54Mbps...not 12.


So was mine, under 8.04. :)

-- 
Mike

---

### Post by Narvinye on 2009-04-18
Hi!  Not sure if this helps but I have an Atheros card and I have used both ndswrapper and madwifi to fix it before.  I came across another fix a while back that allowed me to use the restricted driver on a fresh install and all I had to do was run the make and install.

Recently I installed the 9.4 beta and I have just finished burning the RC to test it.  (Note I didnt upgrade but did a full install - home on separate partition) What I first noticed on the beta install was my that wireless worked natively.  I was stoked since this has never happened before.  Tested on a my brothers Gateway that had wireless issues on 8.04 and same thing. Wireless out of the box. 

```
lspci -v
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k
```
```

sudo lshw -C network

*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wmaster0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.199 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

```

lsmod
cfg80211               38032  2 ath5k,mac80211
mac80211              217208  1 ath5k

```

So my wireless is working on the 9.04 beta with a clean install.  I'm wondering if this driver is what is causing the issue for madwifi users? ;)

---

### Post by ubuntu27 on 2009-04-18
Hello everyone. I have Atheros AR5007 802.11b/g WiFi.
 And the Wireless connection works flawlessly out of the box with Ubuntu Jaunty Beta & RC.

I have not installed it to the laptop, but, it runs well on the LiveCD/DesktopCD.

What it is interesting is that Ubuntu Jaunty recognizes my wireless card as Atheros AR242x:

```

ubuntu@ubuntu:~$ lspci

[Snipped!]

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
ubuntu@ubuntu:~$ 

```

```
ubuntu@ubuntu:~$ lspci -v

03:00.0 
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k

```


```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:0d:96:65
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
      
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.3 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
      
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ 

```
But, believe me, this is actually AR5007.

I wonder if I can do something for you guys. If you tell me to post some command or config file I will do it. (I am not a pro yet)

---

### Post by Narvinye on 2009-04-18
Cool two posts about 9.04 fixing this! :D Can anyone else confirm?
Note you will lose all installed apps if you do a fresh install and its recommend to put home on its own partition so you dont lose your data.

---

### Post by Polygon on 2009-04-18
yeah thats the same exact card i have ubuntu27 (cause the AR5007 is misreported as a  AR242x  on mine as well) and i can't even connect to the internet, in both arch and ubuntu

maybe it will magically work when jaunty final is released....i dunno..

---

### Post by mbott on 2009-04-18
> **ubuntu27 said:**
> Hello everyone. I have Atheros AR5007 802.11b/g WiFi.
 And the Wireless connection works flawlessly out of the box with Ubuntu Jaunty Beta & RC.

I have not installed it to the laptop, but, it runs well on the LiveCD/DesktopCD.

What it is interesting is that Ubuntu Jaunty recognizes my wireless card as Atheros AR242x:

[SNIP]

But, believe me, this is actually AR5007.

I wonder if I can do something for you guys. If you tell me to post some command or config file I will do it. (I am not a pro yet)

9.04 was a clean install on my system, too.

-- 
Mike

---

### Post by Narvinye on 2009-04-19
So the 9.04 build will work with the card but the connection is slower.  How are you testing the speed of your card on the system? I've noticed it can be a bit sluggish but nothing too bad.

---

### Post by Reiger on 2009-04-19
And the `wonder' is actually way back from Intrepid (with the backports enabled).

So to anyone who has old/outdated backports on his system: you may has some luck when removing those in favour of the Jaunty ones?

---

### Post by 67GTA on 2009-04-19
Same here with Jaunty RC. I have used ndiswrapper until now because of slow speeds. I switched to 64bit with Jaunty, and can not get ndiswrapper to work. The speeds in Jaunty are better than in previous releases (48 Mb/s). My card is capable of 54. The alternate madwifi driver offered in Jaunty doesn't work.

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
``````
wlan0     IEEE 802.11bg  ESSID:"Dynex"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:0F:6F:2A   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  Noise level=-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by ubuntu27 on 2009-04-19
Weird. Why is it that for some of us it works, and for others, it doesn't?

---

### Post by Peter09 on 2009-04-19
I have a similar problem with the ath5k driver. I have noticed that it will never resume from a shutdown unless there is a power-off, even then it is intermittent. It appears that the wireless card is not being reset in someway and unless it is powered down the card will not resume. I take the battery out of my laptop to ensure total loss of power.

The symptoms are that an attempt is made to connect to my WPA network but it fails and I am continually asked for the password. The only way to get it to work is a complete power off.

When it does work, speed is reported at 1Mb, but otherwise ok.

This problem seems to have started somewhere along the line in Jaunty.

---

### Post by plun on 2009-04-19
I am trying to help a user within my country with this.

I can only find this bug report about it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004)

Incomplete and undecided...:(

--

---

### Post by tazd on 2009-04-19
Well since updating the beta to RC i have totally lost access to my 5007 wireless card, which is strange as it was working before i did the update to RC.
Well can only hope this is fixed in the final release.

---

### Post by 67GTA on 2009-04-19
> **plun said:**
> I am trying to help a user within my country with this.

I can only find this bug report about it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350004)

Incomplete and undecided...:(

--

I just installed linux-backports-modules-jaunty and my speed now shows 54Mb/s. The updated ath5k module may help some with speed problems.

---

### Post by Narvinye on 2009-04-19
linux-backports-modules-jaunty fixed the speed issue for me.  Before I was getting 1MB bit rate and it would not work over 24.  Its showing 54MB now and working with no issues.

---

### Post by mbott on 2009-04-19
> **Narvinye said:**
> linux-backports-modules-jaunty fixed the speed issue for me.  Before I was getting 1MB bit rate and it would not work over 24.  Its showing 54MB now and working with no issues.

And I think we have a winner!  :D

-- 
Mike

---

### Post by bubba_169 on 2009-04-19
I've been using ndiswrapper since ath5k stopped working and it's been working that well I probably wont switch back until I have to reinstall for some reason.

---

### Post by Polygon on 2009-04-19
> **Narvinye said:**
> linux-backports-modules-jaunty fixed the speed issue for me.  Before I was getting 1MB bit rate and it would not work over 24.  Its showing 54MB now and working with no issues.

it made it worse for me, i was getting 24 mb/s and now im getting 18 or lower.

---

