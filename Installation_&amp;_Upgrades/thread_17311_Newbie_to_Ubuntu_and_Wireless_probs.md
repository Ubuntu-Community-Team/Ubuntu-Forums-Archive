---
title: "Newbie to Ubuntu and Wireless probs"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by iakudi on 2005-02-27
Hi,

I'm new to Linux let alone Ubuntu but I know my way around windows and have been a network support guy for ages so know "a bit" about networking..

I have an Acer Travelmate C110i Tablet laptop, I won't even try to make the tablet work !!

But I have a basic Intel 2100b wireless card built in my laptop, Ubuntu recognises it as "ipw2100" and sees it but I just cannot get it to work. I have tried adding my ESSID details and the WEP key but the little window at the top (R) always says that it does not detect any wireless cards. 

This is strange as my wireless light is continously on so the radio switch is on..

PLEASE PLEASE I AM BEGGING for help...I have already removed SuSe 8.2 Professional, Mandrake 10.1 official and SuSe 9.1. I just want to to get my wireless working, my LAN card is detected fine and worls a dream..even my desktop is awesome....I even got my wife (a true PC novice and Microsoft lover) to take notice with Ubuntu.

Can anyone help?

regards

Ismail

---

### Post by alastair on 2005-02-27
Please give the following information :

sudo grep ipw2 /var/log/syslog

ifconfig -a
iwconfig
sudo cat /etc/network/interfaces

---

### Post by iakudi on 2005-02-27
[QUOTE=alastair]Please give the following information :

sudo grep ipw2 /var/log/syslog

ifconfig -a
iwconfig
sudo cat /etc/network/interfaces[/QUOTE]

Ok here goes:

sudo grep ipw2 /var/log/syslog <====I get

Feb 27 21:15:20 localhost kernel: ipw2100: Intel(R) PRO/Wireless 2100 Network Dr iver, 0.53
Feb 27 21:15:20 localhost kernel: ipw2100: Copyright(c) 2003-2004 Intel Corporat ion
Feb 27 21:15:20 localhost kernel: ipw2100: 0000:02:05.0: Detected at mem: 0xE020 0000-0xE0200FFF -> e037d000, irq: 11
Feb 27 23:01:55 localhost kernel: ipw2100: Intel(R) PRO/Wireless 2100 Network Dr iver, 0.53
Feb 27 23:01:55 localhost kernel: ipw2100: Copyright(c) 2003-2004 Intel Corporat ion
Feb 27 23:01:55 localhost kernel: ipw2100: 0000:02:05.0: Detected at mem: 0xE020 0000-0xE0200FFF -> e0380000, irq: 11


ifconfig -a <===== I get

eth0      Link encap:Ethernet  HWaddr 00:04:23:57:2B:53
          inet6 addr: fe80::204:23ff:fe57:2b53/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:e0200000-e0200fff

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:02:D4:75
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe02:d475/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59333862 (56.5 MiB)  TX bytes:2016140 (1.9 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14980796 (14.2 MiB)  TX bytes:14980796 (14.2 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


iwconfig <===== I get

lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"<MY ESSID>"  Nickname:"ipw2100"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0kb/s   Tx-Power=32 dBm
          Retry:on   RTS thr=2304 B   Fragment thr:off
          Power Management:off

eth1      no wireless extensions.

sit0      no wireless extensions.


sudo cat /etc/network/interfaces <===== I get

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
name Ethernet LAN card

iface eth0 inet dhcp
name Wireless LAN card
wireless_essid <ID OF MY ROUTER>
wireless_key <WEP KEY>

auto eth0


I'm in the UK too, I wish I had checked my messages earlier...guess I'll have to wait..
Luckily I can at least use my LAN in my laptop...UBUNTUis great fun and so easy to use (apart from wireless lol)

regards

Ismail

---

### Post by alastair on 2005-02-28
OK - things do not look too bad.

I assume your have a DHCP server on your wireless network somewhere (iface eth0 inet dhcp)?
Is your ESSID broadcast?

I would try the following - assuming AP == your access point.

iwconfig eth0 ap <MAC address of AP>
iwconfig eth0 key restricted <WEP KEY>

Then check :

iwconfig eth0
ifconfig eth0

Assuming you have a DHCP server available, try getting an IP (if you need to) :

dhclient eth0

---

### Post by iakudi on 2005-02-28
[QUOTE=alastair]OK - things do not look too bad.

I assume your have a DHCP server on your wireless network somewhere (iface eth0 inet dhcp)?
Is your ESSID broadcast?

I would try the following - assuming AP == your access point.

iwconfig eth0 ap <MAC address of AP>
iwconfig eth0 key restricted <WEP KEY>

Then check :

iwconfig eth0
ifconfig eth0

Assuming you have a DHCP server available, try getting an IP (if you need to) :

dhclient eth0[/QUOTE]


No this still does not work, what it does is search for the DHCP 255.255.255.255 whist my mask is 255.255.255.0

My AP is on broadcast and on DHCP. 

What I have done is added the MAC address of my laptop and manually assigned an IP address to it. I've restarted and for the first time I see:

freenet IPv6 tunnel (sit1)

But it fails with:

no ipv6 tunnel as been set

I assume this is not good. 

Once I logged in I noticed that my little wireless icon (top right band bar) picked up eth0. BUT when I try pinging anything other than my laptop IP address or lo it says network unreachable..

help

---

### Post by iakudi on 2005-02-28
[QUOTE=iakudi]No this still does not work, what it does is search for the DHCP 255.255.255.255 whist my mask is 255.255.255.0

My AP is on broadcast and on DHCP. 

What I have done is added the MAC address of my laptop and manually assigned an IP address to it. I've restarted and for the first time I see:

freenet IPv6 tunnel (sit1)

But it fails with:

no ipv6 tunnel as been set

I assume this is not good. 

Once I logged in I noticed that my little wireless icon (top right band bar) picked up eth0. BUT when I try pinging anything other than my laptop IP address or lo it says network unreachable..

help[/QUOTE]


I recreated my wireless setting, with the static IP address and when deactivate and re-activate the wireless card in Networking, for a few seconds I am connected (yippeeeeee)..........but then it just drops it straightaway..

PLEASE people...I am so close..help

---

### Post by alastair on 2005-02-28
DHCP to "255.255.255.255" is normal - it is a broadcast, looking for a reply on the local network to get an IP.

You should be more specific - "added the MAC address of my laptop and manually assigned an IP address to it" - on your laptop? or the DHCP server? What commands? The MAC address I mentioned was the wireless AP itself.

I would forget about the GUI for the moment and use the terminal - this is useful stuff to know anyway. I ignore the GUI just now because it misbehaves sometimes.

Have 2 terminals open - in one, "tail" the system log so you know the state of any changes on the system and can see things happening as they occur i.e. one shell :

sudo -f /var/log/syslog

In another terminal :

1) iwconfig eth0 ap <MAC address of AP>

Perhaps :
2) iwconfig eth0 essid <ESSID name>

... then check "ifconfig eth0' and 'iwconfig eth0'

Perhaps then :

3) iwconfig eth0 key restricted <WEP KEY>

e.g. iwconfig eth0 key restricted 6641465481241...

Then check :

iwconfig eth0
ifconfig eth0

It is useful to see if there is any difference here in the outputs from before.

You can manually set an IP address (if you do not want to use DHCP) using :

ifconfig eth0 <IP address> netmask <MASK>

e.g.

ifconfig eth0 192.168.0.10 netmask 255.255.255.0

---

### Post by iakudi on 2005-02-28
I set up the MAC address of my laptop on my AP itself and assigned it a static IP address. this is what I then used in my wireless setting:

ie. in AP 192.186.1.100 <MAC address of wireless card>

I tried to follow your instructions but everytime I type 

iwconfig eth0 ap <MAC address of ap>    <==== I am assume u ment XX:YY:XX: etc

it comes back with :

Invalid Hardware address XX:YY:XX
Error for wireless request "Set AP Address" (8B14):
  invalid argument "XX:YY:XX"

If I try XX:YY:XX as XXYYXX it has same error code but the message is Invalid interface  address XXYYXX

so I cannot get past this.

Also, my WEP key is set as a 13 charcter ASCII (128 bit), when you advise me to set here do I:

 just type the same ASCII characters or 

do I type s:XYXYXYXYXYXYX 

messages in syslog inc:

- eth0: Radio is disabled by RF switch
- eth0: no IPv6 routers present

thanks for yur help so far

---

### Post by alastair on 2005-02-28
When you say "XX:YY:XX" as a MAC hardware address - do you mean "AA:BB:CC:DD:EE:FF"?

i.e. my wireless card MAC is : 00:04:23:71:B4:58

Got via :

ifconfig eth0 

Look for "HWaddr".

The <AP MAC> I mention is the "HWaddr" (MAC) of the router itself (not your wireless) and will be of a similar format.

As for WEP key, I think there are a few ways to specify - I just do :

iwconfig eth0 key restricted <26 ASCII chars>

Yours is 13 characters? No idea.

---

### Post by iakudi on 2005-02-28
[QUOTE=alastair]When you say "XX:YY:XX" as a MAC hardware address - do you mean "AA:BB:CC:DD:EE:FF"?

i.e. my wireless card MAC is : 00:04:23:71:B4:58

Got via :

ifconfig eth0 

Look for "HWaddr".

The <AP MAC> I mention is the "HWaddr" (MAC) of the router itself (not your wireless) and will be of a similar format.

As for WEP key, I think there are a few ways to specify - I just do :

iwconfig eth0 key restricted <26 ASCII chars>

Yours is 13 characters? No idea.[/QUOTE]


Yeah I meant AA:BB:CC:DD:EE:FF

I did do 

iwconfig eth0 ap AA:BB:CC:DD:EE:FF     <==where AA:BB:CC:DD:EE:FF is of my AP

did you see my amended message above?

messages in syslog inc:

- eth0: Radio is disabled by RF switch
- eth0: no IPv6 routers present

my sys log also said that no subnetdeclaration for eth0 and that I need to write one in dhcpd.conf file???

---

### Post by alastair on 2005-02-28
This bothers me :

"eth0: Radio is disabled by RF switch"

It is a wireless "kill" button - either s/w or h/w i.e. a mechanism to turn off the wireless - wireless is disabled.

See the ipw2100 page :

[http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

"Issues" - "No packets! - RF kill switch"

To see :

cat /sys/bus/pci/drivers/ipw2100/*/rf_kill

If this is "1", then the wireless is switched off.

Then see :

[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

You have an Acer Travelmate C110i?

"For models with a software switch try the acerhk module:"

Do you have a s/w switch to turn the wireless on? or a h/w function key or button? or wireless? If nothing is obvious, you might want to try the module specified.

Good luck.

---

### Post by iakudi on 2005-02-28
will have a look...

my sys log also said that no subnetdeclaration for eth0 and that I need to write one in dhcpd.conf file???

this was "meant" to be easy !

---

### Post by alastair on 2005-02-28
I don't think you need a dhcpd.conf file - this is for a DHCP server. 

Perhaps you are running one by mistake?

---

### Post by iakudi on 2005-02-28
[QUOTE=alastair]I don't think you need a dhcpd.conf file - this is for a DHCP server. 

Perhaps you are running one by mistake?[/QUOTE]
 how do I check and stop a DHCP server?

Also I downloaded the acerhk files and exracted it, the instructions ask me to compile the driver, how do I dp that?

it does mention that I may need to modify KERNELSRC in the Makefile if autodetection does not work,.

One of the errors was that it could not find /lib/modules/2.6.8.1.-3-386/build/include/linux/version.h

as I dont have a build directory here...

---

### Post by alastair on 2005-03-01
DHCP server? See if something like "dhcpd" is running i.e.

ps ax | grep dhcp

(dhclient might be the dhcp client, not server)

If it is running, it might start from an "init" script under /etc/init.d. So ...

ls /etc/init.d/* |  grep dhcp

Anything?


To compile stuff, install "build-essential".

For linux kernel headers, use synaptic to search for something like "linux-headers" - and install the package that matches your kernel.

---

### Post by iakudi on 2005-03-01
I trie to look at:

cat /sys/bus/pci/drivers/ipw2100/*/rf_kill

and there is file called new_id and a link to a directory 0000:02:05.0

I followed the instructions to install the acerhk module but don't know what to do with it as it rather technical.

I still get an IPv6 tunnelling error on startup.

If I set my eth0 to DHCP (by the way I did have a server installed which I removed - in the end I did a clean re-install of ubuntu!) and I try to ifup it always refers to an unknown hardware sit0, when I ifconfgi that I get:

sit0         Link encap:IPv6-in-IPv4

and some messages fir RX and TX packets (all 0).

The dhcp listening fails.

When I try a manual IP address and ifup I get:

at first it just fails with 

SIOCADDRT: Network is unreachable 
Failed to bring up eth0

when I try it again:

Set failed on device eth0; Input/output error
SIOCADDRT: Network is unreachable
Failed to bring up eth0

Any ideas? I saw somethong on a website that suggested "disabling IPv6" completely???

thanks

---

### Post by alastair on 2005-03-01
sit0 should be OK - I have an ipw2100 and sit0 and have no problem. It is just another ethernet device (ipv4 in ipv6 tunnel device). It is not related to eth0 or wireless.

Inside the directory you mention "0000:02:05.0" is a file "rf_kill" - see what it contains i.e. "cat" it :

cat /sys/bus/pci/drivers/ipw2100/0000\:02\:05.0/rf_kill

Mine says "0" - if yours says "1", then this might be the problem - "radio" (wireless) is disabled.

If yours says "1", you could try putting "0" in it i.e.

sudo echo "0" > /sys/bus/pci/drivers/ipw2100/0000\:02\:05.0/rf_kill

Then "cat" to check it says "0" still ...

cat /sys/bus/pci/drivers/ipw2100/0000\:02\:05.0/rf_kill

Then retry the setup.

I am sorry you have felt the need to do a clean reinstall - this is almost always uneccessary. But now you need to star from the thread top and look at :

 - /var/log/syslog (eth0/ipw2100 load/init)
 - ifconfig -a
 - iwconfig
 - etc.

---

### Post by iakudi on 2005-03-01
I had a look and there is no rf_kill anywhere... what can I do next?

---

### Post by alastair on 2005-03-02
[QUOTE=iakudi]I had a look and there is no rf_kill anywhere... what can I do next?[/QUOTE]
 What if you list :

ls -l /sys/bus/pci/drivers/ipw2100/*/

Note the trailing "/" char.

I have :

```
root@muse:/home/alastair # ll /sys/bus/pci/drivers/ipw2100/*/
total 0
-r--r--r--  1 root root 4096 2005-03-02 08:13 bssinfo
-r--r--r--  1 root root 4096 2005-03-02 08:13 capability
...
-r--r--r--  1 root root 4096 2005-03-02 08:13 device
lrwxrwxrwx  1 root root    0 2005-03-02 08:13 driver -> ../../../../bus/pci/drivers/ipw2100
-rw-r--r--  1 root root 4096 2005-03-02 08:13 fatal_error
...
-r--r--r--  1 root root 4096 2005-03-02 08:13 resource
-rw-r--r--  1 root root 4096 2005-03-02 08:13 rf_kill
....
```

---

### Post by iakudi on 2005-03-02
This is nothing like what I get, I get the following:

ismail@ubuntu-tablet:~ $ ls -l /sys/bus/pci/drivers/ipw2100/*/
total 0
-r--r--r--    1 root     root         4096 2005-03-02 21:52 class
-rw-r--r--    1 root     root          256 2005-03-02 21:52 config
-rw-r--r--    1 root     root         4096 2005-03-02 21:52 detach_state
-r--r--r--    1 root     root         4096 2005-03-02 21:52 device
-r--r--r--    1 root     root         4096 2005-03-02 21:52 irq
drwxr-xr-x    2 root     root            0 2005-03-02 21:52 power
-r--r--r--    1 root     root         4096 2005-03-02 21:52 resource
-r--r--r--    1 root     root         4096 2005-03-02 21:52 subsystem_device
-r--r--r--    1 root     root         4096 2005-03-02 21:52 subsystem_vendor
-r--r--r--    1 root     root         4096 2005-03-02 21:52 vendor

How can the same (core) installation of Ubuntu be so different between you and me?

The main error that keeps cropping up with the RF switch is the lack of an IPv6 router....

when I compare everything via ifconfig -a all the other devices have an inet6 address bit not my wireless one...why?

cheers

---

### Post by alastair on 2005-03-02
What version of Ubuntu are you using? I only recently started using it - but installed a recent Hoary snapshot and have since tracked Hoary.

You have :

Intel(R) PRO/Wireless 2100 Network Dr iver, 0.53

(from your logs), but I have :

Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2

Mine seems to be built as part of the kernel I use (I have not explicitly installed it) - 2.6.10-4-386.

If you have the right build environment (kernel headers, "build essential" etc.), then you /could/ download the latest from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and build/install. This is what I used to do (update the driver) every now and then (pre-Ubuntu).

---

### Post by iakudi on 2005-03-02
[QUOTE=alastair]What version of Ubuntu are you using? I only recently started using it - but installed a recent Hoary snapshot and have since tracked Hoary.

You have :

Intel(R) PRO/Wireless 2100 Network Dr iver, 0.53

(from your logs), but I have :

Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2

Mine seems to be built as part of the kernel I use (I have not explicitly installed it) - 2.6.10-4-386.

If you have the right build environment (kernel headers, "build essential" etc.), then you /could/ download the latest from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and build/install. This is what I used to do (update the driver) every now and then (pre-Ubuntu).[/QUOTE]

I am using 2,6.1.8-3-386

Ok, so how do I update to your newer kernel?

That would be a great start....

also, I have been to this site but I get completly lost with all the distro's and versions, I know I sound stupid, but I am justhoping to learn...I am happy to get it wrong, re-install Ubuntu and try again until I get it right...

thanks

---

### Post by iakudi on 2005-03-02
[QUOTE=alastair]What version of Ubuntu are you using? I only recently started using it - but installed a recent Hoary snapshot and have since tracked Hoary.

You have :

Intel(R) PRO/Wireless 2100 Network Dr iver, 0.53

(from your logs), but I have :

Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2

Mine seems to be built as part of the kernel I use (I have not explicitly installed it) - 2.6.10-4-386.

If you have the right build environment (kernel headers, "build essential" etc.), then you /could/ download the latest from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and build/install. This is what I used to do (update the driver) every now and then (pre-Ubuntu).[/QUOTE]


I have downloaded the latest stable kernel,,2.6.11 from the kernel web page...

How do  I "update" my kernel? When you update your kernel, how does it affect all the other components that were installed along with the older kernel?

After I have installed the kernel, I was really hoping you could send me the IPW2100  driver you are using successfully and perhaps teach me how to install it...you can get me at [email]iakudi@lyos.co.uk[/email]

cheers

---

### Post by iakudi on 2005-03-02
I dont  wht I've done, but I 'm sure I installed a new kernel to 2.6.8.-5-386

and then applied ipw2100-1.0.2 from the website you mentioned...but now I have lost my wireless device altogether!!

I cannot fins it when I do iwconfig and it wont come up with ifup...I feel so useless

Looks like I'm going to have to re-install all over again as I have 2 kernel versions on my GRUB and non-working ipw2100...

Can you tell where you got your distribution from please? I was hoping to install the new version and not the 4.10 of UBUNTU from the website..

I really believed that this was the best and easiset to use.....as you can its 2.42 am..I have to be up by 7am...but this is so frustrating...

---

### Post by alastair on 2005-03-03
Downloaded from "kernel.org"? This might be premature.

Use "synaptic" - I assume you have used this - and use "search" for "linux-image".

See what kernel you are using :

uname -r

and look to see if there are later kernels available for install. Note - use the same arch (i.e. 386 or whatever).

If so, select it for install. Perhaps other things will be required (and you will be prompted).

As for other components - assuming no proprietary components (e.g. ATI, NVidia drivers etc.) it should not be a problem.

I cannot just send you a driver because it is tied to the kernel I use.

---

### Post by iakudi on 2005-03-03
I had a look around last night, and have downloaded and created an installation of Hoary 5.04, whoch I believe you are using. When i get home I am going to install this instead and see how it improves things.

What I find hard to understand is how in Linux do you "uninstall" something like you do in Windows if you installed something incorrectly. My failures have taught a lot more about Linux than I knew before !!

I'll let you know what happens later...

---

### Post by iakudi on 2005-03-03
I'm trying to install Hoary 5.04, but during the installation it tells me that eth0 appears to have been disabled by means of a physical "kill switch", and has asked me to switch it on if I want to use it...

I don't know how I can do this during the install, so I am assuming that I can do this after I install...maybe your previous messages may well work !

---

### Post by alastair on 2005-03-03
OK - it's a learning experience, for me as well (still, after almost 10 years of linux). But learning's good!

The Hoary install message is actually promising - it is noticing that your wireless is disabled.

Once installed, all we need to do is "cat" the rf_kill file to check, and then see if we can enable it.

---

### Post by iakudi on 2005-03-03
why me :(  ????

The snapshot I downloaded does not work, it gets to 80%  and then has problems, this then takes me intp a program calle Aptitude, I have been trying to work this out but its impossible, I want to try and deselect the faulty ones but cant do it !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

What version are you using? How can I foind out whoch Hoary version is stable?

---

### Post by alastair on 2005-03-03
I used a base of "array-4" install from the start of Feb.

If this is an installation problem, then it might be best to re-post in the "installation" forum. You need to describe the problem better though. Just because array-4 worked for me doesn't mean it'll work for you.

---

### Post by iakudi on 2005-03-03
Well I got a slightly earlier version of hoarty 5.04 - a few days..its installing perfectly so far but it did not come up with the message that eth0 is switched off.

I'll be on it in a few minutes and get back to you in a little while

PS. in the previous attemp i managed to get ut of adaptive and it booted up to gnome, but I discovered it had a problem with my copy of gnome-applet.

---

### Post by iakudi on 2005-03-03
wow...this new version is SO much better that before...

right wireless is switched off and my rf_kill file has a value of '2". I cant seem to change it...

---

### Post by alastair on 2005-03-03
From the ISSUES file in the ipw2100 source tree :

% cat /sys/bus/pci/drivers/ipw2100/*/rf_kill<br>

The reported values mean:

  0 = RF kill not enabled (radio on)
  1 = SW based RF kill active (radio off)
  2 = HW based RF kill active (radio off)
  3 = Both HW and SW RF kill active (radio off)


The ipw2100 driver can not control the state of the HW based RF 
switches.

For the latest progress on supporting various laptops, please go to the
RF Switch Project at [http://rfswitch.sf.net](http://rfswitch.sf.net).

Do you have a wireless/radio h/w switch or button anywhere?

---

### Post by iakudi on 2005-03-03
yes at the top of the keyboard, it does:

1 press - bluetooth
2 press - wireless
4 press - bluetooth AND wireless
4 press - off

I can almost feel it now !! do you know which package I need to install?

most of these are for non hardware ones, but there is a note from someone who has done one for a tablet pc (which is what I have, well its a tablet notebook)

---

### Post by alastair on 2005-03-04
What is the exact model of your laptop - "Acer Travelmate C110i" is the full model?

The ipw2100 cannot control the "HW based RF kill" - assuming your file still says "2".

Does the button not do anything in Linux? i.e. check "rf_kill" file, press button "2" -> no change in "rf_kill"?

What about the laptops BIOS screen at boot? Have you looked through that? Perhaps there is a setting to turn wireless on by default?

I doubt any s/w package can be installed to control a h/w switch ... 

[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

says that "For models with a software switch try the acerhk module" ...

---

### Post by alastair on 2005-03-04
I downloaded the C110 PDF users guide from Acer and had a look.

Assuming the special wireless button does NOT do anything in linux (see above post to check) ...

The "invilink" button to the left of the "P1" key on the laptop (special key) appears to pop open a windows program in windows to control wireless - not much help.

But there is also a program called "launch manager" in windows - which lets you set whether wireless or bluetooth are enabled or disabled on system start.

Do you still have windows on this machine? Try setting wireless "always on" and reboot - then check the "rf_kill" file again.

---

### Post by iakudi on 2005-03-04
Alistair thats a great idea..I will try that as well...but I got some nes for you..you will be impressed (lol)....I GOT IT TO WORK !!!!

I feel shattered as I was up till late BUT I have cracked it finally...

As you pointed out the wireless device is HW controlled which meant I no choice but get the acerhk driver, also the author Olaf Tauber was a great help (as have you been).

I got the driver and followed the advice Olaf emailed me, it created a new acerhk module and defined some new keys, this driver was for a laptop with just 4 hot keys, but my C110i is a tablet and has 8 hot keys, the 4 extra ones are used when I goto tablet mode. The acerhk module only mapped the 4 tablet keys, which do not include the wireless key, so it seemed like a dead end. Then I thought of using one of these tablet keys as the wireless key instead, i.e. assign it a different function.

It worked !! I now have a key that should be used for a tablet function but instead I have mapped it up as a wireless key.

So, when I switch my laptop on, the wireless light comes on but wireless is not activated. I do the following:

sudo ifdown eth0
modprobe acerhk.o
(this loads the wireless module and sets it up I think)
echo on > /proc/driver/acerhk/wirelessled
(this effectvely "switches" my wireless on as if I had pressed a key)
sudo ifup eth0
(as I am configured as dhcp, off it goes !!)

I have absolutely no problem doing this, after all the trouble I've had, but I just wonder if I will ever just be able to press my wireless button and launch it? But I sill not complain!! I will try activating wireless through the windows program...

Whilst trying to get my wireless functioning, I have become "good" as using the Synaptic app from the menu, as I learnt all the "little extra's" I need to be able to use the functions such as build or make menuconfig. My Openoffice 1.1 didnt work, so now I removed it and have v2.0 !

My next project (lol) once I have basked in this glory of my achievement is to work out why my sound is not working properly, when I put in a music cd, it will recognise the tunes etc. but neither of the 2 music players will "play" the songs and when I load a DVD the dvd app starts but never plays...the joy of Linux.

If I ever meet you and Olaf..I owe you a couple of pints !

---

### Post by alastair on 2005-03-04
Well done - bask in your acheivement for a while!

As for the audio and DVD stuff - do some research your self and then, if you get stuck, start a new thread in a forum.

Glad to be of help!

---

### Post by iakudi on 2005-03-04
[QUOTE=alastair]Well done - bask in your acheivement for a while!

As for the audio and DVD stuff - do some research your self and then, if you get stuck, start a new thread in a forum.

Glad to be of help![/QUOTE]
 As a sign off...setting the wireless to be on via the Bios is perfect. 

As soon as it logs on its connected !!!

---

