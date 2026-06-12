---
title: "Drivers for Belkin Wireless G Notebook Card"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-05-06
Hi all,

Are there drivers (linux, not ndiswrapper) for the Belkin Wireless G Notebook Card Model f5d7010 ver 7000uk? It's currently showing up on Feisty as:
```
16:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
```
I've read around and it looked like rt2500 or rtl818x would be good choices, rtl818x won't build, the makefile spits out all sorts of errors, rt2500 will build if I tweak it a bit but no new interfaces are showing up.

NB: avoiding ndiswrapper like the plague, it doesn't support packet injection.

Thanks for your advice,

Quark_77

---

### Post by phillipchandler1 on 2007-05-29
Hiya

I have the Belkin 54g F5D7010 Ver 7 card, which Im using under 7.04 and it woks perfect.

If you goto [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) 

which is the ndiswrapper site listing for all cards starting with "B", and go down to card 46, it will guide you to [http://www.realtek.com.tw/](http://www.realtek.com.tw/)  to download the drivers for the L8185, which when unzipped will give you the 3 net8185 files.
NDiswrapper then gives the full details of installing the driver, which is below for you :

There will be 3 files net8185.inf net8185.sys net8185.cat.
Open a terminal and change to user root with su and root password, then type
ndiswrapper -i net8185.inf in the folder where you extracted the driver files hit enter.
next typing ndiswrapper -l shows net8185 driver installed we now have to get the device id from root prompt type lspci -n at the bottom of the list is the belkin card card ID info 1799:701f write this down you will need it for the next portion of the installation.
Now from root prompt type ndiswrapper -a 1799:701f net8185
hit enter this associates the net8185 driver with the device ID of the belkin card. from root ndiswrapper -l should now show

<br>net8185 : driver installed<br>&nbsp;&nbsp;&nbsp;device (1799:701f) present<br>

from root prompt type modprobe ndiswrapper
it will pause for a moment and then the lights on the card should come on.
Once the card is running from root prompt type ndiswrapper -m to install an alias for you so the card will activate on boot.
As soon as the card is recognized it and the ndiswrapper kernel module loads fine, run

ndiswrapper -m (as root). Then the next line is automatically added

alias wlan0 ndiswrapper

to /etc/modprobe.conf. After this you can now go to configure it by running the “Network” program from system settings (or just run system-config-network). Select “New” > “Wireless connection”. The card should show up like “wlan0 (ndiswrapper)”. Proceed with the rest of the settings. If you want, you can check here to activate it at boot time. Note: If you are using a WEP key in hexadecimal format (numbers and letters from A to F) make sure you proceed it with a 0x when prompted.

You can then install and use Knetwork manager to list all the wireless connections.

Phillip

---

### Post by woopud on 2007-08-11
> **phillipchandler1 said:**
> Hiya

I have the Belkin 54g F5D7010 Ver 7 card, which Im using under 7.04 and it woks perfect.

If you goto [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) 

which is the ndiswrapper site listing for all cards starting with "B", and go down to card 46, it will guide you to [http://www.realtek.com.tw/](http://www.realtek.com.tw/)  to download the drivers for the L8185, which when unzipped will give you the 3 net8185 files.
NDiswrapper then gives the full details of installing the driver, which is below for you :

There will be 3 files net8185.inf net8185.sys net8185.cat.
Open a terminal and change to user root with su and root password, then type
ndiswrapper -i net8185.inf in the folder where you extracted the driver files hit enter.
next typing ndiswrapper -l shows net8185 driver installed we now have to get the device id from root prompt type lspci -n at the bottom of the list is the belkin card card ID info 1799:701f write this down you will need it for the next portion of the installation.
Now from root prompt type ndiswrapper -a 1799:701f net8185
hit enter this associates the net8185 driver with the device ID of the belkin card. from root ndiswrapper -l should now show

<br>net8185 : driver installed<br>&nbsp;&nbsp;&nbsp;device (1799:701f) present<br>

from root prompt type modprobe ndiswrapper
it will pause for a moment and then the lights on the card should come on.
Once the card is running from root prompt type ndiswrapper -m to install an alias for you so the card will activate on boot.
As soon as the card is recognized it and the ndiswrapper kernel module loads fine, run

ndiswrapper -m (as root). Then the next line is automatically added

alias wlan0 ndiswrapper

to /etc/modprobe.conf. After this you can now go to configure it by running the “Network” program from system settings (or just run system-config-network). Select “New” > “Wireless connection”. The card should show up like “wlan0 (ndiswrapper)”. Proceed with the rest of the settings. If you want, you can check here to activate it at boot time. Note: If you are using a WEP key in hexadecimal format (numbers and letters from A to F) make sure you proceed it with a 0x when prompted.

You can then install and use Knetwork manager to list all the wireless connections.

Phillip

Great HowTo !  Worked perfect, I can finally use Ubuntu full-time on my laptop now !

Bert

---

### Post by Shane10101 on 2007-10-03
Thanks, Phillip!  Worked perfectly for my new installation of PCLinuxOS '07.

:)

---

### Post by ascii85 on 2008-02-16
Many thanks for your post Philip, my Belkin card now works. However, one small problem remains.

I find that each time I start my laptop, the card no longer works, until I use the command "modprobe ndiswrapper" to turn the lights on.

Following Philip's instructions, everything works fine until I try to type in the command

"ndiswrapper -m"

I get the message 

"module configuration already contains alias directive"

and the file /etc/modprobe.conf does not exist on my system. Creating the a one line file /etc/modprobe.conf  containing "alias wlan0 ndiswrapper" does not do the trick.

Any suggestions would be much appreciated.

---

### Post by ascii85 on 2008-02-16
> **ascii85 said:**
> Many thanks for your post Philip, my Belkin card now works. However, one small problem remains.

I find that each time I start my laptop, the card no longer works, until I use the command "modprobe ndiswrapper" to turn the lights on.

Following Philip's instructions, everything works fine until I try to type in the command

"ndiswrapper -m"

I get the message 

"module configuration already contains alias directive"

and the file /etc/modprobe.conf does not exist on my system. Creating the a one line file /etc/modprobe.conf  containing "alias wlan0 ndiswrapper" does not do the trick.

Any suggestions would be much appreciated.

Problem solved by adding the line "ndiswrapper", without quotes, to </etc/modules>

---

### Post by darck1 on 2008-03-04
Has anybody had any luck using this method with 64bit (AMD) Gutsy? I had problems since the 8185 drivers are 32bit. I tried downloading the 64 bit windows drivers and they didn't work either.

---

### Post by ravensorrow on 2008-03-27
> **quark_77 said:**
> Hi all,

Are there drivers (linux, not ndiswrapper) for the Belkin Wireless G Notebook Card Model f5d7010 ver 7000uk? It's currently showing up on Feisty as:
```
16:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
```
I've read around and it looked like rt2500 or rtl818x would be good choices, rtl818x won't build, the makefile spits out all sorts of errors, rt2500 will build if I tweak it a bit but no new interfaces are showing up.

NB: avoiding ndiswrapper like the plague, it doesn't support packet injection.

Thanks for your advice,

Quark_77

I'm curious if this issues was *actually* addressed. The thread suggests it wasn't as the original posters question wasn't answered.

Just for clarity, I have the same card

```

06:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

```

It's a Belkin F5D7010v7 (none UK).

I'd like to know if there are kernel-level drivers for this card.

---

### Post by SockMan on 2008-04-14
Hi All

Totally new to Linux & am trying Ubuntu on my Thinkpad 600E.  Having problems getting Belkin Wireless G notebook card (7010 Chipset RaLink RT2500) to work.  Apparently this is one card that Ubuntu should recognise straight off. 

When laptop is booted up, no lights come on on the card (worked fine in Windows XP on same machine)

 lspci gives:

```
16:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
```

sudo iwconfig gives:

lo no wireless extensions

eth0 no wireless extensions

Would welcome any helpful suggestions.

Thanks

---

