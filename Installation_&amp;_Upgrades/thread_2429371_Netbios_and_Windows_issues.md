---
title: "Netbios and Windows issues"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by anthonyl2019 on 2019-10-17
I used to have working:

```
sudo mount -t cifs -o user=Tonyl,vers=1.0 //lenovo-2729b174/AL-XP /media/Lenovo/home/
```
and incorporated into fstab
```
//lenovo-2729b174/AL-XP /media/Lenovo/home/ cifs vers=1.0,username=Tonyl,password={pwd}
```

Recently the Netbios name is no longer recognised and I need to replace it with the IP, eg
```
//192.168.1.65/AL-XP /media/Lenovo/home/ cifs vers=1.0,username=Tonyl,password={pwd}

```
I'm not sure if this relates to the issue but in any event I'm not clear on the resolution as it is beyond my current understanding:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1789097](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1789097)

I'm running 64bit Kubuntu (cat /etc/issue=Ubuntu 18.04.3)

I have my Windows XP accessing folders on my Linux quite happily using SAMBA (smb.conf) and being able to go the other way to my Windows machines and NAS without fixing iPs would be very handy.

So i think all I need to know is how to get Ubuntu to resolve the Netbios name and confirm that it was some recent update that has broken it and not something I've done.

---

### Post by SeijiSensei on 2019-10-17
Create an entry in /etc/hosts for the machine:

```

192.168.1.65   lenovo-2729b174

```

Linux never uses Netbios resolution. It relies on DNS, or on static entries in the /etc/hosts file.  Assuming you don't want to go to the trouble of creating a local DNS server for your network, adding entries to /etc/hosts on the clients is the easiest solution.

---

### Post by anthonyl2019 on 2019-10-17
I've never had the entry in the Hosts file, it used to accept the name, and it is not how I read the bug report which alludes to something being broken regarding Name resolution. smb.conf has the line
```
netbios name = {m/c name}
```
SMBTREE shows the workgroup workstations (Windows + NAS) by their Netbios names.
The bug report alludes to Name Resolution.

---

### Post by Morbius1 on 2019-10-17
smbtree is a smbclient utility. The samba client knows - under the right conditions - what a netbios name is.

CIFS has no idea what a netbios name is nor does it even know that smb.conf exists. CIFS only knows about a tcp hostname. In order for that host name to be resolved to an ip address some sort of LAN-side dns server has to be in place or some other mechanism ( hosts file, wins, mdns, wsd, ... ) needs to provide that function.

Why not post the make and model of your router because a lot of this can be done by your router. Worst case the assignment of a static ip address can be done by the router itself so you don't have to do on each client.

---

### Post by anthonyl2019 on 2019-10-17
I don't fully understand how the system was able to interpret the names as in my OP, I only know that it did up to a few weeks ago and now it doesn't.  I know how to reserve IPs with my router, it is not what I want to do with my workstations which sometimes might be wireless as the laptops are moved around the house or wired if a bit out of reach of a good WiFi signal.  So whilst there are several workarounds I refer back to my original post and the commands/parameters that worked.  
My 
HOSTS 
```
127.0.0.1 localhost
```
and 
HOSTNAME
```
hplinux
```

files have not changed.

I have accepted all updates offered and would suspect something has interfered.

---

### Post by anthonyl2019 on 2019-10-19
Notwithstanding the responses in this thread (and perhaps feeling somewhat abandoned) the issue has resolved itself, with access reverting to how it used to work despite no knowing changes on my part. 

However one of the machines on the LAN, a Win7 Home, had stopped allowing access from my XP machine.  About once a month I sync some folders using a simple Command script.  I rebooted the Win7 Home and proceeded with the script.  A day or two later I came back to this issue and noticed that it was all working as I desired.  Coincdence?

---

