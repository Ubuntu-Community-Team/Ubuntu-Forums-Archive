---
title: "Gutsy internet speed as slow as hell."
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Chris2691 on 2007-10-23
I have installed Gutsy and the performance over the internet is so slow; It makes Windows XP look like a speed demon. Has anyone got a fix or should I reinstall Fiesty.

---

### Post by kentl on 2007-10-23
You could disable IPV6 if it's enabled. It might do some good for you.

---

### Post by Chris2691 on 2007-10-23
I'm pretty new to Ubuntu: How do I disable IPV6

Thanks

---

### Post by handy on 2007-10-23
In Firefox type ***about:config*** in the address field, then type ***ipv6*** in the new filter field that you will see, then double click on the one & only line that you will see in the main window, this will change its boolean value to ***true***, then shut down FF & restart it, you should be free of the delay while ipv6 times out before you start using ipv4.

[***_This links to instructions for disabling ipv6 system wide_***]("http://ubuntuforums.org/archive/index.php/t-87798.html").

---

### Post by zeronothing on 2007-10-23
hey guys,

if you would like to disable IPv6 from being used not only should you disable it from firefox but you should also disable it in the system as well. Their is no reason to have IPv6 enable right now, unless you in a foreign country that supports it but here in the united states i believe no one uses it (talking about the general public). to disable it go through these steps.

1.) open terminal 

2.) sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases_backup

3.) sudo gedit /etc/modprobe.d/aliases

4.) find the section "alias net-pf-10 ipv6" change it to "alias net-pf-10 off"

5.) reboot your pc 

after all of that ipv6 will be disabled on the system not just in firefox. if you have ever done the command ifconfig you will have noticed an output mentioning ipv6's information. after doing this how-to you will no longer see ipv6 mention, meaning its disabled. have fun everyone.

---

### Post by handy on 2007-10-23
***I lifted this from another thread, it's benefit is that it won't be overwritten as aliases can be.***

***To disable IPv6 globally:***

[I]1. Verify that the IPv6 module is loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
ipv6 265856 10

2. From a terminal type:
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. Verify that the IPv6 module is not loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
dbott@thedrake:~$[/I]

It works for me in Kubuntu 7.10 :-)

---

### Post by Nanoelf on 2007-10-24
I tried both solutions, my network connection is still 342 kbps on Gutsy as opposed to 1762 kbps on a windows box. IPV6 is definitely off. Anyone able to help?

---

### Post by VVebbie on 2007-10-24
And how exactly are you measuring this?

---

### Post by handy on 2007-10-24
> **Nanoelf said:**
> I tried both solutions, my network connection is still 342 kbps on Gutsy as opposed to 1762 kbps on a windows box. IPV6 is definitely off. Anyone able to help?

The 2nd one I posted supersedes the first, it takes IPv6 out globally.  I'm sorry I can't help you beyond that.  You should try the networking sup-forum I think.

---

### Post by tmcmurph on 2007-10-24
I upgraded from feisty to gutsy and the internet access is much slower. I was told it could be DNS but I use OpenDNS and it doesn't get any faster. 

IP6 isn't something I've ever had setup. I'll check it tonight when I get home. Did the default change from feisty to gutsy? 

Firefox is much slower. My download speeds haven't changed (tested via dslreports.com).

---

### Post by handy on 2007-10-24
IPv6 it would seem is the default internet protocol in the *buntu's, some people (including myself) have to turn it off so as to remove the delay that is IPv6 timing out before IPv4 is used, others can't browse the web without turning 6 off.  

IPv6 is in the slow process of superseding IPv4, mainly due to there not being enough IP addresses in 4, apparently 6 is much quicker, but I can't speak from experience on that one.

Turning 6 off can't do you any more harm than slowing down your net speeds if you are one of the lucky ones who has a 6 connection with your ISP.  I'm sure that anyone who turns it off & goes backwards will turn it straight back on again. :-)

---

### Post by windsofhell on 2007-10-25
I am having the same issue. Actually I'm almost changing to some other distribution. 
Unfortunately I have tried all the suggestions about how to speed up the Internet connection without any success. :(

---

### Post by linux23dragon on 2007-10-25
O.K I followed Handy s guides below to the letter:-

> 
In Firefox type about:config in the address field, then type ipv6 in the new filter field that you will see, then double click on the one & only line that you will see in the main window, this will change its boolean value to true, then shut down FF & restart it, you should be free of the delay while ipv6 times out before you start using ipv4
> 
To disable IPv6 globally:

1. Verify that the IPv6 module is loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
ipv6 265856 10

2. From a terminal type:
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6



And I also deleted any IPv6 Host addresses in the "Hosts" tab, found in Network Settings (System->Administration->Network). 

Then Reboot.

Worked for me :-)

Thanks Handy.

EDIT: I forgot to mention that I had to log in as root while doing step 2 like this:

```

sudo -i 
echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
```

Otherwise it will error out, as if you just used the "echo" command without using sudo.

---

### Post by Em-Buntu on 2007-10-25
> **handy said:**
> ***I lifted this from another thread, it's benefit is that it won't be overwritten as aliases can be.***

***To disable IPv6 globally:***

[I]1. Verify that the IPv6 module is loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
ipv6 265856 10

2. From a terminal type:
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. Verify that the IPv6 module is not loaded. From a terminal type:
dbott@thedrake:~$ lsmod | grep ipv6
dbott@thedrake:~$[/I]

It works for me in Kubuntu 7.10 :-)

Thanks Hardy.
When I type in step 2 to blacklist IPV6, I get a permission denied message. I'm logged in as admin, and using sudo. Any idea of why it denying me access?

---

### Post by handy on 2007-10-25
> **Em-Buntu said:**
> Thanks Hardy.
When I type in step 2 to blacklist IPV6, I get a permission denied message. I'm logged in as admin, and using sudo. Any idea of why it denying me access?

Try using:

***sudo nano -w /etc/modprobe.d/blacklist***

& add the line:

***blacklist-ipv6***

to the blacklist file.

You can do the above from your standard user account, you should also be able to do the what won't work for you from a standard user account.  That is what ***sudo*** & the password takes care of.

---

### Post by handy on 2007-10-25
> **linux23dragon said:**
> O.K I followed Handy s guides below to the letter:-





And I also deleted any IPv6 Host addresses in the "Hosts" tab, found in Network Settings (System->Administration->Network). 

Then Reboot.

Worked for me :-)

Thanks Handy.

EDIT: I forgot to mention that I had to log in as root while doing step 2 like this:

```

sudo -i &&
echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
```

Otherwise it will error out, as if you just used the "echo" command without using sudo.

You should really just have to blacklist-ipv6, to solve the problem.

---

### Post by ebash on 2007-10-26
Here's another command for creating the blacklist without login is as root, of course the user must have sudo privileges:

```
echo "blacklist ipv6" | sudo tee /etc/modprobe.d/blacklist-ipv6
```

---

### Post by dajhorn on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/131983](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/131983) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If your Ubuntu Gutsy computer is still slow or otherwise thrashing after you disable ipv6, then you also need to remove the trackerd software, which is installed by default eats system resources.

Run this at a command prompt:

[FONT="Courier New"]$ sudo apt-get remove --purge tracker[/FONT]

---

### Post by VirtualTiger on 2007-11-09
If your network is still slow, you might need to look at how your network card is setup and configure it with the **ethtool** command.

The following command will give you information on how your network card is setup:
```
ethtool eth0
```

This command will set it to a fixed speed of 100 mbs and full duplex, and disabled auto negotiation:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

You'll need to research your network card to see what settings will work the best for you.

Add the command to **/etc/rc.local** so its sets it each time you restart your computer.

---

### Post by GlennW on 2007-11-11
> **VirtualTiger said:**
> If your network is still slow, you might need to look at how your network card is setup and configure it with the **ethtool** command.

The following command will give you information on how your network card is setup:
```
ethtool eth0
```

This command will set it to a fixed speed of 100 mbs and full duplex, and disabled auto negotiation:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

You'll need to research your network card to see what settings will work the best for you.

Add the command to **/etc/rc.local** so its sets it each time you restart your computer.

I've been following this thread and similar ones eagerly and this one, finally, is the closest to the motherlode.

I've gone through everything else, disabled ipv6, blah, blah, blah. What I need to do is (after running *ethtool eth0*) is increase the speed from 10 mbs to 100 mbs as per your instructions. However, when I run that command in terminal, the response is that the -s command isn't recognized. 

My question is then, how do I edit/change the speed to 100 mbs?

Thanks.

---

### Post by linux23dragon on 2007-11-12
> **GlennW said:**
> I've been following this thread and similar ones eagerly and this one, finally, is the closest to the motherlode.

I've gone through everything else, disabled ipv6, blah, blah, blah. What I need to do is (after running *ethtool eth0*) is increase the speed from 10 mbs to 100 mbs as per your instructions. However, when I run that command in terminal, the response is that the -s command isn't recognized. 

My question is then, how do I edit/change the speed to 100 mbs?

Thanks.

That command work O.K for me.  You did copy and paste the command?  I was only able to get that error report if I had missed an "f" of "off" (or anything like that).

But does the card support all of those features?

This following command should tell you if thats the case or not : -
```

sudo ethtool eth0
```

If this has anything to do with the problem at all?.

Hope that helps

---

### Post by GlennW on 2007-11-13
Thanks for the response. Unfortunately I'll be away from my Gutsy box until later this week so I won't be able to check my syntax or run your suggested command. 

Speaking of* sudo ethtool eth0*, what should the output be? I'm really new to Ubuntu and know just enough to be really really dangerous! The more specific (basic) you can be the better.

Thanks...

Edit:  I'm having to use Vista Home Premium while I'm away. I must admit that I am not impressed at all! This is seriously a case of MS taking one step forward and two steps back!

---

### Post by nu2lnx on 2007-11-13
I know the feeling.. I put Gutsy on my laptop while on the road - downloaded it and burned it on the work XP laptop and tossed it onto my personal laptop... been using it ever since!

---

### Post by linux23dragon on 2007-11-16
> **GlennW said:**
> 
Speaking of* sudo ethtool eth0*, what should the output be? 


This is how the output looks on my system:
```

core2@core2-desktop:~$ sudo ethtool eth0
[sudo] password for core2:
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: no
core2@core2-desktop:~$ 
```

EDIT: That network port (eth0) is not connected to any network BTW ;-)

---

### Post by GlennW on 2007-11-18
I'm finally back home on my Gutsy box!!! Love it... Thanks for the output***[COLOR="Red"] linux23dragon![/COLOR]***

Here's mine:

[INDENT]glenn@glenn-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: no
[/INDENT]

I've run the command: "sudo ethtool -s eth0 speed 100 duplex full autoneg off" (cut and pasted from your post) and am immediately returned to: glenn@glenn-desktop! Being a complete newb, I have no idea where to go from here.

I've blacklisted ipv6, changed my DNS numbers to the open ones: 208.67.220.220 but have yet to notice an increase in performance. I suspect that eth0 being restricted could be the cause.

Gutsy box:
P4 1.6Ghz, 1Gb RAM, 80 Gb HDD, nVidia Geforce 6200 256Mb.

---

### Post by TaintedTux on 2008-01-08
This is a legitimate issue that has not been fixed to date. I have disabled ipv6 both in my system and in Firefox, with little or no increase in speed. Googling this issue I have seen SO MANY people complaining of this, I'm astounded it hasn't been fixed yet. There has to be a developer or something out there, that can figure this out. Long tim Ubuntu users may remember this problem being present before Fiesty, then ok with Fiesty but it is back in Gutsy. 

Any suggestions are welcome, as I am puzzled and frankly just annoyed at this point with trying to fix it.

---

### Post by divali on 2008-01-10
> **zeronothing said:**
> hey guys,

if you would like to disable IPv6 from being used not only should you disable it from firefox but you should also disable it in the system as well. Their is no reason to have IPv6 enable right now, unless you in a foreign country that supports it but here in the united states i believe no one uses it (talking about the general public). to disable it go through these steps.

1.) open terminal 

2.) sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases_backup

3.) sudo gedit /etc/modprobe.d/aliases

4.) find the section "alias net-pf-10 ipv6" change it to "alias net-pf-10 off"

5.) reboot your pc 

after all of that ipv6 will be disabled on the system not just in firefox. if you have ever done the command ifconfig you will have noticed an output mentioning ipv6's information. after doing this how-to you will no longer see ipv6 mention, meaning its disabled. have fun everyone.

I tried this solution, here in the uk, and it does seem to be working well.

---

### Post by oldsoundguy on 2008-01-10
Do not know how you handle it with a laptop, but with a desktop the choice is obvious .. swap network cards and put in one that will work .. not some 5 buck Fred Flintstone .. break down and spend 10 bucks on eBay and get a 3com or D-Link.  Those work (I had a Farralon NIC in one box and it was slow as flowing mud .. replaced it with a 3com and it flew. NO other change made.)
Of course, you never are sure what a laptop maker sticks in there to save money.

---

### Post by manusharma on 2008-04-26
> **zeronothing said:**
> hey guys,

if you would like to disable IPv6 from being used not only should you disable it from firefox but you should also disable it in the system as well. Their is no reason to have IPv6 enable right now, unless you in a foreign country that supports it but here in the united states i believe no one uses it (talking about the general public). to disable it go through these steps.

1.) open terminal 

2.) sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases_backup

3.) sudo gedit /etc/modprobe.d/aliases

4.) find the section "alias net-pf-10 ipv6" change it to "alias net-pf-10 off"

5.) reboot your pc 

after all of that ipv6 will be disabled on the system not just in firefox. if you have ever done the command ifconfig you will have noticed an output mentioning ipv6's information. after doing this how-to you will no longer see ipv6 mention, meaning its disabled. have fun everyone.

This seems to have worked for me.  I had previously turned off ipv6 within firefox (and gran paradiso) to no avail, have not tried turning it off to confirm that the above is the 'master switch'.  Thanks for the post.

---

