---
title: "Should I stay with 22.04 or revert to 20.04??"
date: 2023-02-20
forum: Installation &amp; Upgrades
---

### Post by mag3lxub on 2023-02-20
Hello all! I am back to the forum after a bit of an absence. I was building two new mid towers on which I'd install Ubuntu 22.04, both desktop and server. I have completed the server hardware build, after resolving an issue that became rather frustrating for me. It seems the RAM wasn't properly seated.  Once I fixed that, the hardware came up just fine. I got Ubuntu Server installed and I even got some extras installed as well. But there's now a problem.

The objective of this server is to replace my Windows Server 2003 Primary domain controller which, to me, is a ticking time bomb.  It's still living, but I have no idea how much life it has left.  Now that Ubuntu Server is installed, I have to decide on which "Active Directory" Software to use.  After careful consideration, I decided I wanted Zentyal 7.0.  It has all the AD functions I need + DCHP and DNS, Servers, etc. etc.  The problem being, of course, Zentyal 7.0 will only install on Ubuntu Server ver. 20.04, not 22.04.  So, now, I must decide. Do I want to continue with 22.04 and either:  1) Wait for Zentyal 8.0, or 2) Install a different AD software;  or, revert back to Ubuntu Server 20.04 and get Zentyal 7.0 installed?

Ideally, I'd like to stay with 22.04.  Just as an experiment, I attempted to try and install 20.04 server on the hardware I built, overwriting my 22.04 install.  I noticed two things about that attempt. First, the 20.04 install software didn't recognize my Blu-Ray drive and dismounted it.  Second, it failed to recognize my Ethernet (built on the Motherboard), so it was pretty difficult even to proceed with the install.  the 22.04 install program recognized both and installed perfectly.  And I know the Ethernet connection works because I have Firefox up and running.  

So now, I must decide. Do I wait until Zentyal 8.0 comes out (I just received an email from their support team that the Dev. Ed. is on schedule for release in May, 2023), or do I try some alternative to Zentyal that will install presently on Server 22.04?  It certainly won't be anything like "Univention Corporate Server" as I simply cannot afford even a personal license for it or a subscription.  I believe my Windows Server 2003 box has enough life left to last untiil May, 2023. Perhaps, while waiting, I can build the hardware for my 22.04 desktop box and install Ubuntu 22.04 desktop on it and just run it in "administrator" mode without having it join any new domain.  Certainly, if my Win2003 box dies before that, I'll have to go with one of those Zentyal alternatives, but I hope not.

BTW, all of the hardware is working on Server 22.04 and even the Blu-Ray drive is recognized. I just have to search for a good driver that lets me play and record on it.  As soon as I build the desktop box, I'll test things like the dual monitor interface, etc.

Thoughts?  Is there a Zentyal alternative you might recommend I can try now, or should I wait until  Zentyal 8.0 is released?

Thanks much!

---

### Post by MAFoElffen on 2023-02-20
I tested Zental Community Edition (years back). I think it has good scripting and a nice HTTPS interface for someone coming from a Windows background. The learning curve for using their interface for administration is easier and less. I used to recommend it for small businesses... I did find ways to install Ubuntu Server, then (later) change the repo's to Zental's to install their packages and interface. Just a thought that it could be converted/migrated later.

Windows Server has envolved into using more and more Server-Core instances, without any GUI. They have conceded that running a GUI has it's overhead, and security risks. Connecting with an Windows RSAT workstation gives remote management through a GUI, so the GUI is not needed locally.

I used the same methodology with Linux Servers, in that they run headless, and I manage them remotely from a Workstation with a GUI Desktop, usually via ssh... You rarely have to be inside the computer server room, at the racks, unless there is a hardware issue. Although you can connect to a Linux Server through a Windows RSAT workstation, management from such is very limited.

Note that Zental uses SAMBA to use it as a Domain Controller... Just with it's own scripted GUI interface on top of it, to help users configure it. You could just use Ubuntu Server with SAMBA configured as a Domain Controller, straight out of the gate. Well: SAMBA, LDAP, DNS and Kerberos (for single signon).

There is always the thought of Remote management, like through Webmin...

---

### Post by mag3lxub on 2023-03-03
I have elected to stay with 22.04 and I will await Zentyal 8.0 in May.  I'll just build the Ubuntu Desktop box and trick it out before I have it join the domain that I hope I'll create with Zentyal.

And, BTW, when I put up the Ubuntu Server 22.04, it recognized my NFS system immediately.  No issues. That said, I may make the NFS box IP's fixed so they can't be overwritten.

---

### Post by mag3lxub on 2023-03-09
Update:   Ubuntu 22.04 desktop now installed on 2nd tower.  Was having some issues with this tower but unrelated to Ubuntu. Apparently, the "corei9" CPU was too much for the motherboard. It kept freezing things.  I replaced it with a corei7 (same one I used on the server) and it fired right up.  Now, I'm burning in the tower (keeping it on for a week or so) just to check the temperature and other things (there was a problem with that with the corei9).  But Jammy Jellyfish is alive and well!

Last thing I have to install is the TPM (Trusted Platform Module) for my motherboard.   And then I have to look into encryption strategies for it.

All is well.

Thanks.

---

### Post by SeijiSensei on 2023-03-10
> **mag3lxub said:**
> And, BTW, when I put up the Ubuntu Server 22.04, it recognized my NFS system immediately.  No issues. That said, I may make the NFS box IP's fixed so they can't be overwritten.
Servers should always have a fixed IP address. So should peripherals like printers if they are directly on the network. I have my router start assigning workstation addresses above a fixed number like 192.168.1.50. I use the other addresses for static assignments.

---

### Post by mag3lxub on 2023-07-09
Another Update.

I was promised by the Zentyal folks that Zentyal 8.0 would be released prior to the end of June, 2023.  To date, they haven't released it. 

I have, therefore, changed my mind and reverted back to Ubuntu Server 20.04, so that I can use Zentyal 7.0. And, now, I can see why I would have stayed with Ubuntu 22.04 if I could have.  

22.04 is a whole lot easier to configure than 20.04, once installed.  Especially when it comes to Networking and NIC recognition.    First, all I'm doing is installing Ubuntu Server 20.04 raw. And it installs fine. That said, when you get to the Network Configuration screen and it says "select one interface" to connect to the network, I don't see any "interfaces" detected.  All it gives me is the line that says, "Create Bond," even though I'm using the motherboard's built-in NIC. And, instead of "Done" & "Back" it says "Continue without Install."  And, when I plug in, it does lite up, indicating gigE traffic.  I wish I could show the pic but I can't. 

if I type "ip a" all it shows is the loopback interface.    If I type "lshw -C network,"  It does show my built-in NIC as "Unclaimed."    I think I might be able to use "Netplan" to create the interface (via editing the *.yaml file_).  But I have to wonder why the NIC was not detected automatically.   

Questions:  

1) Should Ubuntu 20.04 require a NIC "driver" program generally to be installed prior to activating the NIC, or are they pretty much built-in?  This would explain why it may not have been detected automatically during the install. BTW, the motherboard is an ASUS Prime Z590-P.  

2) Is there a "simple" way (other than manipulating the *.yaml file) to get this done from Scratch?  I can do it via the *.yaml file, but to do it I need to know the MAC address associated with the on-board NIC.  And all of the methods of finding the NIC's MAC address already assume that you have Network established and recognized! :mad: (or you're running Windows) :mad::mad:! Of course, the MAC address isn't stamped anywhere on the motherboard.  So, I may have to figure a different way.  I don't recall but, hopefully, the "lshw -C" command (since it shows basic mfgr. infor about the NIC) will also show the MAC address.  My luck it probably won't. 

Once I'm able to get the NIC recognized/activated, then I can do everything else and install Zentyal 7.0 Community division.  I will use one Static IP while setting this server up so that it doesn't interfere with my Windows server 2003 and the other devices. But when I'm ready to implement it, I just change the static IP to the one the Windows Server is using.  The gateway will always be my existing router's Static IP address so that won't change.  And, of course, the external DNS links won't change.  I will make this machine a DNS server as well, so my devices will point to it, and it will point to the externals.


Anyway, appreciate the help on the above two questions....

---

