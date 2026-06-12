---
title: "How to unintstall ubuntu, completely reformat hard drive"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Lakeside5 on 2010-08-22
I installed ubuntu using a flash stick and I must have done it wrong as I cannot get access to the internet (to install more stuff)so I have to start over. I have searched but still don't know how to do it. Do I         delete all the ubuntu files on mhy flash stick and then insert it in the drive or do I enter something at the command line? thanks for any help.

---

### Post by grief -l on 2010-08-22
If your install was sucessful and you have a functional desktop then there's no need to delete anything. You just need to configure your Network Interface.

Let us know whether it's dialup-modem, ethernet or wireless and whether it's built-in, pci, or USB. If you don't know open a Terminal and type in ```
ifconfig
``` then Copy the output and Paste it here.

---

### Post by Lakeside5 on 2010-08-22
I have two computers.  The one I am talking to you right now is a laptop with windows 7 installed (it came that way lol) which is connected to high speed dsl wirelessly to a home network I set up. The other is a desktop connected to the router with a cable, to the same network. I typed ifconfig at the ubuntu command prompt and cannot cut and paste to here but if you tell me what to look for in the output perhaps...there was so much stuff lol  thanks. I'm thinking I messed up while installing, there was something about configuring the network, and it wouldn't let me go on if I didn't enter and address, so I entered the router address  192.168.1.1 but probably the last number should have been .100, or maybe I should have put 127.0.0.1 (as shown for my 'inet address' under lo for the output,  and also I put for the mask 233.233.233.1 but here it shows 255.0.0.0 instead. I have always had trouble figuring what they want for these addresses.

---

### Post by Lakeside5 on 2010-08-22
I don't know how to configure my network interface. I've read some posts regarding that, but I would appreciate a little help, maybe step by step? I'm mjst looking at a command prompt, and wondering what to do. thanks.

---

### Post by grief -l on 2010-08-23
for the desktop, goto the network applet on the right of your top toolbar (next to the date and right-click on it. Click "edit connections" and in the tab that pops up goto "wired", select eth0 and hit "edit" on the right.

It should have a MAC address already filled in, and MTU set to Automatic. Click 802.1x security and make sure that it is NOT checked. Click IPV4 settings and set it to "Automatic DHCP". Click IPV6 and choose "Ignore". Done, so click "Apply".

Try to log on with a browser

---

### Post by Lakeside5 on 2010-08-23
I'm still trying to understand you lol  he computer I'm posting in this forum on is a laptop with WINDOWS and the computer I'm trying to configure is a desktop, that right now only gives me the command prompt, as I only installed the bare bones server off a flash drive. So...there is nothing to 'go to' or click, and I'm wondering how to proceed, as it keeps telling me it can't 'resolve that address' (for ANYTHING I type in after wget..) I have to tyupe in some kind of command there I guess, to fix the mess I must have made when installing it, like entering the wrong ip address or something.  Can anyon help? thanks

---

### Post by Lakeside5 on 2010-08-23
grief-1, are you asking me to edit something with the computer  I'm on NOW? (the windows laptop) If so I will have to use a windows command, and I'm not so familiar with windows anymore, having been with Linux for a bit. It seems I do both...not so well lol. This laptop is connected to my network wirelessly, but is probably the 'main' computer so I should maybe use it to edit connections?

---

### Post by oldfred on 2010-08-23
Can you plug your laptop into the network with an Ethernet cable just to finish the setup. It updates faster and often you need to download a wireless driver.

Was there some reason to install a minimal server on the desktop? You can configure everything from the command line.

---

### Post by Lakeside5 on 2010-08-23
Thanks for your patience with me :)  I will plug my laptop into the router (keep in mind I have Windows on this laptop, not linux.) so then what do I do? I kind of need to know 'step by step'  thanks.  As for the install,  I just downloaded the latest 10.04 server edition, with no gui.  I don' know if it is 'minimal' or not, it just came that way, with no gui, just shows a command prompt. I read that the simpler the server the less security risks, and that having a gui etc. gives more vulnerability.

---

### Post by 10snoopy1 on 2010-08-23
> **Lakeside5 said:**
> I have two computers.  The one I am talking to you right now is a laptop with windows 7 installed (it came that way lol) which is connected to high speed dsl wirelessly to a home network I set up. The other is a desktop connected to the router with a cable, to the same network. I typed ifconfig at the ubuntu command prompt and cannot cut and paste to here but if you tell me what to look for in the output perhaps...there was so much stuff lol  thanks. I'm thinking I messed up while installing, there was something about configuring the network, and it wouldn't let me go on if I didn't enter and address, so I entered the router address  192.168.1.1 but probably the last number should have been .100, or maybe I should have put 127.0.0.1 (as shown for my 'inet address' under lo for the output,  and also I put for the mask 233.233.233.1 but here it shows 255.0.0.0 instead. I have always had trouble figuring what they want for these addresses.


If it is a laptop, you should try clicking on the network applet (up by the audio applet) and if you find the network, connect to it. 

Hope that helps.

---

### Post by pricetech on 2010-08-23
Check out the help on the Ubuntu site.  What you'll need to do is set your IP address using the command line.

In order to know, or at least guess, what IP you want to use, open a command prompt on your windows laptop and type "ipconfig /all" without the quotes.  That will tell you what IP your router is assigning to your laptop.  Use an IP address that's close to what's assigned to your laptop, then use the same numbers for Subnet Mask, Gateway, and DNS.

For example, lets say that typing the command in windows yields:
192.168.0.2 for an IP
255.255.255.0 for a Subnet Mask
192.168.0.1 for a gateway
Assign 192.168.0.11 to your desktop and use identical numbers for Subnet and Gateway.

You'll also want to match the DNS addresses exactly.

That should get you connected.  Once you do get connected, you'll probably want to install at least a minimal desktop environment to help you along until you get comfortable with working from a command line.

---

### Post by Lakeside5 on 2010-08-23
> **10snoopy1 said:**
> If it is a laptop, you should try clicking on the network applet (up by the audio applet) and if you find the network, connect to it. 

Hope that helps.

I'm not sure what you mean by 'applet'  Physicall on the laptop itself, above the keyboard area, thare is a light I can click to mute the audio (left side) way over on the right is another light for that says it is my 'hp wireless assisstant' Can only turn wifi on and off with it though. The icons on the bottom of my screen (battery life, speaker icon etc.) include 'internet access' so I clicked on it, right clicked on the wireles connection I set up, went to properties, status and then was lost lol. The box that says 'configure' is greyed out for some reason so I can't click on it. But if I put an x in the box that says 'enable wlan connection settings' then that box is clickable. *edit*  hmmm just for the heck of it I put an x in that box and then clicked the 'configure' button and it said 'cisco compatible eXtensions connections settings enabled' Under 'properties' it says something about ipv6 not being enabled

---

### Post by Lakeside5 on 2010-08-23
Pricetech, I just saw your post. Thank you, I am going out but will try that as soon as I get back! It looks fairly straightforward and I hope it works :) thaks again and to everyone else too.  Great forum!

---

### Post by grief -l on 2010-08-23
You need to download and install the the 10.04 desktop, not the server. At this stage you don't know enough about the command line to get done what you want to do. Believe me, you don't have to worry at all about vulnerabilities (other than you, the user LOL).   Once you have a desktop set up on one of your boxes you can start messing around with servers and such. The next few weeks you will be very busy sorting out hardware issues (unless you're very lucky!), so you need a working box, with ubuntu on it, so you can follow instructions, experiment and learn.

---

### Post by 10snoopy1 on 2010-08-23
> **grief -l said:**
> You need to download and install the the 10.04 desktop, not the server. At this stage you don't know enough about the command line to get done what you want to do. Believe me, you don't have to worry at all about vulnerabilities (other than you, the user LOL).   Once you have a desktop set up on one of your boxes you can start messing around with servers and such. The next few weeks you will be very busy sorting out hardware issues (unless you're very lucky!), so you need a working box, with ubuntu on it, so you can follow instructions, experiment and learn.

And to add to that, it is best if you use the desktop edition even if it is a netbook.

---

### Post by Lakeside5 on 2010-08-23
Hmmmm...maybe I will try that, the desktop, I kind of miss the gui lol So, I will take my usb stick and erease/format it, and replace it with the desktop 10.04 and reboot the computer with this in the usb port and it will start installing this on the computer? I hope so.
*edit* Well here I go again, I can't remember if it's a 32bit ot 64 bit but I am going to download the 32 bit as it says it is recommended for most computers. I guess if it is I will find out when I try to use it. I was going to use the advice of assigning numbers in the command line but I don't know how to do that :)

---

### Post by Lakeside5 on 2010-08-29
I've just installed the 10.04 desktop ubuntu on my hard drive and I ahave a purple screen with the 'applications places settings menu at the top and nothing else on the desktop or anything so basically normal lol  Now I'm wondering what packages to install to make it into a server, and also how to make it secure this time so I diont get hacked again! I would go into the terminal (applications...) but then what? Please help thanks.

---

### Post by Lakeside5 on 2010-08-29
I was given advice before when I was trying to install the server edition and needed to configure the network, but I thought I would ask again in the case of having the desktop version installled. I just went to applications>internet and of course I can't access any web sites as it is not connecting to the network. Now I have to go into the terminal and do it but how? any help greatly appreciated thanks

---

### Post by oldfred on 2010-08-29
Do you have it plugged into a Ethernet port. Sometimes you have to use hardwired initially.

System, Preferences, Network connections. You should see auto eth0 if you have a hard wired set up and connection to your router. If not connect it and then add if necessary. If you have arth0 you can edit to see your config. Look under the IPv4 tab. If you want to change from DHCP to fixed this is where you would do it.

---

### Post by Lakeside5 on 2010-08-30
Yes I do have auto eth0 and did exactly as you said and entered the exact numbers and where you have them in the diagram in your post. Thanks for the post too and the diagram.  Now I do have a new connection in the list called auto eth0 and it says connection established but I still can't connect to the internet for some reason, maybe I have to change the numbers a bit?  192.168.1.1 IS my router address, and the 255.255.255.0 is the mask (not sure about the other one) so I don't know why it won't connect. *edit* I used ipconfig at the windows command prompt on this laptop (it is connected wirelessly to the router) and I entered the values to edit the auto eht0, it was close to what you had, only adddress was .100 not .20 at the end. A connection ID established, just it won't connect to the internet.*edit* Last edit I promise, I did ifconfig in the ubuntu terminal and the numbers were slightly different, where 'gateway' was called 'bcast' and was 192.168.1.255 so I edited the connection again for that but still can't 'surf' lol.  Also, when I save the numbers, they don't seem to stay, the gateway changes to all 0's. Every time I go in to edit, I have to enter the numbers all over again.

---

### Post by oldfred on 2010-08-30
Back when I had to set up ethernet ports all manually and was a newby with ethernet, I accidently used the same address for two computers. For days things worked then we had problems. It turned out one PC or the other was not on and it worked but as soon as one was turned on the second would not work.

You DHCP has in effect assigned the default range. Most routers use 100-150 as the preassigned range and therefore you cannot use any of those numbers. Try anything but 100 thru 150 or check your routers documentation for what range is uses.

---

### Post by Lakeside5 on 2010-08-30
Thanks, I'll try right now :)

---

### Post by Lakeside5 on 2010-08-31
I followed your advice, entered all the values that I got from the laptop computer, just changed the ip address to 192.168.1.156, because the laptop one was 192.168.1.100. It shows that a connection is established, but I still can't sruf the net, strange. Another odd thing, when I enter the ip address, netmask etc. it asks me to enter my password and when I click the box to do so, the numbers where I had the 'gateway' (192.168.1.1 all turn back to 000.000.000.000 and don't stay.

---

### Post by oldfred on 2010-08-31
If you log in to your router what range is pre assigned to DHCP?

---

### Post by Lakeside5 on 2010-08-31
Oldfred, it is just as you said, the DHCP range is 192.168.1-149 (the laptop that is connected wirelessly) So I tried assigning the ubuntu box, 192.168.1.160, or .....200 etc. but that didn't work.

---

### Post by oldfred on 2010-09-01
Back to post #2.

Post results of 

ifconfig

but hide the hw address, I do not think that should ever be posted. Even though mine is spoofed from my old computer so comcast did not see me plugging in two computers before I had a router (20min wait to reset). Now my router has that same HW address.

HWaddr 00:00:00:00:00:00

---

### Post by vicgclemente on 2010-09-01
Hi there!

I have Ubuntu 10.04 installed on my laptop. It is the only operating system present. Now my problem is, I have to uninstall it and re-install later after a Windows OS is installed. That means I want to have a dual-boot system. How do I start?

Thanks for the support... :D

---

### Post by Lakeside5 on 2010-09-01
I'm assuming you want the output of ifconfig from my Ubuntu maching (where 10.04 is installed) not the windows laptop. Well of course there is a lot of output and I cannot cut and paste this won't be the whole ouptut but here it is:  **intet addr** 192.168.1.156   bcast: 192.168.1.255: (I'm assuming 'bcast' is 'gateway', the windows ipconfig shows 'gateway' but ubuntu shows bcast)   Mask is the same: 255.255.255.0  So are these the numbers I would put in for ip addr, subnet mask and gateway?  EDIT I applied those numbers, and although I have a network connection that says it is active, I still cannot access any websites. :(

---

### Post by oldfred on 2010-09-01
Some others that know more than I talk about the DNS nameservers, but on my system that is configured on the router. 

google ip should ping 3 times
ping -c3 74.125.39.106


and what does this file have:

/etc/resolv.conf

should have domain, search & nameservers

---

### Post by Lakeside5 on 2010-09-01
Wow, still lots I don't know, because I wasn't sure what you meant by some of that. I went to the ubuntu desktop terminal and entered 
ping -c3 74.125.39.106 and it said 'Network is unreachable'. 
Also there is no resolve.conf but there is an  etc/resolvconf which has a folder 'update-libc.d' which has avahi-daemon in it, and no mention of what you mentioned.

---

### Post by oldfred on 2010-09-01
resolv.conf is a file not the folder.

I have comcast but this was autocreated:

# Generated by NetworkManager
domain hsd1.il.comcast.net.
search hsd1.il.comcast.net.
nameserver 68.87.72.134
nameserver 68.87.77.134

When I look at my router all these are settings in the router:

Router calls domain as domain name
Search not shown but it looks like it is the same as Domain
Router calls nameserver DNS1 & DNS2

I think you should try creating a file and copy your data from your router into it.

sudo nano /etc/resolv.conf

Copy my data and change to your domain & dns.

You can also use google's dns
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)
Configure your network settings to use the IP addresses 8.8.8.8 and 8.8.4.4 as your DNS servers or
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

### Post by Lakeside5 on 2010-09-03
Thanks for the reply. I went into my router,and did see the nameserver numbers. Both start with  216... However I looked all over for something saying 'domain' or 'search' and did not see it, i saw 'domain name' and it was blank. Also, how do I create the file called 'resolv.conf'? I know, by not I should at least know how to do that.. thank you again

---

### Post by oldfred on 2010-09-03
That your domain is blank in your router may be the problem?

Your router should be getting that info from your provider using DHCP.

This was my entire resolv.conf but is based on my comcast provider in this area.

# Generated by NetworkManager
domain hsd1.il.comcast.net.
search hsd1.il.comcast.net.
nameserver 68.87.72.134
nameserver 68.87.77.134

---

### Post by Lakeside5 on 2010-09-03
I appreciate your continued support.  So you're saying  (because I'm trying to understand :) that normally, after installing and creating a network connection, there is a file existing such as yours (resolv.conf..but for some reason I have t create this file) and that file contains the info you showed, which is generatd by your service provider who also should provide DHCP, and that same info is usually in the router too?  For some reason I didn't have that file, also my domain name is blank in the router.  Do I hav to  call my isp and ask what's up? What should I do? thanks.

---

### Post by oldfred on 2010-09-03
Is your service provider using DHCP? Some my still use hardcoded IPs.

If you have hardcoded they would provide that data. Otherwise I think it all comes from DHCP. I have not done any maintenance to add that info on my system.

---

### Post by Lakeside5 on 2010-09-03
Helpdesk guy at my isp said they use DHCP, and he thinks it's weird that there is no 'gateway' showing when I ifconfig (I had mistakenly thought that 'Bcast' was Ubuntu's name for 'gateway'  but my ifconfig does not yeild a gateway.  so he thinks that there is an issue in my machine or install or whatever that is 'hiding' the gateway?  I get to call hin back in an hour and a half. he's going to install ubuntu on his machine and 'play around with it' (he'd treid to before and gotten frustrated lol) So if nothing else I've succeeded in calling another ubuntuite back into the fold :)
*edit* Well, he spent a long time trying lots of stuff, and in the end, from process of elimination from all of this (I was still 'connected' but couldn't surf the net) he thinks maybe I need a new ethernet card in the back of that computer which may be possible.  It wasn't replaced since the box was built about 4 years ago! I will try that and let you know.  Also, if i decide to get rid of this install and start over, would I just download/install another distro onto that flash stick and then install it over the current one? thanks

---

### Post by Lakeside5 on 2010-09-06
Here is just a respons I had locally that I thought I would share,  someone here had an idea too about what my roblem is. I think this forum had already addressed this though, and I have been assigning as such.
' I am going to 'guess' that the problem is with your router configuration. I am not sure if you are using your router for DCHP or not. It sounds to me that you are trying to statically assign your other computers.
You could (should) use DHCP on your router. However, IF you statically assign your computers IP addresses you need 3 things.
1) An IP address on the same network and subnet.
2) A default gateway (the IP address of your router)
3) DNS lookup IP assignments (from your ISP prvider or any other DNS sevice)
Those three things (if your router is NATting and you have conectivety) should get you surfing the internet.

---

