---
title: "USB Wireless sees router but does not connect (DHCP problem?)"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by theSpaceAmoeba on 2009-01-22
I just recently built a new computer and installed Jaunty Alpha 3. Everything works except for my wireless connection. I have an old Linksys wireless USB network adapter (WUSB11 ver.2.6, 802.11b only!). I am trying to connect to a home router which is mixed b/g and is unsecured (neither WEP nor WPA security). This adapter worked fine with my old Windows machine.

As far as I can tell, Jaunty does have the correct driver installed for the adapter (at76_usb). Most importantly, the device is seen and used by the system (ifconfig and iwconfig see it fine, but no IP address, though an inet6 one does show up for whatever reason) and Network Manager sees all of the available wireless networks, including my home network. However, when I try to connect it takes about 30 seconds and then times out.

daemon.log shows DHCP problems: "can't create /var/lib/dhclient-wlan0.lease: No such file or directory".
I also see a series of messages like "dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval ##" where ## is a different number in each message.

One other thing of note: the Ubuntu 8.10 live CD did not even get this far because it did not recognize my wireless adapter. Jaunty recognized it, loaded the driver, and saw the wireless networks "out of the box".

I have searched this forum and else where for clues, even trying some things, but to no avail. I have re-installed Jaunty to get rid of some the mess (I had in desperation tried ndiswrapper).

Any help would be much appreciated. Thanks!

---

### Post by cariboo on 2009-01-22
I would suggest you create a /var/lib/dhcp3/dhclient-wlan0.lease file. On my system it is an empty file. Open up a terminal and type:

```
sudo touch /var/lib/dhcp3/dhclient-wlan0.lease
```

Then see what happens.

Jim

---

### Post by theSpaceAmoeba on 2009-01-22
Thank you for the quick reply:

First, I made a mistake: the file that was missing was "/var/lib/dhclient/dhclient-wlan0.lease"

But anyway, I tried your suggestion (with the correct path) and that did get rid of the error, but I'm still having the same basic problem. The same DHCPDISCOVER messages as above, followed by the message "NetworkManager: <info> Device 'wlan0' DHCP transaction took too long (>45s), stopping it."

EDIT: I not only had to create the file I had to create the "dhclient" directory. There was a "/var/lib/dhcp3" directory, but not a "/var/lib/dhclient" directory.

---

### Post by theSpaceAmoeba on 2009-01-22
I don't know if this helps, but looking at my router's logs I can see that is receives my computer's DHCPDISCOVER requests and does reply with a DHCPOFFER with an IP address. So why doesn't my computer "hear" this?

---

### Post by ronacc on 2009-01-22
I had a similar problem that cleared itself today for no reason I can find , see my comment this thread . [http://ubuntuforums.org/showthread.php?t=1046937](http://ubuntuforums.org/showthread.php?t=1046937) . I wish I could offer some help but I had tried for several days to find out why it wasn't connecting and then it cured itself with no action on my part .

---

### Post by theSpaceAmoeba on 2009-01-23
Problem fixed!

Short answer: the version of the driver included (at76_usb version 0.14beta1) does not work!

Long answer: Use driver and firmware according to the instructions given here: [http://ubuntuforums.org/showthread.php?p=6601419#post6601419](http://ubuntuforums.org/showthread.php?p=6601419#post6601419)

As I posted in that thread, there is one additional step. You will have to patch the original source file before it will compile using the patch found here: [http://developer.berlios.de/patch/?group_id=727](http://developer.berlios.de/patch/?group_id=727)

Maybe this updated driver should be included in the kernal by default?

Anyway, thanks for your input!

---

### Post by ronacc on 2009-01-23
good find , file a bug on it and include and your fix .

---

