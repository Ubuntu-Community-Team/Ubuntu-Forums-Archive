---
title: "How do I instal Intel PRO wireless 3945ABG driver in Ubuntu 12.04"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by VictoriousONE on 2012-05-06
I am totally lost on this.  I have spent days and days searching the Internet for a solution to this issue but I have gotten nowhere so far.  Can anyone here walk me through the procedures to get my wireless card  drivers installed in Ubuntu 12.04? I am new to Ubuntu, so, it will have to be a step by step process, but, I can follow instructions very well if given the right directions. Your help will be extremely appreciated.

---

### Post by VictoriousONE on 2012-05-07
Did I say something wrong or is this just a slow moving forum?  Sure could use a hand with this problem.

---

### Post by Pilot6 on 2012-05-07
You do not need any drivers for that adapter. Driver is included unto kernel and installed automatically.
What is your problem? You cannot setup a wireless connection or what?

---

### Post by darkod on 2012-05-07
What is actually going on, it doesn't exist as a network adapter?

If you open terminal and type:
ifconfig

do you see your wi-fi adapter there?

---

### Post by VictoriousONE on 2012-05-07
Yes, I am trying to set up a wireless connection.  Below is what I get when I enter ifconfig.

vic@vic-Aspire-5610:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:f2:24:a5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fef2:24a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31821399 (31.8 MB)  TX bytes:947012 (947.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22468 (22.4 KB)  TX bytes:22468 (22.4 KB)

---

### Post by darkod on 2012-05-07
It seems your adapter is not working. Maybe the correct module is not loaded or it has a conflict with another module.

One thing you could check, if you click the Network Manager icon top-right, does it show option Enable Wireless and does it have a tick mark next to it?

---

### Post by darkod on 2012-05-07
Google says the module used for that card is iwl3945. You can see whether you have that module loaded in terminal with:
lsmod | grep iwl3945

---

### Post by VictoriousONE on 2012-05-07
This what I get when I run the command you gave me:

 vic@vic-Aspire-5610:~$ lsmod | grep iwl3945
iwl3945                73111  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211

---

### Post by darkod on 2012-05-07
Looks loaded. Did you check if maybe wireless is disabled in Network Manager? That's the network icon in the top-right, close to the clock. If you are connected by cable right now, the icon is like two arrows up/down. Click on it and check in the menu that opens whether Enable Wireless has a tick mark. If it doesn't, click on it.

---

### Post by VictoriousONE on 2012-05-07
Wireless is enabled in Network Manager, but, it keeps trying to connect but does not and has never connected. When I click on the 2 arrows the wireless radio icon comes on flashing but never becoming solid yet the wireless network is not engaged. Keeps telling me that authentication is required by network even though I have entered the correct password.  This is the same password that I use on the Windows operating system network and the password works on those computers.

---

### Post by darkod on 2012-05-07
Hmm, it might be "confused" by something. When you click on the network manager icon you should see the option Edit Connections at the bottom. Go there and click the Wireless tab.

Select the connection to your network, and remove it. Close edit connection.

Now when you click on the network manager again, it should display available networks. Try connecting again to your wireless.

---

### Post by VictoriousONE on 2012-05-07
> **darkod said:**
> Hmm, it might be "confused" by something. When you click on the network manager icon you should see the option Edit Connections at the bottom. Go there and click the Wireless tab.

Select the connection to your network, and remove it. Close edit connection.

Now when you click on the network manager again, it should display available networks. Try connecting 
again to your wireless.

I removed my network connection and then tried to reconnect.  It showed my network plus several others in the neighborhood so it's seeing the networks but it will not connect, just keeps trying.

I installed Ubuntu on a USB thumb drive and then ran my other computer with the thumb drive containing Ubuntu 12.04 and the wireless worked just fine on the desktop computer, therefore, the program and network password are fine.  I tried the same thing on my laptop with the wireless problem booting from the thumb drive with Ubuntu, but, no dice, it will not connect to the wireless network.

I should also mention that this laptop also has Vista installed and I have no problem connecting to the wireless network when running Vista.  It almost seems like the problem is in the wireless settings in Ubuntu, but, I'm only guessing at this point.  Thanks for trying so far but I sure wish I knew about Ubuntu so I could get this wireless working.

---

### Post by VictoriousONE on 2012-05-07
Is this typically what Linux forums are like, very quiet?  Anytime I had a question about Windows in Windows forums it seemed like I got a million answers to my questions almost instantly.  Is this an omen telling me to steer clear of Linux or is this just an unuasually slow day in this forum?  I realy am liking Ubuntu 12.04, but, it seems so very difficult to get any help with this operating system.  I'm not being snotty or sarcastic, I'm just trying to find out if Ubuntu 12.04 is worth my time or not. Sure would appreciate some good help with getting the wireless working on my Ubuntu 12.04 system and then I think that I could enjoy it while learning how to work it better.
 
Can anyone help me get my wireless working?

---

### Post by darkod on 2012-05-07
Personally I don't have further ideas. You can see if there are inactive adapters with:
ifconfig -a

But even if it lists your wi-fi, not sure how to enable it since the module looks loaded, it can see your network, but doesn't connect to it.

You might have better luck in the networking section of the forum. I am not an admin so I can't move this thread there.

---

### Post by darkod on 2012-05-07
PS. Can it be something from these two threads?
Especially the first one has some commands to try even though it is for 10.10.
[http://ubuntuforums.org/showthread.php?t=1689100](http://ubuntuforums.org/showthread.php?t=1689100)
[http://ubuntuforums.org/showthread.php?t=1972448](http://ubuntuforums.org/showthread.php?t=1972448)

---

### Post by thatguruguy on 2012-05-07
> **VictoriousONE said:**
> Is this typically what Linux forums are like, very quiet?  Anytime I had a question about Windows in Windows forums it seemed like I got a million answers to my questions almost instantly.  Is this an omen telling me to steer clear of Linux or is this just an unuasually slow day in this forum?  I realy am liking Ubuntu 12.04, but, it seems so very difficult to get any help with this operating system.  I'm not being snotty or sarcastic, I'm just trying to find out if Ubuntu 12.04 is worth my time or not. Sure would appreciate some good help with getting the wireless working on my Ubuntu 12.04 system and then I think that I could enjoy it while learning how to work it better.
 
Can anyone help me get my wireless working?

If you have trouble getting answers to your questions here, you may sometimes find an answer on [askubuntu.com]("http://askubuntu.com/").  It's free, and it's searchable. Here's a post dealing with a problem that [sounds a lot like yours]("http://askubuntu.com/questions/128794/intel-pro-wireless-3945abg-drops-wireless-and-forgets-wireless-pass-key-every-10").

---

### Post by westie457 on 2012-05-07
Hi try resetting the security of the router to WPA/WPA2 personal then reconnecting.

If that still fails Edit the connection in 'Network Manager' and set IPv6 to ignore.

Either course of action or both will be necessary.

---

### Post by VictoriousONE on 2012-05-07
Thanks for pointing me in the right direction guys.  I made some changes in the edit network connection panel and lo and behold the wireless network suddenly turned on and seems to be working fine now.  Thank you, thank you, thank you.  Don't know exactly what changes I made precisely (although I would like to know) but all is well thanks to your prompts.  Have a good nite all.

---

### Post by WishForHelp on 2012-08-23
> **VictoriousONE said:**
> Thanks for pointing me in the right direction guys.  I made some changes in the edit network connection panel and lo and behold the wireless network suddenly turned on and seems to be working fine now.  Thank you, thank you, thank you.  Don't know exactly what changes I made precisely (although I would like to know) but all is well thanks to your prompts.  Have a good nite all.

What exactly did you changed? I'm having the same problem, and they don't know the answer it seems... This really sucks a lot... I only can use wifi here, can't sit the whole day near the router with a cable.... I used every 'solution' I've found on the net but.... nope, nothing at all!!!

I hope you will ever see this post again, and tell me. :(:(:(:(:(:(

---

### Post by tekCTRL on 2012-08-27
AH I was having this problem with my Sony Vaio VGN-SZ61MN with the intel Pro wireless 3945ABG WiFi installed. I was trying to connect to a BT Home Hub and it kept dropping connections. Eventually discovered that Ubuntu was getting the wrong security type for my password and thought it was WEP and not WPA2 oddly. Thought it would of worked it out correctly from the get go but it seems it didn't. Manually added in the right security and no more dropped connections!

---

### Post by LikA380 on 2013-01-18
Hello to all! I'm new in Ubuntu (just installed first time and ONLY because it was my last hope to fix wireless issue). It may be a stupid thing but, disconnect your Modem and the Rooter from the current for few seconds and reconnect them back. I was upset  because nothing worked and for a moment I did that.
After reconnecting them to current, the wireless connection was established in few seconds.
I really have no idea what happened. The problem appeared when I've tried to switch off  the wireless physically and for win XP I've got no solution.
Good luck!

---

