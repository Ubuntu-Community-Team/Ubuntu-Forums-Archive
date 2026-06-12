---
title: "Does lucid have some tcp ip connections number limit?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-23
is it possible that lucid have some sort of tcp ip connections nubmer limit because torrents here most of the time work very very slow here but sometime there fast and in amule i get low ID so how can i check that?

thanks in advance.

---

### Post by P4man on 2010-04-23
more likely its a port forwarding problem from the router. What client are you using?

---

### Post by aviramof on 2010-04-23
i have no router i'm using adsl modem dsl-600E and i use transmission but i also tried other clients and i also have speed problem with amule and linuxDC++

---

### Post by P4man on 2010-04-23
In that case, have a look here:
[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by aviramof on 2010-04-23
i don't see any thing there that can help i really don't understand this and i also don't understand why i can't use network manager adsl option it never dial from there i'm using
pppoeconf in order to connect.

in any case i'm going to download the RC dvd version and format again because something here isn't right.

---

### Post by P4man on 2010-04-23
Is it a modem (USB?) or a router (using ethernet?).

If it a modem, then the problem might be right there. Even some routers choke on bittorrent, causing the router to run out of memory due to too many open connections, I wouldnt be surprised to see cheap USB modems do worse, and linux implementation of drivers for that modem to be worst of all.

If its a half decent router (that does BT fine with windows) then ignore the above.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> i have no router i'm using adsl modem dsl-600E and i use transmission but i also tried other clients and i also have speed problem with amule and linuxDC++

That modem **is** a router. [http://www.aztech.com/prod_adsl_dsl600e.html](http://www.aztech.com/prod_adsl_dsl600e.html)

---

### Post by P4man on 2010-04-23
> **Longinus00 said:**
> That modem **is** a router. [http://www.aztech.com/prod_adsl_dsl600e.html](http://www.aztech.com/prod_adsl_dsl600e.html)

Good catch. It is indeed. That he needs PPOE seems to indicate the router is not set up properly and working as a bridge.

---

### Post by psyke83 on 2010-04-23
> **P4man said:**
> Good catch. It is indeed. That he needs PPOE seems to indicate the router is not set up properly and working as a bridge.

Well.... from the product page, it seems that users do need to connect via PPPoE/A: > From: [http://www.aztech.com/prod_adsl_dsl600e.html](http://www.aztech.com/prod_adsl_dsl600e.html)
Targeted at the                                                                 residential users,                                                                it is for  both the                                                                single  user with                                                                Bridge  mode with                                                                host based  PPPoE                                                                Client or  for multi-users                                                                utilizing  the DSL600EU                                                                inbuilt  PPPoE/A,                                                                IP  routing, NAT                                                                 functionality to                                                                share the  ADSL link.                                                              aviramof,

As I mentioned to you in an older thread, the steps you were following to allow auto-login were causing issues with your GNOME Keyring (since you seemed to have no active default keyring). NetworkManager depends on a working default keyring in order to store passwords, so don't mess with the keyrings in future.

I gave you steps to try and fix it (to re-create a keyring, and to remove any custom manual network configuration), but you never indicated if you even tried the steps.

---

### Post by P4man on 2010-04-23
> **psyke83 said:**
> Well.... from the product page, it seems that users do need to connect via PPPoE/A: 

from that quote, it seems to support both. The OP says he has to use ppoeconf, which wouldnt be necessary if the router was setup to connect using PPoA. Then he'd just get an IP from the router and thats that.

Now I'm not entirely sure what the best approach would be for bittorrent and when you only have 1 pc, but id definitely prefer my router doing the pppox stuff than my PC. unless its a really crappy router.

Either way before delving deeper in to any potential BT problems, I think the OP has some other things to verify first. AFAICT, there isnt anything in Lucid that would prevent a bittorrent client from achieving line speed on a properly configured network.

---

### Post by psyke83 on 2010-04-23
> **P4man said:**
> from that quote, it seems to support both. The OP says he has to use ppoeconf, which wouldnt be necessary if the router was setup to connect using PPoA. Then he'd just get an IP from the router and thats that.

Now I'm not entirely sure what the best approach would be for bittorrent and when you only have 1 pc, but id definitely prefer my router doing the pppox stuff than my PC. unless its a really crappy router.

Either way before delving deeper in to any potential BT problems, I think the OP has some other things to verify first. AFAICT, there isnt anything in Lucid that would prevent a bittorrent client from achieving line speed on a properly configured network.

I am quite sure that aviramof needs to use ppoeconf rather than NetworkManager because he/she deleted their GNOME keyring; if you do a search you will see the older post (in which I also replied, trying to provide assistance).

My understanding is that PPPoE and PPPoA are virtually identical in terms of functionality and efficiency (the latter being slightly more optimal), but neither of these protocols can negotiate connections without a pre-existing configuration set; are you mistaking PPPoA for DHCP? If the modem was in fact a genuine router, then clients should ideally connect via DHCP; the PPPoE/A connection would be negotiated between the router itself and the ISP.

Getting back to the bittorrent issue - it could be a port forwarding problem (such as UPnP/NAT-PNP not being supported on the modem/router), or an efficiency problem (on Windows, uTorrent 2.0 uses different bandwidth management algorithms compared to Transmission), or less likely, a tracker problem (Transmission gets blacklisted by clients).

---

### Post by aviramof on 2010-04-23
as for deleteing my GNOME keyring i do have a problem with it sometimes someting about no communication with the kernel engine or daemon i posted a bug report about it but in network manager it does save the password but it still doesn't work maybe because i chose unsafe storage.
 
as for how i connect i use pppoeconf in alt+F2 i set user name and password and everything eles next and as for the amule+bittorent+linuxDC++ none of this softwares is working well in ubuntu in amule i can see that i get Low ID and i don't know why.
 
is there any information or commands that i can use to check and see if there is any problem because i don't think formating would really help.
 
i tried to install pppoe package which for some reason is not installed by default and removed ufw is there something eles i can do?any information i can check or post here to so i could solve this problem once and for all?

---

### Post by sdowney717 on 2010-04-23
this came to mind, ISP slowing down torrent traffic

[http://torrentfreak.com/comcast-throttles-bittorrent-traffic-seeding-impossible/](http://torrentfreak.com/comcast-throttles-bittorrent-traffic-seeding-impossible/)

> the past weeks more and more Comcast users started to notice that their BitTorrent transfers were cut off. Most users report a significant decrease in download speeds, and even worse, they are unable to seed their downloads. A nightmare for people who want to keep up a positive ratio at private trackers and for the speed of BitTorrent transfers in general.

Comcast Throttles BitTorrent Traffic, Seeding ImpossibleISPs have been throttling BitTorrent traffic for almost two years now. Most ISPs simply limit the available bandwidth for BitTorrent traffic, but Comcast takes it one step further, and prevents their customers from seeding. And Comcast is not alone in this, Canadian ISPs Cogeco and Rogers use similar methods on a smaller scale.

> And Comcast is not alone in this, Canadian ISPs Cogeco and Rogers use similar methods on a smaller scale

> Last year we had a discussion whether traffic shaping is good or bad, and ISPs made it pretty clear that they do not like P2P applications like BitTorrent. One of the ISPs that joined our discussions said: &#8220;The fact is, P2P is (from my point of view) a plague &#8211; a cancer, that will consume all the bandwidth that I can provide. It&#8217;s an insatiable appetite.&#8221;, and another one stated: &#8220;P2P applications can cripple a network, they&#8217;re like leaches. Just because you pay 49.99 for a 1.5-3.0mbps connection doesn&#8217;t mean your entitled to use whatever protocols you wish on your ISP&#8217;s network without them provisioning it to make the network experience good for all users involved.&#8221;

---

### Post by aviramof on 2010-04-23
Yes i don't use comcast and i don't my isp netvision is throttleing connectios and i'm using this isp for about eight or nine years far more then i use ubuntu and in any case
there is nothing i can do about it i can leave this isp for the next ten month what i need to do is to find out what is the problem in ubuntu is it something in pppoe packahe or pppd or tcp ip something eles.
 
and by the way via http i now download ubuntu 10.04 RC DVD at 500KB which is my max for the next ten months.

---

### Post by Longinus00 on 2010-04-23
In transmission, under the preferences menu, go to the network tab and test your port. If it reports the port as closed then you'll need to open it to get max performance. This can usually be done via a page on your router's web interface.

---

### Post by andrewthomas on 2010-04-23
> **P4man said:**
> from that quote, it seems to support both. The OP says he has to use ppoeconf, which wouldnt be necessary if the router was setup to connect using PPoA. Then he'd just get an IP from the router and thats that.

+1 Let the modem handle the PPoE

---

### Post by aviramof on 2010-04-23
and how exceclly do i do that i don't understand exceclly what you mean?
 
pppoeconf is the only way i know to connect to my isp because network manager don't work for me.

---

### Post by andrewthomas on 2010-04-23
Log into the router using the web based                                                                           HTTP management                                                                           GUI and configure it properly.

EDIT you should be able to access it at 192.168.1.1

---

### Post by aviramof on 2010-04-23
in windows it's 10.0.0.138 but i don't want mpls connection meaing permenet one if i wanted it i would have used a router or ask for it from my isp i like the fact that i can
connect or dissconnect when ever i want to and change ip when ever i want to.
 
the only problem i have is with this low id and torrents problem and that should not happen ubuntu should work better then that.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> in windows it's 10.0.0.138 but i don't want mpls connection meaing permenet one if i wanted it i would have used a router or ask for it from my isp i like the fact that i can
connect or dissconnect when ever i want to and change ip when ever i want to.
 
the only problem i have is with this low id and torrents problem and that should not happen ubuntu should work better then that.

I told you to check if you port is open or not.

---

### Post by cariboo on 2010-04-23
It also depends a lot on what torrent you are downloading, I currently have one going, the transfer rates have never been more than 20Kbps, while yesterday I downloaded the Alternate install iso via bittorent, it was finished in less than 5 minutes.

---

### Post by aviramof on 2010-04-23
the problem is that even with six or seven torrents or more i can bearly reach 150KB and it happen a lot but sometimes it reach 500kb with one torrent and my torrents are
from private trackers not public one.
 
is it possible that there are or there should be newer pppd or rp-pppoe and etc software that don't come with lucid or that should be updated to work better with lucid?
 
did any of the developers ever tried to check that?

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> the problem is that even with six or seven torrents or more i can bearly reach 150KB and it happen a lot but sometimes it reach 500kb with one torrent and my torrents are
from private trackers not public one.
 
is it possible that there are or there should be newer pppd or rp-pppoe and etc software that don't come with lucid or that should be updated to work better with lucid?
 
did any of the developers ever tried to check that?

Why do you continue to ask for help when you were given useful advice already? Check if your ports are open before doing anything else.

---

### Post by aviramof on 2010-04-23
i have a modem not router of course my ports are open and yes i checked via transmission many times and the port was open there

any way i installed ubuntu again now RC version and network manager seem to work but i still have some problem getting it to connect automaticly will see if it would help with torrent.

and by the way does something in this command might cause problems?

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted startupmanager acpi gnome-device-manager apt-p2p mplayer smplayer gnome-mplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview assogiate fusion-icon simple-ccsm emerald vlc cheese compiz subversion compiz-fusion-plugins-extra gmountiso rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree gstreamer0.10-ffmpeg samba gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar && aptitude install xfonts-terminus compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev 
```

---

### Post by P4man on 2010-04-23
problem is most likely the tracker or peers not accepting your bt client; because its not on their approved list: Nothing ubuntu devs can do about that; im sure it will work fine on a public (and legal) tracker like those hosting ubuntu releases?

---

### Post by aviramof on 2010-04-23
the site support my bt client i have accounts so the tracker also accept everything any way i reinstalled ubuntu let's see if it fixed the problem.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> i have a modem not router of course my ports are open and yes i checked via transmission many times and the port was open there

any way i installed ubuntu again now RC version and network manager seem to work but i still have some problem getting it to connect automaticly will see if it would help with torrent.

and by the way does something in this command might cause problems?


I've told you multiple times your modem is a combined modem/router. Do you have upnp enabled? Are you using random ports?

---

### Post by psyke83 on 2010-04-23
> **Longinus00 said:**
> I've told you multiple times your modem is a combined modem/router. Do you have upnp enabled? Are you using random ports?

I feel like we're talking to a brick wall ;)

aviramof, even if your modem is not a router, Ubuntu itself has a  built-in firewall. Your ports may be closed via a software **or **hardware  firewall, or your ISP may be blocking certain ports. Either way, you  need to check Transmission to see if it reports the currently used port  as open or closed. That is the best way to begin troubleshooting speed  problem

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> 
and by the way does something in this command might cause problems?

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted startupmanager acpi gnome-device-manager apt-p2p mplayer smplayer gnome-mplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview assogiate fusion-icon simple-ccsm emerald vlc cheese compiz subversion compiz-fusion-plugins-extra gmountiso rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree gstreamer0.10-ffmpeg samba gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar && aptitude install xfonts-terminus compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev 
```

Just stop before going ahead with installing those packages, please. **Why **are you installing these packages? Do you even need them? Don't indiscriminately install packages unless you're sure that you need them - and I **know** that you're not sure if you need them.

You're installing Adobe's flash, gnash and swfdec packages. They conflict with each other and you only need **one**. You're installing libflashsupport - **why**? It causes Adobe flash to crash at random intervals.

Do some research about what you put on your system and stop relying on others to guide your every action.

---

### Post by aviramof on 2010-04-23
i know my  modem is a combined modem/router i tried accessing it setting in 192.168.1.1 with no luck the same go with 10.0.0.138 but again i don't want to use my modem as a router i don't want a fix ip i just want to fix my problem with torrents.

as for the command this is something i made for my self so of course it's not error proof but as for the packages i don't install them i remove them "sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla"

as for the rest i believe  i need them all either as them self or as dependencies for other softwares but again there could be some errors there like dependencies packages that i don't really need and etc.

---

### Post by P4man on 2010-04-23
Try this torrent:
[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent)

If you get line speed on that one, the problem is with your tracker or your peers, and not ubuntu. At least nothing ubuntu can do to solve it.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> i know my  modem is a combined modem/router i tried accessing it setting in 192.168.1.1 with no luck the same go with 10.0.0.138 but again i don't want to use my modem as a router i don't want a fix ip i just want to fix my problem with torrents.

Listen, your modem is a router. It will never not be a router. Get over it.

Second, if you want to find your gateway ip address, use route.

```
$ route -n
```

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> i know my  modem is a combined modem/router i tried accessing it setting in 192.168.1.1 with no luck the same go with 10.0.0.138 but again i don't want to use my modem as a router i don't want a fix ip i just want to fix my problem with torrents.

as for the command this is something i made for my self so of course it's not error proof but as for the packages i don't install them i remove them "sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla"

Ok, I didn't see the "remove" part - you should indeed remove them from your system if they are installed. Anyway, mixing up multiple issues in the same thread is not going to help get your problems sorted any faster.

---

### Post by aviramof on 2010-04-23
Well downloading this torrent is not going well i only get 30K right now and i am connected to 51 out of 60 in transmission and i really don't know what do to about it anymore.

any more suggestion on how to check my connection?softwares that would show me 
all the connections that run in ubuntu and etc?

as for the command i just wanted to make sure that there is nothing there that is going to cause problem to my new RC installation i just did.

---

### Post by P4man on 2010-04-23
Actually, for whatever reason, Im not getting anything more on that torrent myself right now... and that is under windows 7 with utorrent. Its usually an uber fast torrent, im not too sure whats up with that. Could be a completely unrelated issue on my side though

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> Well downloading this torrent is not going well i only get 30K right now and i am connected to 51 out of 60 in transmission and i really don't know what do to about it anymore.

any more suggestion on how to check my connection?softwares that would show me 
all the connections that run in ubuntu and etc?

as for the command i just wanted to make sure that there is nothing there that is going to cause problem to my new RC installation i just did.

*Check. Your. Ports.* You have been asked to do this repeatedly. See [post #15]("http://ubuntuforums.org/showpost.php?p=9163733&postcount=15").

In Transmission you can also check the "Message Log" from the Help menu.

---

### Post by aviramof on 2010-04-23
i already said in the past that i did test my port and it is open.

i checked the message log and i think it something to do with NAT-PMP

```
Sat Apr 24 01:22:51 2010                 Transmission 1.92+ (10515) &#1492;&#1514;&#1495;&#1497;&#1500;
Sat Apr 24 01:22:51 2010             RPC Server    Adding address to whitelist: 127.0.0.1
Sat Apr 24 01:22:51 2010             DHT    Reusing old id
Sat Apr 24 01:22:51 2010             DHT    Bootstrapping from 136 nodes
Sat Apr 24 01:22:51 2010                2 torrents loaded
Sat Apr 24 01:22:51 2010             port transfer (NAT-PMP)    initnatpmp past (0)
Sat Apr 24 01:22:51 2010             port tranfer (NAT-PMP)    sendpublicaddressrequest past (2)
Sat Apr 24 01:22:51 2010             port transfer    State changed from "not transferd" to "start"
Sat Apr 24 01:22:59 2010             port transfer    State changed from "start" to "???"
```

it might not be accurate because i translated part of it to English but i hope that you would understand it any way.

---

### Post by aviramof on 2010-04-23
i think that the strangest thing is why i can't connect to my modem interface via 10.0.0.138 
i think maybe here lies the problem.

my modem is **aztech dsl 600e router**

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> i already said in the past that i did test my port and it is open.

i checked the message log and i think it something to do with NAT-PMP

```
Sat Apr 24 01:22:51 2010                 Transmission 1.92+ (10515) &#1492;&#1514;&#1495;&#1497;&#1500;
Sat Apr 24 01:22:51 2010             RPC Server    Adding address to whitelist: 127.0.0.1
Sat Apr 24 01:22:51 2010             DHT    Reusing old id
Sat Apr 24 01:22:51 2010             DHT    Bootstrapping from 136 nodes
Sat Apr 24 01:22:51 2010                2 torrents loaded
Sat Apr 24 01:22:51 2010             port transfer (NAT-PMP)    initnatpmp past (0)
Sat Apr 24 01:22:51 2010             port tranfer (NAT-PMP)    sendpublicaddressrequest past (2)
Sat Apr 24 01:22:51 2010             port transfer    State changed from "not transferd" to "start"
Sat Apr 24 01:22:59 2010             port transfer    State changed from "start" to "???"
```it might not be accurate because i translated part of it to English but i hope that you would understand it any way.

The UPnP/NAT-PMP protocols are designed to negotiate with a router and open ports when requested. If you say that Transmission reports the port as **open**, then it doesn't matter what the NAT-PNP/UPnP output says.

---

### Post by Longinus00 on 2010-04-23
I notice you're using an unofficial build of transmission. Where did you get it from?

---

### Post by aviramof on 2010-04-23
i just downloaded it had nothing to do with my problem i was hopping it would fix something but it didn't.
[https://edge.launchpad.net/~transmissionbt/+archive/nightly]("https://edge.launchpad.net/%7Etransmissionbt/+archive/nightly")

my problem does not depend on any spesifiec problem it's probably something between my modem and ubuntu as i said i can't enter my modem configuration from any address i know.

not via  10.0.0.138 and not 192.168.1.1 as been said here before and i just installed ubuntu so it can't be something that i did on such sort time.

maybe it's a driver problem if ubuntu or something eles about hardware recognition.

---

### Post by Longinus00 on 2010-04-23
Have you used route -n to figure out your gateway ip like I suggested?

---

### Post by aviramof on 2010-04-23
i did and something here is very strange:

this are my current address.
```
93.173.128.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.137.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         93.173.128.1    0.0.0.0         UG    0      0        0 ppp0

```i still don't know how or why i can't connect to my modem configuration and i think it's probably the source of my problem.

i have here device manager installed and when i check now there are a lot of question marks i guess it mean that Ubuntu doesn't recognize my hardware as good as i thought.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> i did and something here is very strange:

this are my current address.
```
93.173.128.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.137.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         93.173.128.1    0.0.0.0         UG    0      0        0 ppp0

```i still don't know how or why i can't connect to my modem configuration and i think it's probably the source of my problem

Your gateway is 93.173.128.1

---

### Post by aviramof on 2010-04-23
tried this it doesn't open my modem configuration.

maybe later i would try to connect my modem to my built in network card but i doubt it would work.

---

### Post by P4man on 2010-04-23
since he is using pppoe and his modem/router is acting as a bridge, the gateway you see would be his provider, wouldnt it? I dont know how you should access the modem/router but its probably in the manual :)

---

### Post by aviramof on 2010-04-23
the address i know is 10.0.0.138 then i type admin admin and that it.

but ubuntu want except that for some reason.

---

### Post by Longinus00 on 2010-04-23
> **aviramof said:**
> tried this it doesn't open my modem configuration.

maybe later i would try to connect my modem to my built in network card but i doubt it would work.

The reason it doesn't open up your modem is because you're connecting directly to your ISP via ppp.

---

### Post by aviramof on 2010-04-23
at the moment i'm using network connection option via dsl tab not ppoeconf as before so what 
can i do about this problem now? if i dissconnect it would help i guess?

---

### Post by psyke83 on 2010-04-23
> **aviramof said:**
> at the moment i'm using network connection option via dsl tab not ppoeconf as before so what 
can i do about this problem now? if i dissconnect it would help i guess?

There is a [guide]("ftp://ftp.aztech.com/support/malaysia/ADSL/DSL600E%20Convert%20from%20bridge%20router.pdf") from your router's manufacturer specifically for this purpose.

It seems that your network configuration is messed up; you should be connecting to your **router** (yes, it is a router), via DHCP and not via PPPoE/A. Read the guide carefully.

---

### Post by aviramof on 2010-04-23
well unfortunally the modem doesn't accept the default password  via firefox even that the modem is reset to default options so i can't do anything even if wanted i a fixed ip address.  

in windows 7 it's working fine via ubuntu it's not.

---

