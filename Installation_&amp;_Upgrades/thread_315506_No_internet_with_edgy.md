---
title: "No internet with edgy"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by adana on 2006-12-09
I had ubuntu breezy installed on my laptop working well. I did a complete reinstall with Edgy using official downloaded CD and now have no internet connection.

Ifconfig list only lo. No etho. I cannot ping any ip except 127.0.0.1.

Any advice? I've installed ubuntu many times and this has never happened.

---

### Post by bscbrit on 2006-12-09
Can you give us some details of the hardware please?

---

### Post by adana on 2006-12-09
Thanks for the response! 

Gateway solo
creditCard Ethernet 10/100 + modem 56
512M

Not sure what else to provide.

---

### Post by bscbrit on 2006-12-09
I don't recognise any of the hardware, but that doesn't mean much.  What might be sold under one brand name in one country might have a completely different name in another.

Was the network connected while you did the upgrade?  Usually, Ubuntu does a pretty good job of recognising hardware, which should have been even more likely as it appears to have recognised it earlier under Breezy.

I cannot recommend which driver to install as I do not know the hardware.  Does the ethernet card emulate a more common type of card?  I'm going to do some searching on the internet to see if I can find any clues.

If anyone else reads this and has some bright ideas - please feel free to chip in!

---

### Post by bscbrit on 2006-12-09
If you run the Live CD again, does it recognise your ethernet connection.  If it does, can you please tell me what make/model it believes it is and which driver it has used?

---

### Post by adana on 2006-12-09
Interesting idea! No, when I boot with the CD it doesn't connect to the internet, so I guess it didn't during the install. Bummer, I never thought to check that before installing!

---

### Post by adana on 2006-12-09
Very interesting. If I pop that "creditcard" ethernet card  out and plug it back in, ubuntu auto configures it within 1 minute and I am on the internet. If I reboot, it's gone and I have to pop it out again.

So I have to figure out how what config files might have those settings.

Any ideas?

---

### Post by bscbrit on 2006-12-10
No - I've not noticed this behaviour before.  But at least you have a short-term solution.  Do you have network-manager installed?  It sounds like you might have, in which case it is doing precisely what it is meant to do...

But, the best I can offer is to look at the configuration files before and after inserting the card to see what is changing.  A quick search of /etc will probably identify all the files that have changed in the last 30 secs or so, and that will give you a starting place.

Secondly, once the card is working, make details of its make, model and any other relevant information.  Write it in your programmers' notebook (now you know why you need one!) and transfer the details to your network configuration files to see if you can get the settings to stick permanently.

---

### Post by Bill007 on 2006-12-10
Kia ora all

Sorry to jump in here, I have a server with two network interface cards eth0 and  eth1 , when I reboot eth1 fails to configure everytime even after I set a directive in the boot directory, so I have to manualy re configure the card:

 check **root@production:#  ifconfig** gives all the details of network interfaces 

configure eth1 or eth0 just change the number to suit
**root@production:# ifup eth1** 

Then check again **root@production:#  ifconfig**

I only have the command line if you can access it try the above 

 maybe its a small bug

Regards Bill007;)

---

### Post by bscbrit on 2006-12-10
Bill007 - thanks for the input.

The original problem was that the ethernet card wasn't being recognised. We still haven't quite fixed that but at least we have a short-term fix.

Once it is recognised, we will see if it configures automagically at boot time.

---

### Post by Bill007 on 2006-12-10
Well that makes it real hard to configure the eth0 card sorry

but cant you maually set up in

**sudo nano /etc/network/interfaces**

# The loopback network interface

auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

iface eth1 inet static
address 192.168.2.100
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0
# No gateway needed for this eth interface

---

### Post by bscbrit on 2006-12-10
Bill007 - yes we could, but as it wasn't recognised during the installation we were not sure which drivers had to be installed to make it work.  It is a make and model that I did not recognise.  However, during our experiments to try to identify it the OP discovered that, if he removed the card and reinserted it, Ubuntu configured it automatically.

Now I want to identify exactly which make and model Ubuntu thinks that it is - and then we can configure the interfaces to recognise it immediately.

My logic might be convoluted - but at least I thought I knew where I was trying to go :-k 

I've asked the OP to make a note of how the card is configured - 1) so that we can solve this problem, and 2) so that we can let other card users know in the event that they also experience a problem in the future. 

Stick around Bill, I'm probably going to need / be grateful for your assistance once I have collected enough information to move forward.

---

### Post by Bill007 on 2006-12-10
sure I have been thru hell with linux and love to try and solve problems and there have been a few

Ill be up late Sunday in NEW ZEALAND what else to do 

Hey when you get the card going adana

I beleive you can get the net  by re inserting it, correct or am I wrong here

can you run some checks on it

ifconfig for a start 

or thru you visual interface (dont much about the visual set up if some one could step in here)

get back soon

---

### Post by Bill007 on 2006-12-10
how ever you can do this thru the command line or graphical interface

set you card up like this 

**nano /etc/network/interfaces**  name of config file


# The primary network interface
auto eth0
iface eth0 inet dhcp


This will set the config up on the eth0 card

save and xit

**ifup eth0**

it should stick

---

### Post by adana on 2006-12-10
Wow, thanks for the replies!

I saved my /etc/network/interfaces file after rebooting and did a "diff" after popping the network card out/in. Surprisingly, my /etc/network/interfaces file is identical before and after.

 Here it is:

adana@adana-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

##################################################################

I don't know exactly how to tell what card ubuntu thinks I have but looking in the device manager , it says under the advanced tab:

info.vendor: strlist Xircom
info.linux.driver strlist xirc2ps_cs
info.bus strlist pcmcia
info.product strlist CreditCard Ethernet 10/100 + 
modem 56

I would be happy to get you any more information you need; just let me know where to find it.

Thanks!

---

### Post by adana on 2006-12-10
I uploaded 2 screenshots from the device manager showing the "networking interface" entry that appears after I pop out/in the network card.

---

### Post by Bill007 on 2006-12-11
Its Been a big day:) 

So every thing looks fine here I know its a pain but at least you can get going for the moment Im sure Ive heard of it before and I suffer it but only on my second eth card when I reboot the server which isnt a lot

Sorry cant do much from here what about one last thing can you set up your boot file to include the  **ifup eth0** command on boot or just plain ole boot ya eth card in the backside on start up not familar with the graphical interface but some googling will help

Bill007

---

