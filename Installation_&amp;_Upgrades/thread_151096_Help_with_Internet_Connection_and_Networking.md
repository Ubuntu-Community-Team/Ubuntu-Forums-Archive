---
title: "Help with Internet Connection and Networking"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by Vinic0com on 2006-03-27
I hate posting this, as I know there are many posts on this subject,
but after working for several hours on it, I'm at my wits end and
can't help but think that someone might be able to point me a the
right direction.

I've been impressed so far about the ease of installation.
There's been no snags in downloading/ burning my own CD and getting 
ubuntu to load. 

However, while installing, it was not able to automatically 
configure the network.

Having my windowsxp system operable is extremely important to my 
business, so I'm using a second hand, older pc to play around with 
Linux, and get accustomed and to make sure it does all  I need 
(I suspect it will), before attempting to load it on my 2.8ghz machine.

Anyway, the hardware being used is:
p3 550 mHz
3.2 G HD
650M + 320 extended ram
3c905C-TX/TX-M [tornado] network card
Linksys wrt54g v.2 w/ v.4 firmware (connected via cat5)
 two desktops and two laptops working on wan



what I've done so far:

installed samba

sudo apt-get install portmap

sudo smbpasswd -a foo

about:config
set ipv6 to true

sudo gedit /etc/modprobe.d/aliases

Change this line: alias net-pf-10 ipv6

To this: #alias net-pf-10 ipv6

(# = commented out), Save & Exit


Network settings ethO is active and using DHCP

 sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:01:02:2b:4b:eb
Sending on   LPF/eth0/00:01:02:2b:4b:eb
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

If it's not obvious, I've been gleening the forums for awhile trying
to find a solution.  From the wiki, it looks like my hardware is all
compatitable, unless  I've missed something!?
At this point I have to wonder if pecking away is going to start
binding things up or conflict altogether.  

Was hoping someone might be available to help point out what might
be the problem and how to resolve it.  

Looks like a nice os, if I can get it launched onto the web!

TIA

vinic

---

### Post by Zimmer on 2006-03-27
I'm no expert on this, but could IPv6 be the problem, from your info...
> about:config
set ipv6 to true
What have you set IPv6 to be true for?

[http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x898.html](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x898.html)
IPv6 does not seem to be enabled for my web browsing on a standard 5.10 install. 
Have you tried the command sudo dhclient  (without the eth0 ) ? to try and get a 'lease'  ?
Have you tried altering network settings via System>Administration>Networking?
Sorry if this is repeating things you may have tried already...
What does dmesg reveal about the detection of the eth0 card?

---

### Post by Vinic0com on 2006-03-27
[QUOTE=Zimmer]I'm no expert on this, but could IPv6 be the problem, from your info...

What have you set IPv6 to be true for?</QUOTE]

I cannot say exactly where, but had come across a post that recommending trying this when having trouble getting online.

But I reset the IPv6 to see.

I'm not sure exactly what has changed now..... I reset the router too and then reloaded a backup of the firmware, and now I can see the router for the first time through Ubuntu.




> 
[http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x898.html](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x898.html)
IPv6 does not seem to be enabled for my web browsing on a standard 5.10 install. 
Have you tried the command sudo dhclient  (without the eth0 ) ? to try and get a 'lease'  ?

Did this and now I'm getting online :p   Yeha.  

One thing about this process, I really feel like it's an accomplishment to get it running.


Your help is Greatly appreciated!!

Thanx so much.

> 
Have you tried altering network settings via System>Administration>Networking?
Sorry if this is repeating things you may have tried already...
What does dmesg reveal about the detection of the eth0 card?

Now I've got to figure out how to get the network working.  I know I installed samba, but not sure how to access it.  Not really asking a question here.  Feel like I should spend some time looking it up........ but would gladly accept any direction.;) 

regards,
Clyde Gill
[http://www.PeacefulBend.com](http://www.PeacefulBend.com)

---

### Post by Zimmer on 2006-03-27
Best place to look..
visit [http://ubuntuguide.org/#installsamba](http://ubuntuguide.org/#installsamba)
and for a 'translation' into layman's english of the Samba user bit see my post here:
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)   post #5

Glad things are working out for you, I enjoy using Ubuntu and have learned a lot over the past 6 months or so.
Best Regards
EDIT:  nice place you have there in Missouri... :)

---

### Post by Vinic0com on 2006-03-28
Here's a distillation of what worked for me for getting online with Ubuntu.  Hopefully it will help someone else out there with the same setup/trouble, or, even better yet, might help a developer in some way!


System>Administration>Networking:
[password]
Select Ethernet connection>properties:
configuration=DHCP
check "Enable this connection"

in Firefox:
Edit>Preferences>Connection Settings>
Auto Detect Proxy Settings for ths network.

restored settings in linksys wrt54g router (this seemed to be critical to get the following step to register)
set "Client Lease Time" to 9999 :-k 

then ran the following in 
Applications>Accessories>Terminal:

 sudo dhclient

**BIG NOTE**:  MUST SELECT [COLOR="Red"]SAVE CURRENT SETUP[/COLOR] SETTINGS WHEN LOGGING OFF UBUNTU!!

It remains to be seen as to whether or not my setup is stable.  Yesterday, I didn't do this last step (thus the red type) and started all over again.   This gave me clues as to the exact steps (I was grabbing at so many) were actually necessary to get the system working.  By yesterday evening, the system was working even after rebooting. This morning, the client lease was no longer valid and it required that I reset the router and ran sudo dhclient again before I had access again.  I suspect it was the router setting for client lease time that was the fault.  It was set to "0" which it says is for one day.  Whether that means 24 hours (it was only about 12 that had lapsed) or overnight, I don't know.  I might know more tomorrow morning! Or if anyone else can clue me in on this, I'd greatly appreciate it.  Maybe there's a way to have ubuntu request another lease on a regular basis?  My other pc's were working fine on the "0" setting.  As noted above, I now have it set to 9999, which to my calculations should be just more than a year, which I could live with.


Thanx again Zimmer, for pointing me in the right direction.  I glanced at some of the references you gave me..... heading back there now.

On to file transfers within the network!!

regards,

Clyde Gill, Ubuntu convert.
[http://www.PeacefulBend.com](http://www.PeacefulBend.com)
[http://www.MissouriGrapeGrowers.org](http://www.MissouriGrapeGrowers.org)
[http://www.Vinic.com](http://www.Vinic.com)

---

### Post by Vinic0com on 2006-03-28
My settings seem to hold only when the system is restarted.

Any clues on how to keep my client settings with the router?

Clyde

---

### Post by Zimmer on 2006-03-28
Well, how about the router settings? Is the router set to be the DHCP server? 
Found some interesting reading here.
[http://www.troubleshooters.com/linux/dhcp.htm](http://www.troubleshooters.com/linux/dhcp.htm)
My Netgear is configured to act as the DHCP server and every time I switch on the PC (router already active) it auto detects and I have never had to fiddle with the network settings .
However, you can set the eth0 network card in the PC to a Static IP address on the network. Maybe that will overcome the problem...
EDIt: a quote from my router help..
Use gateway as DHCP server

The DG814 gateway is set up by default as a DHCP (Dynamic Host Configuration Protocol) server, which provides the TCP/IP configuration for the all the computers that are connected to the gateway.

Unless told to change these settings by your ISP, leave the Use gateway as DHCP server check box checked.

If your ISP has you clear this check box, you must have another DHCP server within your network or else you must manually configure the computer.

---

### Post by Vinic0com on 2006-03-28
I don't think it's a router setting issue.  My four other pc's on the system have no problems (all XP at this point, two wireless laptops).

I tried this sudo command found in another thread:

/etc/init.d/networking restart to /etc/rc.local

but have yet to test to see if it works.  Rebooted once, but haven't really turned the pc off, which is where it would loose it before.

But just for reference, my router is setup as a gateway using DHCP and all the settings I could find in ubuntu are set for DHCP also.

Thanx again for your help.  Nice to have someone else "out there".

The more I work with this OS, the more I like it.  Imagine it will just take a little work, a little fine tuning, to get it where it works best for me.

regards,

clyde

---

### Post by Zimmer on 2006-03-28
Perhaps seeing what IP the router has assigned to the box, then fixing that as the static IP for it might do the trick. I tried a few of the cut down versions of Linux on a very old P2 machine a few weeks ago and had the same problem with one of the Distros, I think it was Ubuntu Lite. DSL (Damn small linux) auto detected and set up ok, but I had to run sudo dhclient for Ubuntu lite every time I rebooted.
There are ways of running that command at startup (I don't know exactly how...yet) if all else fails...

Oh, and what is in your hosts file? That may have a bearing on the problem, if your computer name conflicts with another on the network, maybe...guessing here, though...

---

### Post by Vinic0com on 2006-03-29
Late last night I sorted this problem.  After playing around, and screwing up my /etc/hosts file, I started asking questions about fixing that problem over in the beginners forum (probably where I belonged from the beginning!), and while booting several times in recovery mode, I slipped into the ROM edit area for a looksee.  Found a switch for Plug and Play.  Once that was turned on, the network, including the DHCP, started to work great.  The network was the big surprise. After reading many posts about setting this up, I was prepared for a struggle.  I really didn't do anything special... had installed samba through Synaptic Package Manager... but nothing else really beyond the stuff I listed at the beginning of this thread.  The file system is working better than what windows did.  And I can see both ways easily (from all xp boxes and to all xp boxes).  Nothing was required for setup within the windows boxes which really surprised me.  That was too easy.  I was expecting a challenge!!

Anyway, just wanted to let you know that everything is sorted at this point.  I have learned volumes in the past couple of days.  Hope someone else finds this thread of some use, if not just for entertainment purposes.  Also wanted to say how much I appreciated your feedback and handholding Zimmer.  Truely the ubuntu spirit lives here!

Regards,

Clyde

---

### Post by Zimmer on 2006-03-29
Thanks, Clyde. I will make a note of that as I have another user who is having trouble with the network card side of things and maybe that is the answer for him, too .

---

