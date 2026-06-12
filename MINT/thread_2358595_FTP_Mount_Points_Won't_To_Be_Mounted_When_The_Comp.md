---
title: "FTP Mount Points Won't To Be Mounted When The Computer Boot-up."
date: 2017-04-15
forum: MINT
---

### Post by guillaumesoucy on 2017-04-15
Hello,  
  
 
  I have FTP mounted on a lot of my machines using curlFTPfs and each time they boot-up, the FTP is mounted into mount points as I have set /etc/fstab for this happen.  
  
 
  But, I got an Asus netbook without any builtin wired network interface card, so I have hooked an USB 3.0 NIC to the USB 3.0 port of the netbook. Each time the machine done to boot-up and I login into my user account, the network is already connected (Static IP configuration) but the FTP mount point set in /etc/fstab are not mounted. I need to to an mount -a (As root) for getting them mounted. 
  
 
  I know its not the end of the world to have to do a mount -a at each system boot-up but I don’t understand why other computers can mount the FTP mount points without any intervention from my end, issuing the command mount -a.  
  
 
  Is this can be related to the USB 3.0 NIC is not “ready” when the system try to read /etc/fstab when he booting?  

  
 
  Also, I try to setup “Start up applications” for the command mount -a can be executed when I login but there was no good results as this command need to be executed with root privileges. I add my username   in the root group (0), when verifying in which group my username is, the Terminal return stated my username was in the root group.  
  
 
  I reboot the netbook, nothing mounted after having logged into my account.

  
 
  Thanks in advance for your help!
  
 
  Guillaume

---

### Post by TheFu on 2017-04-15
If you have interest ... [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Sounds like a startup dependency issue that isn't properly handled. Which release are you running? Networking needs to be up before any network mounting is attempted. In theory, systemd should make that easier.

Using plain FTP isn't something I'd do.

---

### Post by guillaumesoucy on 2017-04-16
Hi TheFu


Thanks for your reply!

I ran Mint 18.1, I know its not Ubuntu and I posting on the Ubuntu forums but both systems are based on the same thing. 

I suspect the issue was effectively caused because the network is not available when the system read /etc/fstab during boot-up as its an netbook and the network is provided by a USB 3.0 NIC due to no NIC builtin on the motherboard. All other machines here doesn't have that issue as they all having an integtated NIC.  

Also, what I should do with the startup dependency? And should change something in /etc/system.d/system.conf ?


Guillaume

---

### Post by coffeecat on 2017-04-16
> **guillaumesoucy said:**
> I ran Mint 18.1

*Thread moved to the **MINT** sub-forum.*

---

### Post by TheFu on 2017-04-16
If the system are on the same LAN, you should stop using FTP and start using NFS.  PERIOD.

I don't know what "mint 18.1" means at a low level, so cannot make any recommendations about boot dependencies. Sorry.

---

### Post by Morbius1 on 2017-04-16
> **guillaumesoucy said:**
> I suspect the issue was effectively caused because the network is not available when the system read /etc/fstab during boot-up as its an netbook and the network is provided by a USB 3.0 NIC due to no NIC builtin on the motherboard. 
Then issue the "mount -a" as root after the network is up:

Create a file:
```
gksu xed /etc/network/if-up.d/refstab
```
Add this to it:
```
#!/bin/sh
mount -a
```
Make the file executable: 
```
sudo chmod +x /etc/network/if-up.d/refstab
```

---

### Post by guillaumesoucy on 2017-04-16
@Morbius1

Thanks, I've try this tonight and update this post. 

@TheFu 

Thanks for your recommendation, I appreciate that but, for certain reasons I can't use NFS.

---

### Post by TheFu on 2017-04-16
And the **autofs** suggestion?

---

### Post by guillaumesoucy on 2017-04-16
> **TheFu said:**
> And the **autofs** suggestion?


Yes it works, finally! Thanks! ;-)

---

