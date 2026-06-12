---
title: "No internet access in other OS after installing 12.10"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2012-10-26
I installed Ubuntu 12.10 in its own disk/partition and a different disk contains an installation of Linux Mint 13.

I can still boot Linux Mint, everything works but no app has internet access. The wired connection shows OK and the System monitor even shows occasional network activity. The other thing I noticed is that Mint time is now wrong by several hours.

The Ubuntu install was just experimental, but I do important work in the Mint OS which is now apparently useless without internet access. What's happening?

---

### Post by 2F4U on 2012-10-26
Do you have internet access in Ubuntu?

---

### Post by darkod on 2012-10-26
The ubuntu installation has nothing to do with how another OS works. When on separate partitions, the OSs are exactly that, separate. If there is a Mint forum I suggest you seek some advice for troubleshooting there, I don't know Mint.

---

### Post by dino99 on 2012-10-26
with some hardware, networkmanager is a nightmare. If you can install wicd from /var/cache/apt/archives/ using dpkg -i , then you are lucky.

did  you ping somewhere to check eth0 ?  what says ifconfig ? have you paid your isp ? (joke)

---

### Post by Rebelli0us on 2012-10-26
> **2F4U said:**
> Do you have internet access in Ubuntu?

Yes Ubuntu 12.10 works fine, it even works with the MATE shell!

---

### Post by Rebelli0us on 2012-10-26
> **darkod said:**
> The ubuntu installation has nothing to do with how another OS works. When on separate partitions, the OSs are exactly that, separate. If there is a Mint forum I suggest you seek some advice for troubleshooting there, I don't know Mint.

Yes, that should be so. The 2 disks even have their own bootloader. I mounted the Mint partition from Ubuntu 12.10, so I thought maybe the mountmanager (erroneously) changed permissions or something...

---

### Post by Rebelli0us on 2012-10-26
> **dino99 said:**
> with some hardware, networkmanager is a nightmare. If you can install wicd from /var/cache/apt/archives/ using dpkg -i , then you are lucky.

did  you ping somewhere to check eth0 ?  what says ifconfig ? have you paid your isp ? (joke)

I didn't ping, I ran ifconfig and lshw -c network and got what appears to be a normal connection.

---

### Post by darkod on 2012-10-26
> **Rebelli0us said:**
> Yes, that should be so. The 2 disks even have their own bootloader. I mounted the Mint partition from Ubuntu 12.10, so I thought maybe the mountmanager (erroneously) changed permissions or something...

Don't blame the mountmanager. The computer does what you tell it to do. :)

Usually mounting and touching system partitions of another OS is a bad idea. That's why you create shared data partitions and you can access them from any OS.

If you are talking about wi-fi connection it could be disabled now in a way, but this is only pure speculation.

If it uses dhcp, first check if it receives a correct IP in your range. Then start pinging, the home router first. Then a public IP like 8.8.8.8. Then a domain.

If ping by IP works but by domain doesn't, it's dns issue and check the dns configuration in Mint.

Etc, etc...

---

### Post by Rebelli0us on 2012-10-26
> **darkod said:**
> Don't blame the mountmanager. The computer does what you tell it to do. :)

Usually mounting and touching system partitions of another OS is a bad idea. That's why you create shared data partitions and you can access them from any OS.

If you are talking about wi-fi connection it could be disabled now in a way, but this is only pure speculation.

If it uses dhcp, first check if it receives a correct IP in your range. Then start pinging, the home router first. Then a public IP like 8.8.8.8. Then a domain.

If ping by IP works but by domain doesn't, it's dns issue and check the dns configuration in Mint.

Etc, etc...

Thank you, I mounted the ext4 partition to fetch some files I needed, isn't that what computers are for? 


ok so ping 8.8.8.8 and 192.168.1.1 worked but domains like att.net, yahoo, google and morningstar returned "unknown host"...

I googled "dns configuration" and it looks like a technical nightmare. What happened here, that OS was working just fine?

---

### Post by dino99 on 2012-10-26
sudo dpkg -i /var/cache/apt/archives/wicd.deb

---

### Post by Rebelli0us on 2012-10-26
> **dino99 said:**
> sudo dpkg -i /var/cache/apt/archives/wicd.deb

```
sudo dpkg -i /var/cache/apt/archives/wicd.deb
dpkg: error processing /var/cache/apt/archives/wicd.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/wicd.deb
```

Both installations have the same computer/host name, could that be spooking the router?

---

### Post by dino99 on 2012-10-26
dpkg does need to go on internet, use nautilus to search about wicd on your hdd(s) (maybe its registered name is not exactly "wicd", i cant check on my side)

---

### Post by Rebelli0us on 2012-10-26
> **dino99 said:**
> dpkg does need to go on internet, use nautilus to search about wicd on your hdd(s) (maybe its registered name is not exactly "wicd", i cant check on my side)

Thank you. Apparently there is a known bug:

[Intermittent DNS Resolution Failure Linux Mint 13]("https://bugs.launchpad.net/linuxmint/+bug/1023392")

and the link leads to a script that supposedly fixes the problem:


```
#!/bin/bash

clear

# Test for UID=0
if [ "$(echo $UID)" != "0" ]
then
echo “You must be superuser to run this program. Try ‘sudo ./fixmint13.sh’”
exit
fi

sed -i -e 's/dns=dnsmasq/#dns=dnsmasq/g' /etc/NetworkManager/NetworkManager.conf

ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
resolvconf --create-runtime-directories
resolvconf --enable-updates

reboot


```

gonna try it...

---

### Post by dino99 on 2012-10-26
hey we like mint too, but here its an ubuntu forum; next time you'll get fired :(

---

### Post by Rebelli0us on 2012-10-26
> **dino99 said:**
> hey we like mint too, but here its an ubuntu forum; next time you'll get fired :(

Thank you, well I thought Ubuntu did something when I mounted the disk to do some work.  Mint is basically Ubuntu 12.10 with a modified gnome.

The script didn't work, so I have a disabled OS and I can't do any work today.... and I'm at my beach house in NC and there's a hurricane warning for Cape Fear.

---

### Post by darkod on 2012-10-26
As I said, I don't know Mint 13 but there must be an easy way to set up manual dns servers. In Ubuntu it's quite easy in Network Manager.

Basically, you have to tell it to receive an IP automatically from your router, but use the dns servers that you tell it to use. If you don't know your ISP servers you can use Google's 8.8.8.8 and 8.8.4.4.

---

### Post by Rebelli0us on 2012-10-26
> **darkod said:**
> As I said, I don't know Mint 13 but there must be an easy way to set up manual dns servers. In Ubuntu it's quite easy in Network Manager.

Basically, you have to tell it to receive an IP automatically from your router, but use the dns servers that you tell it to use. If you don't know your ISP servers you can use Google's 8.8.8.8 and 8.8.4.4.

Thank you. It's like most things in life, once you know it, it's easy! But I don't...
 
The OS basically self-destructed.

It's faster to reinstall than try to fix it, and waste more of your precious time and mine.

---

### Post by jdthood on 2012-10-29
If resolvconf is installed in Mint, make sure that /etc/resolv.conf is a symbolic link to ../run/resolvconf/resolv.conf. If it isn't, create the symlink or run "dpkg-reconfigure resolvconf".

---

