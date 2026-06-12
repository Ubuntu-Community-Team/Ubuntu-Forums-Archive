---
title: "SSH into Ubuntu server Virtualbox"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by retrodans on 2012-06-28
I have been trying things for ages, and still haven't found a solution for this.  I have installed the new ubuntu server in virtualbox within an ubuntu desktop host.  I checked the SSH checkbox on install, then ran ifconfig.  But there is no ip to use there by default.

Within virtualbox I have setup the second network adapter to host-only, but now am at a loss as to what to try.

Any suggestions would be most appreciated, as this is a little frustrating as to what I am doing wrong.

Thanks for any advice you can give,
Dan

---

### Post by darkod on 2012-06-28
I think it's much easier if you set the adapter mode in Bridged mode. That way it will be bridged into the same LAN as your ubuntu desktop.

For example, if the desktop is running in a subnet from your router like 192.168.1.x you can set any static IP outside the router dhcp range to the server.

Then you can access it from any computer on the LAN by its IP, and also you can easily forward ports on the router directly to this IP in case you want to access (or simply test) anything from outside your home.

---

### Post by retrodans on 2012-06-29
Thanks for your reply Darkod, I have since shutdown the server client, set the adaptor to bridged mode (I chose eth0 - only other option was wlan0), then restarted the server client.

Sadly, looking at ifconfig, I don't think it has worked.  My eth0 inet addr is showing 10.0.2.15 (but my local range is 192.168.xxxx as per usual).  I also see no eth1, and wonder whether it is eth1 I should be seeing for ssh usage.  I know some documentation says I need to edit files if I use host-adaptor, do I have to do anything similar for bridged?

Thanks for your advice,
Dan

---

### Post by darkod on 2012-06-29
By default the server install configures only the first eth0 adapter. For the second eth1 you have to do it yourself.

But also I wanted to mention, depending with how many adapters you want to use the server, you can disable the second adapter in the VBox settings, and change the mode of the first one from NAT to Bridged.

Right now, the first adapter is NAT by default, so VBox is doing the change from 192.168 to 10.0.

If you want to keep both adapter, the configuration of the second would be like:
```
auto eth1
iface eth1 inet static
   address 192.168.1.x
   netmask 255.255.255.0
```You need to add that to /etc/network/interfaces, save the changes and restart the server. After that you should be able to SSH into it.

I use nano to edit, but you can use vi if it's easier for you. I find nano easier.
sudo nano /etc/network/interfaces

When you add the lines you press Ctrl+O to save, Ctrl+X to exit nano.

In case you want to work with only one adapter and you disable the second and change the first to bridged, use the same lines as above but replace eth1 with eth0. And you will need to add another line below netmask with the gateway (which is your router), so it should be something like:
```
gateway 192.168.1.1
```

---

### Post by retrodans on 2012-06-29
Thanks for your advise, I will give that a try tonight when I am home and let you know how it goes.  From what I understand I need the NAT device to use the network from my HOST.  Although if this is not the case, as Bridged will allow the client to connect directly, therefore getting internet access, then I will remove the first network device as suggested.

Thanks again,
Dan

---

### Post by darkod on 2012-06-29
VBox configures only one adapter by default, and always in NAT mode.
But it allows you to change it to Bridged in which case you can imagine it like a second computer on the same LAN and you need to use 192.168.1.x address on it, with your router as the gateway. In much cases it's easier to use it like that instead of with NAT.

---

### Post by retrodans on 2012-06-29
That has worked perfectly.  I set my 1st network adapter as a bridge and to use my wlan, and straight away it finds the correct ip.  So much easier than trying to set a second adapter up.

Thanks for your help,
Dan

---

### Post by darkod on 2012-06-29
No problem.

Just remember, if you left the setting as dhcp in /etc/network/interfaces, sometimes it can change the IP.

It's best to be configured with static IP even if it's simply a test server in VBox.

When you consider it solved, please mark it Solved in the Thread Tools above the first post.

---

