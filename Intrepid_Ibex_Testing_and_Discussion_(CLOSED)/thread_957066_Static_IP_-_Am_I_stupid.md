---
title: "Static IP - Am I stupid?"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roasted on 2008-10-23
I'm trying to set a Static IP with Intrepid 64 bit. Am I stupid? I can't seem to figure it out. I went to network config and went to the IPV4 tab and set an IP, but when I ifconfig in terminal, it brings back the DHCP IP. I have no idea how else to do it. This appears to be right to me, but I'm obviously doing something wrong.

---

### Post by gaspard.leon on 2008-10-23
hi...

Did you run the following after changing the setting:
```
sudo /etc/init.d/networking restart
```

??

OR... fully restart the machine?

Cheers,

Gaspard

---

### Post by Roasted on 2008-10-23
No, I did not. But I just ran that command and it yielded no changes. I'm still on 192.168.1.101 when I want 111 as the last octet (for samba networking reasons).

---

### Post by hikaricore on 2008-10-23
Network manager in Intrepid overrides your /etc/network/interfaces file.

You will either need to remove network manager, or configure your static IP through it instead of through standard networking.

---

### Post by Roasted on 2008-10-23
I'm going to reiterate the "am I stupid" comment and ask... where is network manager?..........

---

### Post by alienexplorers on 2008-10-23
It's a small icon that looks like two terminals next to the speaker icon and the date in the upper right hand side of the top panel.

---

### Post by Roasted on 2008-10-23
What should netmask be? I got IP and gateway but, netmask? Subnet??

---

### Post by rturner on 2008-10-23
The Network Manager icon up near the speaker icon disappeared for me, but not before I set my own static ip address.  Netmask is 24, subnet is 255.255.255.0.  I haven't figured out how to call network manager to get the icon back, but so far networking is working much better than it did under hardy.  (maybe because I installed samba?).

---

### Post by otherush on 2008-10-23
If it's any consolation, I couldn't set a static ip either. :confused:

---

### Post by mc4100 on 2008-10-24
> **rturner said:**
> The Network Manager icon up near the speaker icon disappeared for me, but not before I set my own static ip address.  Netmask is 24, subnet is 255.255.255.0.  I haven't figured out how to call network manager to get the icon back, but so far networking is working much better than it did under hardy.  (maybe because I installed samba?).
The command for the NetworkManager 'icon' is:
```
nm-applet
```

---

### Post by Sef on 2008-10-24
> **Am I stupid?**

No, not knowing does not make you stupid.  Not asking does.  By asking you learn and become more informed.

---

### Post by PRGUY85 on 2008-10-24
I don't know if this was fixed already, but wasn't setting Static IP addresses a common issue posted by Ubuntu on Intrepid Ibex Beta release notes?

---

### Post by alphacrucis2 on 2008-10-24
> **PRGUY85 said:**
> I don't know if this was fixed already, but wasn't setting Static IP addresses a common issue posted by Ubuntu on Intrepid Ibex Beta release notes?

When I first tried Intrepid it was at Alpha 4 and NM was not working properly at that stage. After a later update setting static addresses worked and it also remembered them. Maybe there is a regression?

---

### Post by petri on 2008-10-24
That's strange. My computers works with static IP:s even the Atheros wifi on laptop which didn't work at all in 8.04

Made the adjusments yesterday and the still works after an update. This link put me on the track (but you all seems already know how to create static IP) [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update)

---

### Post by rturner on 2008-10-24
> **mc4100 said:**
> The command for the NetworkManager 'icon' is:
```
nm-applet
```

Thanks.  For some reason it's returning an error message:

```
** (nm-applet:22504): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

```

But I was at least able to set a static ip earlier.  Hopefully the OP can get his set.

---

### Post by krul on 2008-10-24
I had some problem with setting a fixed ip using the networking applet. However, after disabling and enabling the network it was working with the fixed ip address. Hopefully this is fixed with the RC or Final version.

---

### Post by estyles on 2008-10-24
It sounds like you're on a router (based on the IP address), so can you log into the router settings and tell it to reserve IP 111 for your MAC address?  It's not setting a static IP, but most of the time it has the same effect.

Apologies if this isn't helpful for you, but that's what I did (although I never really bothered trying to set a static IP).

---

### Post by Dedoimedo on 2008-10-24
Hello,

I set the IP to static without any problems. Just uncheck the system settings box.

You can see here:
[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update)

Look for heading: More about the Network Manager ... 

Dedoimedo

---

### Post by davebgimp on 2008-10-24
> **Dedoimedo said:**
> Hello,

I set the IP to static without any problems. Just uncheck the system settings box.

You can see here:
[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html#update)

Look for heading: More about the Network Manager ... 

Dedoimedo

Worked for me. Thanks! :)

---

### Post by bobnutfield on 2008-10-24
> **rturner said:**
> Thanks.  For some reason it's returning an error message:

```
** (nm-applet:22504): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

```

But I was at least able to set a static ip earlier.  Hopefully the OP can get his set.

If you will right click on the top panel, click "Add to Panel", the scroll down to "Notification Area", and add that to your panel, you will find that the network applet is there.

---

### Post by natros on 2008-10-25
I have the same problem, no static ip, only dhcp works but dhcp is not enabled by default on my network.

---

