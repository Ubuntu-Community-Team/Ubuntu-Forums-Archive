---
title: "Help Please : Bug 258743"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-12
I need some help please on bug:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/+bug/258743](https://bugs.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/+bug/258743)

With the latest NM 0.7 I cant edit my autosetup eth0 connection to modify the MTU so I can test if its now fixed.

There is no unlock button and I don't know how to launch it as root to overcome the security.

Thanks

---

### Post by taavikko on 2009-02-12
> **Nullack said:**
> I need some help please on bug:

There is no unlock button and I don't know how to launch it as root to overcome the security.

Thanks

You can start it with,
```
nm-connection-editor
```
and appropriate privileges before the command (sudo,gksu,gksudo,sudo su,su)

Hmm, that didn't seem to do the trick... time to visit LP..

---

### Post by Nullack on 2009-02-12
Hmmm gksudo nm-connection-editor is still greyed out. Maybe I need to delete the auto config one and do a manual one?

---

### Post by taavikko on 2009-02-12
> **Nullack said:**
> Hmmm gksudo nm-connection-editor is still greyed out. Maybe I need to delete the auto config one and do a manual one?

Yeah, just noticed (couldn't test when replied, posted with mobile phone)

It seems that Policykit integration is failing with nm-applet?

---

### Post by taavikko on 2009-02-12
Just additional info:

To test connection: [http://www.speedguide.net/analyzer.php](http://www.speedguide.net/analyzer.php)

for used to be good settings?
```
# increase TCP max buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase Linux autotuning TCP buffer limits
# min, default, and max number of bytes to use
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216

#several tcp optimizations
net.ipv4.tcp_congestion_control = cubic   
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_rfc1337 = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.route.flush = 1
net.ipv4.tcp_moderate_rcvbuf = 1

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
```

Add it to /etc/sysctl.conf and **sudo sysct -p** to run it on the fly

---

### Post by tawmas on 2009-02-12
Here I can edit the "auto eth0" connection with no problems...

Have you already checked PolicyKit (System > Administration > Authorizations). I'm posting a screenshot of the relevant settings.

Right now I can't recall if that's the default or if I edited them.

---

### Post by scaine on 2009-02-12
Fine here in Intrepid too - I'll pop upstairs and check Jauny later on tonight.

Checked authorisations and noticed there's a HAL/Wake on LAN entry just after the network manager entry.  Anyone know what this implies?  Is there a gnome GUI in the works for enabling this stuff?  Cos that would rock - WOL is a total pain in Ubuntu (or any other linux I've ever tried).  Even Leopard gets this right, so I don't understand why it's such a struggle in Ubuntu...

---

### Post by Gourgi on 2009-02-12
> **tawmas said:**
> Here I can edit the "auto eth0" connection with no problems...

Have you already checked PolicyKit (System > Administration > Authorizations). I'm posting a screenshot of the relevant settings.

Right now I can't recall if that's the default or if I edited them.

can you please the output of
```

cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf

```

auto eth0 is locked for me too.

---

### Post by Nullack on 2009-02-13
> **tawmas said:**
> Here I can edit the "auto eth0" connection with no problems...

Have you already checked PolicyKit (System > Administration > Authorizations). I'm posting a screenshot of the relevant settings.

Right now I can't recall if that's the default or if I edited them.

Thanks tawmas

Ive found a critical bug with policykit:

[https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/328921](https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/328921)

I'm trapped every direction I attempt to go when testing this :)

---

### Post by tawmas on 2009-02-13
> **Gourgi said:**
> can you please the output of
```

cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf

```

auto eth0 is locked for me too.

I'm away right now. I'll post them tonight.

---

### Post by tawmas on 2009-02-13
Here they are:

```
tawmas@tylke:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 208.67.222.222 208.67.220.220
tawmas@tylke:~$ cat /etc/NetworkManager/nm-system-settings.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true


```

---

### Post by Gourgi on 2009-02-13
> **tawmas said:**
> Here they are:

```
tawmas@tylke:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 208.67.222.222 208.67.220.220
tawmas@tylke:~$ cat /etc/NetworkManager/nm-system-settings.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
[COLOR="Red"]managed=true[/COLOR]


```

i think this why you can manage auto eth0
my nm-system-settings.conf 
says 
```
[ifupdown]
managed=false

```
 i'll look at it and post back

---

### Post by scaine on 2009-02-15
My eth0 interface is also completely greyed out.  I have nothing in /etc/network/interfaces except a lo entry.  But in /etc/NetworkManager/nm-system-settings.conf, I do have :
```
[ifupdown]
managed=false

```I edited this to be true, then issued a restart of networking, but I get the following error, and the interface is still greyed out in Network Manager :
```
scaine@Groovy:/etc/NetworkManager$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]
```

I'm stumped.

---

