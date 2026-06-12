---
title: "impossible to set a static IP with network manager"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by giorsat on 2009-09-29
I Installed the latest alpha version of Karmic and I'm not able to set a static ip with network manager. It simply doesn't save the configuration and keep adhcp profile even if I create a different profile from standard auto eth0
is it possible to write the stati configuration manually in some config file ? my pc is useless without network connection (and I can't update either)

---

### Post by moviemaniac on 2009-09-29
You can edit your /etc/network/interfaces to assign a static IP to your ethernet card. 

Here's what my eth0 part looks like:

> auto eth0
iface eth0 inet static
       address 192.168.0.3
       netmask 255.255.255.0
       gateway 192.168.0.1
	dns-nameservers 208.67.222.222 208.67.220.220


---

### Post by OffHand on 2009-09-29
You can also configure a static lease in your router and put your computer to DHCP.

---

### Post by hikaricore on 2009-09-29
Personally I've had no luck with network manager since it became part of ubuntu.
Everytime I'd configure a static IP the next boot it would be gone.

I suggest just removing this piece of garbage if it's not working for ya and setup your interfaces file manually as suggested above.  :p

---

### Post by wizard10000 on 2009-09-29
> **OffHand said:**
> You can also configure a static lease in your router and put your computer to DHCP.

^^^ this is my preferred method.  All my devices do DHCP (four computers, two game consoles, a printer and a satellite receiver) and the devices that need static IP addresses get them from the DHCP server.

We do the same thing at the office with several thousand computers - all workstation static addresses are managed on DHCP servers by MAC reservation.

---

### Post by zika on 2009-09-29
> **giorsat said:**
> I Installed the latest alpha version of Karmic and I'm not able to set a static ip with network manager. It simply doesn't save the configuration and keep adhcp profile even if I create a different profile from standard auto eth0
is it possible to write the stati configuration manually in some config file ? my pc is useless without network connection (and I can't update either)Did You check the "Available to all users" box? ...

---

### Post by Grenage on 2009-09-29
I feel your pain, and ended up using wicd.  I manually configured it initially, enly for the default manager to clean it all out after 10 minutes.

---

### Post by shakaran on 2009-09-30
You should be fill a bug with this problem, else the developers dont see this problem for make a GUI for static IP configuration.

---

### Post by zika on 2009-09-30
I'm still missing the way how You could encounter problems that You describe. I've had problems with NM but that was in earlier versions of Ubuntu, 8.10 especially, but now it works like a clock, I've had it stopped and hidden in 8.10 and I've restarted using it eventhough I love just using interfaces and resolve.conf files ... Please give us contents of /etc/NetworkManager/nm-system-settings.conf ... and check my previous post in this thread. I'm just missing what could be the problem on Your box. I've reread Your original post and the only difference is that I've deleted original "auto eth0" entry and created new one that NM gave name "Wired connection 1" ... I've edited my interfaces and resolve.conf got automatically re-created by NM. I did not use DHCP, except on chaos around Sept. 15, for quite some time ...

---

### Post by xens on 2009-09-30
I had this issue in previous ubuntu releases, I thought It was fixed???

Edit:
I just checked on my laptop... can't believe this isn't fixed, I think it's an 2 years old issue!

---

### Post by Pingue_Pinguino on 2009-10-01
I'm not able too. I've a fresh install of UNR KK on my netbook and when i try to set a staic IP, the applet crashes with a "core dumped" message.

On my previous UNR JJ network manager applet worked fine and i had my static IP set. 

Here there is a description of this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/439956](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/439956)

---

### Post by internalkernel on 2009-10-01
I was having a similar issue (maybe the same), where changing any of the settings in my current connections were not sticking. I would get an authorization dialogue then the nm-connection settings dialogue would disappear and my connections would return to a default. 

I emailed the nm mailing list... 

Updating NM to the latest daily build fixed the issue:

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

I'm not planning on leaving that repo enabled, but it's good to know it's there. :) And now I can have static settings with NM again... life is grand, ain't it...

---

### Post by scaine on 2009-10-01
I use Jaunty latptop and and older Intrepid laptop at work, plus a series of Dell PE2600 and PE2900 servers, plus the Tosh laptop I'm writing this on - all configured statically using network manager.

Can you maybe post how you're trying to set the static IP?

Here's what I do :
1. Right click on NM applet and choose "Edit Connections"
2. Click "Add" to create a new wired connection.
3. Give it a name, like "Static 192.168.1.150"
4. Click on IPv4 settings
5. Click Method and change to "Manual".
6. Click "Add"
7. Double click on Address bit - enter address, remember to hit return.
8. Do the same for netmask - remember that return button at the end.
9. Do the Gateway, and yep - hit return to save everything.
10. Optionally configure DNS and search domains.  I usually stick DNS as the gateway address.
11. Hit Apply and close the dialog.
12. Finally, left click on NM applet and choose your "Static 192.168.1.150" entry.

I'd like to hear at which point this process breaks down for you.

---

### Post by internalkernel on 2009-10-01
This is a specific regression that applied to karmic with NM 0.7.996 - 

1. open nm-connection editor
2. edit either an existing connection or create a new one
3. add static ip, netmask, gw 
4, hit apply
5. prompted with a authorization dialogue (this was confusing because it wasn't the typical keyring manager, AND it wasn't consistent.)
6. enter password & hit authenticate
7. Dialogue disappears, nm-connection editor closes. 
8. Re-open nm-connection editor and check for my previous changes
9. Get frustrated because changes didn't apply
10, try several more times
11. finally email nm-mailing list... 

~~~~~
Below is the response from the mailing list:
~~~~~
78b7101d570aa874cd748b0488ddeda15d7657df

which fixes that issue, but exposed another one with wifi secrets not
getting pulled into the connection editor.  Working on that one.  You'll
want the Ubuntu guys to pull latest changes into their package.

Dan

~~~~~~

most should be fixed in latest daily build which will get uploaded
after karmic beta is out (tomorrow)

So, please try the latest from this ppa:

   [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)


  - Alexander 


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
So, I did what they suggested... and it fixed the issue. My current version of NM is: 0.8~a~git.20090930t162757

Hope that helps...

---

### Post by xens on 2009-10-01
Hi Daniel, 

I just read your post on the nm-mailing list. Hope it'll hit karmic before finale release!

---

### Post by peterthewolf on 2009-10-01
Vote with your feet and dump network manager. The repos contain WICD which replaces network manager and just works.:)

---

### Post by internalkernel on 2009-10-01
> **peterthewolf said:**
> Vote with your feet and dump network manager. The repos contain WICD which replaces network manager and just works.:)

Ok... I'll bite... 

Network Manager "just works" too and IMHO it continues getting better and better... The work they've done on it is amazing. 

I'll agree there was a while there where it was touch and go, but that's the way it is with any beta/emerging software like that. Seriously, NM hasn't even hit 1.0 yet... and it's all ready robust and feature complete. 

The regression in this thread is to be expected, especially on an Alpha release... but, look at the date on the bug report and look at when we had an available fix. You have to admit, these guys are working hard on this... and it really shows. 

So... I am voting with my feet. :)

---

### Post by peterthewolf on 2009-10-01
Point taken intrenalkernal
However all my connections are wifi and for that WICD wins hands down

---

### Post by alexmurray on 2009-10-01
The recent bluetooth integration with network manager is a killer feature (can finally *easily* use my mobile phone as a 3G modem - just use Bluetooth applet to connect to it and tick the 'Use this device for Internet Access' (or something like that) option, and it just shows up in NetworkManager as an available connection - awesome! Besides, NetworkManager has always worked fine for me.

---

### Post by Pingue_Pinguino on 2009-10-02
Hi all,

i've followed the suggestion of internalkernel about adding a ppa source and i've solved my issue; now my nm-connection editor stores all the changes, included static ip's.

That's great, thanks a lot internalkernel ;-)

---

### Post by kevindontenville on 2009-10-21
I have this with the Beta release on a KVM instance. I cannot set a static IP and for a range of reasons I can't initiate DHCP on the network.

Too tired right now to faff with removing NM and setting old style static IP in the interface file. I hope NM gets a fair bit more polish before the RC, it does still seem to be a tad flaky in the bare essentials.

---

