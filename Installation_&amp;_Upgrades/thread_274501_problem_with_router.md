---
title: "problem with router"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by troubl3dmind on 2006-10-09
I have a frustrating situation on my hands.  Me and my sister both have computers right next to eachother in my house.  Her computer didn't work for a while, so i had the internet directly connected to my computer.  We got her computer fixed, and are trying to connect them both to the internet through a linksys wireless-g router.  The problem is that i don't have much experience with linux, and that's what my computer has on it.  My sister has xp on hers.  How can i connect them both to the router?  I have the install disc, but it still won't install the router on my sister's computer, and running the disc on mine is pointless because it's a windows disc.  Can anyone help me configure this router?

---

### Post by Mr Frosti on 2006-10-09
The only thing the installation disc will do is provide a nice walk through of the configuration process for your router's settings. If you are more comfortable with Windows XP, you can use your sister's machine to verify that the router is working properly. If you are using wireless on the router, you can check this as well. Once you have verified that access through the router  is working, you can duplicate these settings on your machine.

You can do this by using the "Network Monitor" icon in your Gnome panel. Click on this and change your device by using the "Configure" button. You can setup the wireless network name and password (if any) in this dialog. Place a check next to the connection to "bring it up". This should connect you to the Internet.

You can verify your IP address by clicking on "Support" and reading your address information.

---

### Post by Eran on 2006-10-09
Let me see if I got it correctly: the trouble is to connect both computers through the Linksys router to the net? In that case, don't worry, there is nothing special to install. 

**First, the router** - is it configured to connect to the Internet already? On the LAN / wireless LAN side - is it configured to work as a DHCP server?

How do the computers connect to the router? Do you need to install the wireless card on both computers?

**On your computer,** and assuming that the network card is already installed and recognized, you should enable DHCP client. Go to 'system' > 'administration' > 'networking' and  to your Ethernet connection. Make sure that it does not have any statically configured IP address. Instead, it should state 'DHCP'.

**On your sister's computer** you should do the same (by default after new installation it should be like that. If not, do it in network properties).

Theoretically, if the router is connected to the net, both computers are connected as well. Does it work?

---

### Post by troubl3dmind on 2006-10-09
I'm sorry, the way i asked the question might have been misleading.  I'm not trying to connect wirelessly.  I'm simply trying to connect the router to the two computers which are but 5 feet away from eachother.  The router is on the floor inbetween the tables.  As for the DHCP.... i'm not sure quite what the means but it says nothing about it on the router, and as far as i know i didn't see anything about it trying to install it.  Hopefully this is just for the wireless g cards, and not for just connecting to it with wires.

---

### Post by troubl3dmind on 2006-10-09
btw... network monitor?  I'm not sure how to get to this.  Is the gnome panel just the main menu?  If so, how do you get to network monitor.

Another thing is that i am on my sister's computer right now because since i tried to configure the router i can't directly connect to the internet from my computer... only hers.  So if i want to read the forum i can't connect the router because it doesn't work.... dunno if that helps but just thought you should know

-Thanks

---

### Post by Eran on 2006-10-10
Ok, let's start with your Linux PC (of course). Did you go as I told you to: 'system' > 'administration' > 'networking'?

Do you see your Ethernet card listed there? click on that and tell us what you see in the Ethernet card configuration.

As for your connection to the Internet service provider - do you know how you connect your router? Is the router already connected and properly configured for that?

---

### Post by PriceChild on 2006-10-10
If you're connecting via ethernet it should be simple :D

System>Administration>Networking

If your ethernet card is listed, click it, then click configure.
Select the "enable this connection" box. You will then be able to make sure that it is set to DHCP (Automatic Configuration) as opposed to Static IP.

Press ok, let it think a while.

Then activate the connection using the gui you're left with :)

---

### Post by troubl3dmind on 2006-10-10
My router is already configured for the internet connection... well not right now, cuz i have to be on the internet.  But i plugged the modem in and connected all the wires, then went into networking and the card was already configured.  I disabled it, and then hit configure.  It sat there for a minute then told me that it was configured.  Clicked the internet icon... nothing.

I know it's not with the way i set the router up, because i've done it many times before.  It's just been a long time since the last time i installed the software for the router.  Could this be because i'm using linux?

And one more thing, when i install the router on one of the PCs, is it going to install the router on both?

---

### Post by dannyboy79 on 2006-10-10
i don't think you really understand what a router does. the cd that came with the router doesn't INSTALL the router on the computer. all it does is allow a gui for you to "setup" the routers config options. if you are hooked up the router using an ethernet cable from your linux box to the router you should have no problem getting on the internet. but we need to first make sure that you are getting an ip address. so do me a favor and let me know what ifconfig  gives back when you type it into a terminal session. lets start there.

---

### Post by troubl3dmind on 2006-10-10
let me just say that i know how to configure a router.  I posted this question online because the router is not working.  I know that the disc is only a way of making installing it easier, the reason i tried to use the disc is because i don't know the hard way to do it. ( again... the reason i posted this question )  I'm positive i've connected the routers to the computer correct, but the router **still** is not working.

The 2nd part i don't think you're understand is that i cannot look at this forum with the router connected.  I have to run the internet directly into my sister's computer to get online and look at this forum.  I do'nt know if this matters.

When i type ifconfig into the terminal it says:

eth0   Link encap:Ethernet  HWaddr 00:40:2B:69:49:CE
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (o.o b) TX bytes:0 (o.o b)
Interrupt:209 Base address:0x2000

lo    Link encap:Local Loopback
inet addr:127.0.0.Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

once again, this is not my first outing with routers.  I'm posting this question because it is not working, and i have it connected correctly.  I know what a router does, i know that if i have it connected it should be running the internet, but it's not; that's the reason for this post.

---

### Post by troubl3dmind on 2006-10-10
let me just say that i know how to configure a router.  I posted this question online because the router is not working.  I know that the disc is only a way of making installing it easier, the reason i tried to use the disc is because i don't know the hard way to do it. ( again... the reason i posted this question )  I'm positive i've connected the routers to the computer correct, but the router **still** is not working.

The 2nd part i don't think you're understand is that i cannot look at this forum with the router connected.  I have to run the internet directly into my sister's computer to get online and look at this forum.  I do'nt know if this matters.

When i type ifconfig into the terminal it says:

eth0   Link encap:Ethernet  HWaddr 00:40:2B:69:49:CE
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (o.o b) TX bytes:0 (o.o b)
Interrupt:209 Base address:0x2000

lo    Link encap:Local Loopback
inet addr:127.0.0.Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

once again, this is not my first outing with routers.  I'm posting this question because it is not working, and i have it connected correctly.  I know what a router does, i know that if i have it connected it should be running the internet, but it's not; that's the reason for this post.

---

### Post by dannyboy79 on 2006-10-10
let me say that the reason i stated that i didn't think you knew what a router did was because you stated over and over that you wanted to install the router into the computer and that doesn't occur.

we want to 1st verify that the router is working, so first lets hook up the router to the windows box and go thru the configuration of it and set it up to be a dhcp server (this means that it will hand out ip addresses to all the computers that are hooked up to it). if your windows box ends up being able to connect to the internet thru the router than we know the router works. what ip does therouter get whn you go theu the config of it? what does ipconfig give you on the windows box?

most routers have a dhcp server setup by default but if  you didn't see that option when going thru the config than we need to log in to your router thru the windows machine after you config it to work with the router and go to ie and type in either 192.168.0.1 or 192.168.1.1 and if it asks for a username and a password type them in there. if you don't know them then sometimes they are admin and password for the username and password, if that's not it and you don't remember what they are we need to gogle and find out what the default settings are for your exact model number. after we make sure the router is setup to be a dhcp server we will then hook up a ethernet cord from the router to the ubuntu box and wait a minute. then again see if you can ge on internet. if not, than please post your ifconfig from linux. 

it appears from the last time you posted your ifconfig you are not getting a ip address from the router and that's why you can't get on the internet! check out my ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:12:13:6C
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe12:136c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:856694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1238320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:75169632 (71.6 MiB)  TX bytes:1329109816 (1.2 GiB)
          Interrupt:225 Base address:0xe200

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

notice the inet addr:192.168.0.3


 Can you please post the output of lspci -v. we need to see what kind of ethernet card we are dealing with. also please post the output of cat /etc/network/interfaces. we'll go from there.

if you get an ip within ifconfig and you still can't get on try the following.

In the firefox address/URL space type "about:config" , scroll down to network.dns.disableIPV6 = false ,double click this line to change it to true.
In the above do NOT type in any quotes.

The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:

Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases

Look for the line that reads:
alias net-pf-10 ipv6

Change it to:
alias net-pf-10 off #ipv6

Save and reboot your PC.

---

### Post by troubl3dmind on 2006-10-13
When i do ifconfig there is no ip address in the first paragraph,jbut in the second paragraph sis says inet addr:127.0.0.1 Mask:255.0.0.0

When i do lspci -v it says it's detecting the ethernet controller.

---

### Post by dannyboy79 on 2006-10-13
What does it say aboutthe ethernet controller, it should be instantanious. lspci -v should output all the info about the pci interfaces in your box. did you get my email?

---

### Post by troubl3dmind on 2006-10-13
Yes i got your email.  The information about the router is:

0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Trigam Computer Inc. Unknown device 3189
Flags:bus master, medium devsel, latency 64, IRQ 217
I/O ports at 2000 [size=256]
Memory at e8100000 (32-bit, non-prefetchable) [size=256]
Capabilities: <available only to root>

---

### Post by dannyboy79 on 2006-10-13
> **troubl3dmind said:**
> Yes i got your email.  The information about the router is:

0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Trigam Computer Inc. Unknown device 3189
Flags:bus master, medium devsel, latency 64, IRQ 217
I/O ports at 2000 [size=256]
Memory at e8100000 (32-bit, non-prefetchable) [size=256]
Capabilities: <available only to root>

my screen name is new2linx, i installed gaim and typed in your name in my buddy list so when you get on i'll see ya and can help.
after searching the ubuntu forums and find only 2 other references to your ethernet controller and both state that they're having problems getting online so i'll see whayt I can do abouit this.
apparent;y i have found that slckware 8139too is the module that has ben working for slackware so hopefully that module is in ubuntu

---

