---
title: "DSL Connection"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by salmanal on 2005-09-13
I am, one of many [I hope] persons who tried several Linux distros and 
nearly "canned" Windows. 

I am help up because I'm not sure it recognizes my DSL Modem.

Efficient Networks Speed Stream 5100. I cannot connect to my ISP with Linux, only Windows - UGGH!

I did install Warty yesterday and Loved it. I miscobnfigured 2 things and wanted to install it again, but, this time, it did not connect. (yesterday was fine)

I wiped my hard drive this morning and run Winbdoos on a 25 gig partition.

I want Warty on a 50 gig partition.
I have the DNS info and I use DHCP.

I have 256 MB RAM, 1.5 gHz AMD processor, and radeon vid card. Again, I am 
writing this via Windows and want to "jump off."

Please help,

salmanal   ](*,)

---

### Post by ispmarin on 2005-09-13
Hã, did you try to install the system and the modem did not work? Did you configure the pppoe correctly? The problem, it seems, is just the pppoe configuration.
Try tk-pppoe or some other package that can manage a dsl connection. 

Ivan

---

### Post by salmanal on 2005-09-13
Oh, we must configure PPOE manually? I love this! We actually work
as opposed to Windows doing all for us keeping us uneducated.

I'll try tk-ppope. If there are others, please tell me the ones you
know and where I can set set up/usage info.

Meanwhile, I'll do a Google search.

Thanks so much for the quick response,

salmanal

---

### Post by ispmarin on 2005-09-14
You can configure the pppoe with some scripts that runs pppoe, or you can do a 
dpkg-reconfigure pppoe
This should work. I know that is a kpppp, or something similar on kde, but with no network working, it would be hard to install this. Try tk-pppoe first, this worked for me on debian.

Ivan

---

### Post by salmanal on 2005-09-16
Thanks Ivan,

My ISP requires that my modem's PPOE be disabled and changed to "Bridge" mode.

This worked for some other distros and Ubuntu when I first installed it.

I'll do some reading this weekend and try again Sunday. I purchased both the 
Debian/Gnu Linux, and The Linux Bible this week.

For me, Internet connections off Winblows has been 50/50.

Mepis, and Suse worked all the time with no connection configuration.

Knoppix "live" worked most of the time, Ubuntu worked the first time, and
I liked it enough to deal with a difficult install in order to
install it again.

-s

---

### Post by karuptdata on 2005-09-16
One other thing you may want to try...I know i hada to do this in order for my dsl to work. Under System-Administration-Networking make sure its set to dhcp of course, also make sure that you click on the dns tab and make sure your isp dns servers are listed there..if not get your isps both primary and secondary and list them there and then reboot..thats how i fixed my machine..Hopes this helps...

---

### Post by salmanal on 2005-09-18
Thanks for the tip KaruptData,

I reinstalled Warty this morning and it went beautifully.

Yes, the install did, but the ISP connection still
leaves a bit to be desired.

At the top of the screen, I click on "Computer"

From there, I select Sys Config

Networking

Network Settings

I see  4 Tabs:

Connection, General, DNS, Hosts.

Connection: I add my Ethernet connection as DHCP

General: My PC's System name

DNS: my Primary and Seconday DNS search order per my ISP

Hosts: my Primary DNS search I.P. address with Alias as my ISP' name
I can try entering my ISP's I.P. addres after writing this message.


I OK all of it, Log Off/ON and still cannot connect. What can be missing here?

It was mentioned to me in anoth forum that a Router may take care of
this. My DSL modem is in "Bridge" mode rather than PPOE. I also
don't have extra space for a router, but if I need one, I can Make
space for it.

I connect finely with other distros (Mepis, Mandriva, SuSE), but it like
what Ubuntu offers much more. Mepis is Debian based as well, but it
is a bit Raggedy in my opinion.

Thanks for the support,

-s

---

### Post by salmanal on 2005-09-18
When I checked the Network Settings again,
I saw eth0 is not activated. I tried deactivating and reactivating
it, but to no avail.

When I click on Activate (for eth0), a small check appears and disappears
within one second.

---

### Post by salmanal on 2005-09-19
Time to just drop ubuntu for a distro that connects. I'll try Fedora 4 or
the other distros that did not give me this issue.

---

### Post by karuptdata on 2005-09-19
It doesnt seems as if it is a distro issue i had the same issue with ubuntu fc4 debian sarge..What i did to relieve the issue was set my dsl modem to static at 192.168.0.4 of course gateway default 255.255.255.0 and the gateway needs to be the ip address of your dsl modem.mine for ex was 192.168.0.1....try this before your try a diff distro..

---

