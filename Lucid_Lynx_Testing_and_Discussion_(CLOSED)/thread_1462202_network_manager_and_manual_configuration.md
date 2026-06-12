---
title: "network manager and manual configuration"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garba on 2010-04-25
New release, same old problems affecting network manager, I am trying to manually setup my nic through NM but it doesn't seem to work, no default route is set, even tried to manually set it up in the "routes" tab but no luck, the changes I make there just get discarded. Is anybody experiencing the same issue?

---

### Post by Jordanwb on 2010-04-25
On my desktop machine I edited /etc/network/interfaces and removed NM.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1

```

---

### Post by cariboo on 2010-04-25
When using Network-Manager to set a static ip address, you have to press enter after entering each item, eg:

enter ip address, press enter, enter netmask press enter, enter gateway address press enter.

The above has worked for me since Jaunty.

---

### Post by garba on 2010-04-25
> **cariboo907 said:**
> When using Network-Manager to set a static ip address, you have to press enter after entering each item, eg:

enter ip address, press enter, enter netmask press enter, enter gateway address press enter.

The above has worked for me since Jaunty.

Yes, this definitely is quality software well suited for a LTS release. Today out of curiosity I even tried connecting to my VPN through the OpenVPN plugin, I've run into every sort of issues and had to give up in the end. Don't even bother with reporting bugs against this thing (at least, I know I won't), there are bug reports which have been filed two years ago and are still in the "unconfirmed" status.

---

### Post by aviramof on 2010-04-25
I personally gave up completely on connecting via Network manager or pppoeconf and simply set my modem/router as router just so that i could bypass all the network problems i had with linux.

---

### Post by cariboo on 2010-04-25
@aviramof

You make it sound like a bad thing to have your router do the sign on for you. I have 8 systems, both wired and wireless behind a router, with both static and dynamic ip addresses. I can do more connected through the router than I could if I only had a direct connection to the router.

@garba

If you have a Cisco/Linkysy router you can set up a VPN connection in the router.

---

### Post by aviramof on 2010-04-25
the point is i never needed to do that via windows. ever since i had adsl/cable connections that about 9 years i have always used the os to do the
 dialing except a short time i had an mpls connection and now in order to change ip address i need to enter to the modem interface.

and now i also need to find solutions to how to remotely connect to my computer in windows 
and in linux and also how to share my Internet to my other computer in the home network that is 
connected via crossover cable any ideas how to do all of this via the modem/router interface?

and it's not that i can't use Network Manager or pppoeconf to but i have problem with downloading 
via P2P softwares that i have proved that are caused by something in linux  because with linux i reach 
max of 150kb and mostly a lot less then this and without linux i reach more then 500kb in the same bitorrent  
client. 

Or that i have problems with auto login for a very long time i was forced to use this command in order to connect
sudo poff -a && sudo pon dsl-provider because it did not connected on his own despite what pppoeconf said about pppd 
and NM didn't worked either and now when you fixed the auto connect problem i had the fix killed my P2P softwares.

and beside i think you can do better then this NM software that doesn't work very well.

---

### Post by garba on 2010-04-25
> **cariboo907 said:**
> @aviramof

You make it sound like a bad thing to have your router do the sign on for you. I have 8 systems, both wired and wireless behind a router, with both static and dynamic ip addresses. I can do more connected through the router than I could if I only had a direct connection to the router.

@garba

If you have a Cisco/Linkysy router you can set up a VPN connection in the router.

...

You see, we are talking about getting things done through the provided GUI tools here, I believe most people reading this forum perfectly know how to deal with this kind of stuff straight from the CLI, the point I was trying to make is that network manager, after years of development, fails miserably at providing a robust solution for the most trivial network configuration tasks. We are not talking about, say, Tomboy, this is a key system utility. I usually get rid of that thing first thing after a clean install, but I just wanted to give it a try and see what configuring your network interfaces is like for a new user. Actually, NM is such a pile of crap that Canonical should be ashamed of including it in the default install, it just doesn't meet the most basic QA requirements. And yes, this was meant to be a rant. :P

---

### Post by cariboo on 2010-04-25
> **aviramof said:**
> the point is i never needed to do that via windows. ever since i had adsl/cable connections that about 9 years i have always used the os to do the
 dialing except a short time i had an mpls connection and now in order to change ip address i need to enter to the modem interface.

Isn't the external ip address provides by your isp, and internal ip addresses provided by the router?

> and now i also need to find solutions to how to remotely connect to my computer in windows

To connect to a windows computer if it is running a Pro version use Applications->Internet->Terminal Server Client,

to connect to a computer running Unbuntu from Windows, there are several ways of doing it, install openssh-server on the Ubnutu system and use putty from Windows, or if you need a desktop install one of the free vnc windows clients, and use the default remote desktop sharing application. 
 
> and in linux and also how to share my Internet to my other computer in the home network that is 
connected via crossover cable any ideas how to do all of this via the modem/router interface?

Does your router only have one ethernet port? IF you are running a cable between the two systems, why not run a cable for each system? I you want to setup internet connection sharing, you need to set up some iptables rules, see this [howto]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

> and it's not that i can't use Network Manager or pppoeconf to but i have problem with downloading 
via P2P softwares that i have proved that are caused by something in linux  because with linux i reach 
max of 150kb and mostly a lot less then this and without linux i reach more then 500kb in the same bitorrent  
client.

You may be able to reach higher speeds running through the router, you should also check the network settings in which ever bittorrent client you are using/ 

> Or that i have problems with auto login for a very long time i was forced to use this command in order to connect
sudo poff -a && sudo pon dsl-provider because it did not connected on his own despite what pppoeconf said about pppd 
and NM didn't worked either and now when you fixed the auto connect problem i had the fix killed my P2P softwares.

There have been changes made for security reasons, you have been given several solutions to get around problems when using auto login.

> and beside i think you can do better then this NM software that doesn't work very well.

It's mostly a matter of learning how to use the program more than anything else, it is setup to work a certain way by default, ie: not using auto login.

It is pretty hard for a former/current Windows user to start using a Ubuntu testing version as your first. You have habits that don't carry over between Windows and a Linux variant, personally I think you have done pretty well considering your lack of Linux experience.

I hope you will still be around for Maverick testing.

---

### Post by aviramof on 2010-04-26
first of all i am using dsl-600E which is a modem/router with one Ethernet exit it's not a regular router and i am not about to change that.

as for connecting to a windows computer i have managed to do that the problem is to remotely connect to my computer when he's running Ubuntu or windows 7 because now
the modem gets the ip address not the os i need a software like pcanyware that support 
analog methods like this.

my home network is a crossover cable and in my computer i have two network cards 
the problem is to share internet now  because what i did before doesn't work 
i set eth1 as 192.168.137.1 as usual and i have a one way network between the two computer meaning i can access the xp computer via ubuntu but not the other way around

and this internet sharing commands don't work now:
```
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```as for checking network setting in any bittorent client i am using trust me that i already have done everything 
i could possibly  do before i decided to bypase ubuntu dialing methods and use my modem as router.

and i was not talking about auto login before i was talking about auto connect the auto login is not a problem the problem i had that pppoeconf was supposed to set pppd to automatically connect but for a long time it didn't 
worked and NM was unusable at all i tried he didn't worked but when it started to work fine then my bittorent and other P2P softwares started to work very bad and i drive my poor isp crazy but it wasn't there fault or it's combine 
faults that the new Ubuntu setting don't work well with Netvision isp setting but  in the end it was still ubuntu faults that the setting are not good enaf for all isp's and i'm still hopping that what ever update that fixed my auto connect 
problem would be tweaked so that my P2P softwares would work better if it some sort of tcp ip limit then the number should set be higher then now and etc.

Update: 

i managed to share connection using the iptables commands my big problem now is how to remotely  access my computer first via windows to windows and then via windows to ubuntu which i don't think i ever managed to do with ubuntu in the past.

---

