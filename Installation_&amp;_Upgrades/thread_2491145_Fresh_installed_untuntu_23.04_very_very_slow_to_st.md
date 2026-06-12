---
title: "Fresh installed untuntu 23.04 very very slow to start"
date: 2023-09-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-09-27
is there a way to reduce the seconds of the following services  to speed up the start up ??

 systemd-analyze blame
29.518s plymouth-quit-wait.service
21.894s e2scrub_reap.service
16.746s NetworkManager-wait-online.service
12.412s snapd.service

Cheers

---

### Post by TheFu on 2023-09-27
Yes, but not is ways that are neophyte friendly.

Just because something takes a long time, that doesn't mean it is part of the critical path to the multi-user GUI login. I'd check that instead.

---

### Post by hoboy on 2023-09-28
> **TheFu said:**
> Yes, but not is ways that are neophyte friendly.

Just because something takes a long time, that doesn't mean it is part of the critical path to the multi-user GUI login. I'd check that instead.

Can you please elaborate what you mean please ? you mentioned "multi-user GUI login"
how do I check that ?

Cheers

---

### Post by MAFoElffen on 2023-09-28
'e2scrub_reap.service' is maintenance for ext[2,3,4] filesystems.. Do an fsck on those filesystems to ensure they are okay. Doing so may speed that up.

'NetworkManager-wait-online.service' is what it looks like. If you fill out your /etc/netplan/whatver_the_name_of.yaml network file, and for each device, add "optional=yes", that will speed that up dramatically.

I've seen the Snap Daimon sped up by disabling or uninstalling Snaps. But a lot of User do not want to substitute Firefox for non-Snap or want other Snaps they installed.

---

### Post by hoboy on 2023-09-28
> **MAFoElffen said:**
> 'e2scrub_reap.service' is maintenance for ext[2,3,4] filesystems.. Do an fsck on those filesystems to ensure they are okay. Doing so may speed that up.

'NetworkManager-wait-online.service' is what it looks like. If you fill out your /etc/netplan/whatver_the_name_of.yaml network file, and for each device, add "optional=yes", that will speed that up dramatically.

I've seen the Snap Daimon sped up by disabling or uninstalling Snaps. But a lot of User do not want to substitute Firefox for non-Snap or want other Snaps they installed.

I have the following 
/etc/netplan# vi 00-installer-config-wifi.yaml
/etc/netplan# vi 00-installer-config.yaml
/etc/netplan# vi 01-network-manager-all.yaml
/etc/netplan# vi 00-installer-config-wifi.yaml

The  01-network-manager-all.yaml contains the following 

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

****************************************************************
where shall I add optional=yes  ??

cheers

---

### Post by TheFu on 2023-09-28
Try 
```
systemd-analyze critical-chain
```
so you can pay attention to the things that are actually slowing down your login and initial use.

Also, if this isn't a desktop that moves, you don't need network-manager if you are using correct, static IPs, in a YAML file.  And if you are in a fixed location, run an ethernet cable and stop using wifi. Wifi brings all sorts of issues.

So, here's mine on a desktop, 
```
graphical.target @2min 4.166s
&#9492;&#9472;multi-user.target @2min 4.166s
  &#9492;&#9472;postfix.service @2min 4.164s +1ms
    &#9492;&#9472;postfix@-.service @2min 2.328s +1.835s
      &#9492;&#9472;network-online.target @2min 2.324s
        &#9492;&#9472;network.target @2.072s
          &#9492;&#9472;networking.service @1.970s +101ms
            &#9492;&#9472;network-pre.target @1.969s
              &#9492;&#9472;ufw.service @1.324s +644ms
                &#9492;&#9472;local-fs.target @1.315s
                  &#9492;&#9472;run-user-112.mount @2.819s
                    &#9492;&#9472;swap.target @1.011s
                      &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2d4d4273c9b260.swap @1.004s +6ms
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2d4d4273c9b260.device @1.004s

```
That claim of 2 minutes is bogus. It is closer to 5 seconds to boot.

Using the "blame" option, 
```
2min 257ms systemd-networkd-wait-online.service
   30.592s apt-daily-upgrade.service
   30.407s apt-daily.service
    4.540s plocate-updatedb.service
    1.835s postfix@-.service
    1.350s munin-node.service
    1.222s fwupd-refresh.service
     644ms ufw.service
     568ms systemd-udev-settle.service
     467ms x2goserver.service
     402ms user@1000.service
     369ms ubuntu-system-adjustments.service
     336ms networkd-dispatcher.service
....

```
That tells me that I forgot to disable the daily apt checking which I don't want anyway.  I patch weekly, not daily and I don't want to waste time getting updates at boot time.  Ok, those are disabled and masked now.  Let's see if it is faster .... I'll need to reboot, so I'm posting this BEFORE doing that.

**Update**
Ok, I've logged into the system and tried to run the same 2 commands. Alas, even though the system is up and available, 

```
tf@deneb:~$ systemd-analyze blame 
Bootup is not yet finished (org.freedesktop.systemd1.Manager.FinishTimestampMonotonic=0).
Please try again later.
Hint: Use 'systemctl list-jobs' to see active jobs
tf@deneb:~$ systemd-analyze critical-chain 
Bootup is not yet finished (org.freedesktop.systemd1.Manager.FinishTimestampMonotonic=0).
Please try again later.
```
So, don't get too hung up on this raw data. The manpage is pretty clear that it doesn't show what we think it shows.

Ok, so now I can run those commands.
Blame:
```
2min 163ms systemd-networkd-wait-online.service
    1.386s postfix@-.service
    1.174s munin-node.service
     923ms x2goserver.service
     621ms systemd-udev-settle.service
     613ms ufw.service
     553ms networkd-dispatcher.service
     428ms accounts-daemon.service
     384ms user@1000.service
     370ms ubuntu-system-adjustments.service
...
```
So the apt stuff is gone. Mission successful, but it still claims 2 minutes startup.  I promise you I logged in and had networking in about 10 seconds after the reboot.  Most people wouldn't have postfix, munin, x2go, or networkd on their desktops, so my largest boot time wasters wouldn't apply to most people (I'm guessing).
Critical chain:
```
graphical.target @2min 3.812s
&#9492;&#9472;multi-user.target @2min 3.812s
  &#9492;&#9472;postfix.service @2min 3.810s +1ms
    &#9492;&#9472;postfix@-.service @2min 2.422s +1.386s
      &#9492;&#9472;network-online.target @2min 2.414s
        &#9492;&#9472;network.target @2.140s
          &#9492;&#9472;systemd-networkd.service @1.949s +190ms
            &#9492;&#9472;network-pre.target @1.944s
              &#9492;&#9472;ufw.service @1.322s +613ms
                &#9492;&#9472;local-fs.target @1.302s
                  &#9492;&#9472;run-user-112.mount @3.334s
                    &#9492;&#9472;swap.target @939ms
                      &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2>
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\>

```
That's the full output from that command. Remember, I was logged in in less than 10 seconds after the reboot, so the 2 minutes is bogus ... from a real-world measurement, but I have no doubt that getting everything completely started for my multi-user system did take that long, officially. It is just that everything dependent after the first 10 seconds really wasn't important.

Pay attention where attention is needed.

Now, I'm running these commands on a Mint 21.2 system, which is based off 22.04.  I don't touch non-LTS releases. They aren't worth my time.  I did my alpha/beta testing time throughout the 1990s. Let someone else run beta code like 23.04 and 23.10, that's my stance.

---

### Post by MAFoElffen on 2023-09-28
*** ---> Hold off a bit...

I just spun up one of the main Luner Test VM's I had going from Dev testing... And it is having this problem. (I recreated it) So I can confirm "Houston, there is a problem." It's been booting for over 20 minutes now, so far, and is not finished..."

I have to wait for it to "finish" doing it's thing, before analyzing it to see what it is doing. Ugh.

---

### Post by TheFu on 2023-09-28
> **MAFoElffen said:**
> *** ---> Hold off a bit...

I just spun up one of the main Luner Test VM's I had going from Dev testing... And it is having this problem. (I recreated it) So I can confirm "Houston, there is a problem." It's been booting for over 20 minutes now, so far, and is not finished..."

I have to wait for it to "finish" doing it's thing, before analyzing it to see what it is doing. Ugh.

Another example for why sticking with LTS releases only for anything important could be a good idea.

---

### Post by MAFoElffen on 2023-09-28
+1 --

Yup. The one is still running right now. It's been trying to boot for hours. Itsays the estimate on the start job is 7-1/2 hours.

See attached.

It's time to kill it and intervene.

---

### Post by MAFoElffen on 2023-09-28
Booted from Installer LiveUSB ISO. Opened terminal.
```

sudo fsck.fat /dev/sda1
sudo fsck /dev/sda2

```
Mounted partitions. Mounted virtual filesystem. Chrooted into the installed system. Refreshed apt cache and applied updates.

Rebooted and everything cam up very quickly...
```

mafoelffen@lunar-lander-01:~$ sudo systemd-analyze
Startup finished in 1.268s (kernel) + 3.037s (userspace) = 4.306s 
graphical.target reached after 3.031s in userspace.

mafoelffen@lunar-lander-01:~$ grep -m1 'model name' /proc/cpuinfo
model name    : 13th Gen Intel(R) Core(TM) i9-13900K

```

---

### Post by MAFoElffen on 2023-09-28
After fsck, mounting and chrooting into it, then applying updates... It comes up very fast. In less than 4 seconds.

Back to you question. See where this says "optional: yes"?
```

mafoelffen@msi-ubuntu:~$ grep . /etc/netplan/00-installer-config.yaml
# This is the custom network config written by MAFoElffen
network:
  version: 2
  renderer: networkd
  ethernets:
    enp6s0:
      dhcp4: false
      dhcp6: false
      addresses:
          - 10.0.0.5/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      routes:
          - to: default
            via: 10.0.0.1
            metric: 100
            on-link: true
      mtu: 1500
      optional: yes
## Begin SR-IOV on enp7s0f0 
    enp7s0f0:
      virtual-function-count: 7
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v0:
      link: enp7s0f0
      addresses:
          - 10.0.0.10/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v2:
      link: enp7s0f0
      addresses:
          - 10.0.0.12/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v3:
      link: enp7s0f0
      addresses:
          - 10.0.0.13/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v4:
      link: enp7s0f0
      addresses:
          - 10.0.0.14/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v5:
      link: enp7s0f0
      addresses:
          - 10.0.0.15/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v6:
      link: enp7s0f0
      addresses:
          - 10.0.0.16/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
## End SR-IOV on enp7s0f0
## Begin Bridge on enp7s0f1
    enp7s0f1:
      dhcp4: false
      dhcp6: false
      optional: yes
  bridges:
    br0:
      interfaces: [enp7s0f1]
      addresses: [10.0.0.6/8]
      routing-policy:
         - from: 10.0.0.6
           table: 10
      # ** ADDITIONAL ROUTING POLICY **
         - to: 172.16.1.0/24
           table: 172
      # *******************************
      routes:
         - to: 0.0.0.0/0
           via: 10.0.0.1
           table: 10
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1, 1.0.0.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no
      optional: yes
## End Bridge on enp7s0f1

```
That is very much more than you would ever need. It is static addresses, bridged networking and sr-iov virtual NIC's. But notice that every network device is listed and each says "optional: yes". That prevents a job from starting in the boot process that checks and tries to wait for them to come up. I'm not sure why they do that, becaue it usually fails and throws an error, because it starts that job too soon in the boot process. I know they work and come up later. So I tell the system that checking them is "not require".

From what you posted, yours would probably be more like this... Do this to list your network devices: (or just pick them out from the output of 'ip a')
```

ip a | awk '/^[0-9]{1,2}:]?/ {print $2}' | awk '/enp[0-9]s[0-9].*:|wlo[0-9].*:/ {print}' | sed 's/://g'
## Or this gets the same information from a different source ##
awk '/^enp[0-9]s[0-9].*:|wlo[0-9].*:/ {print $1}' /proc/net/dev | sed 's/://g'

```
That outputs a list of all your network device names. Say it says your Ethernet NIC is "enp4s0". 
You take the names and use them in your netplan .yaml file, which you said was
```

 # 01-network-manager-all.yaml
# Let NetworkManager manage all devices on this system

network:
version: 2
renderer: NetworkManager

```
Which would then be:
```

 # 01-network-manager-all.yaml
# Let NetworkManager manage all devices on this system

network:
   version: 2
   renderer: NetworkManager
    ethernets:
      enp4s0:
        dhcp4: true
        dhcp6: true
        optional: yes

```

---

### Post by hoboy on 2023-09-29
Hi 
well I see lots of text but for ordinary lay man can you help with some commands ??

Cheers

---

### Post by TheFu on 2023-09-29
> **hoboy said:**
> Hi 
well I see lots of text but for ordinary lay man can you help with some commands ??

Cheers

You can't edit system files?  That's what the config files "text" are for. You are expected to edit the netplan file(s) as shown, then do the netplan generate/apply to get them working. A reboot after the apply proves to work would be a good idea too, but don't reboot too quickly. Be 100% certain the changes are working.

Of course, you'll need to run the already supplied commands to determine require information about YOUR system and edit the netplan files with the specific device name for the NIC(s) on your system.   Every time you change the netplan files, the 'generate/apply' cycle is needed.

Looks like just 1 place needs to be modified for your system in the netplan example provided.  enp...... something.  That device needs to reflect what your system has, not  MAFoElffen's or mine.

---

### Post by MAFoElffen on 2023-09-29
LOL. That's where in my instructions I said
[quote=MAFoElffen]
*Say it says your Ethernet NIC is "enp4s0".* 
[/quote]
You would take what 'your' own system output says is the device name, and use that name instead of enp4s0...

And yes, like TheFu said, after editing and saving that file, then you do
```

sudo netplan generate
sudo netplan apply

```
Note that .yaml files are indent and whitespace sensitive, which means that you can only use saces (no tabs) and all the indents have to be consistent. One extra space somewhere ad it will fail in the generate process. But the error will tell you which line # it had problems with.

That includes for your wifi... This is a wifi nelpan .yaml file for Netwrok Manager, using dhcp and allowing for user connection:
```

mafoelffen@Mikes-B460M:~$ grep . /etc/netplan/01-network-manager-wifi.yaml.off
# This is a network config written by MAFoElffen
network:
  version: 2
  renderer: NetworkManager
  wifis: {}
    wlp3s0: {}
      dhcp4: true
      dhcp6: true
      optional: yes

```
Note that you have to use your own device name for that also. WiFi device names start with the letters "wlo"

---

