---
title: "Ubuntu 20.04 LTS Update"
date: 2022-08-26
forum: Installation &amp; Upgrades
---

### Post by securitydad on 2022-08-26
I guess you can file this under, I should have known better.

I clicked the link to update my Ubuntu 20.04 LTS box, and today when I restarted it, the Network connection was gone.

I added another WIFI interface via USB, but that did not connect either.

Any suggestions for a quick repair for the OS so that I can rejoin the network?

Thank you.

---

### Post by ajgreeny on 2022-08-26
Was this a normal update or an upgrade of the OS version  from 20.04 to 22.04?

To help you we need a lot more detail of the system hardware and software so the output from command ***inxi -Fzx ***would be very useful.

---

### Post by securitydad on 2022-08-27
The update was a normal update from the software Mangler.

I tried using a static IP on the network controller to no avail.  I am going to presume that the only update available is a reinstall from USB.

---

### Post by kurt18947 on 2022-08-27
Anything useful here?

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

I assume you have another means of internet access? If not, do you have a live DVD/USB? 

I just searched for "ubuntu + manually configure a network". Lots of possibilities there. Of course it may be easier to simply reinstall.

---

### Post by deadflowr on 2022-08-27
Have you tried rebooting into an older kernel?

---

### Post by securitydad on 2022-08-27
I appreciate your reply, and the guide to set an IP Address (I did the same thing, only differently), the issue is that while the interface reports being up, it cannot reach the network.  A simple ping to the network gateway does not work.

I will get a USB to repair/reinstall.  Thank you for the helpful converation.

---

### Post by securitydad on 2022-08-27
I have not, Please remind me what the secret handshake is on startup to select a different kernel.

---

### Post by TheFu on 2022-08-27
Network connection not working could be multiple things.  Often, a DNS failure will be seen by end-users as "no network", when the network is actually working fine.

If you can 
```
$ ping 1.1.1.1
```
Then the network is fine and it is just the DNS causing issues. This is much more common.
If you can't ping that, try pinging your LAN router.  A typical LAN router IP is:
```
$ ping 192.168.1.1
```
If that works, then it is an issue for the ISP or a routing problem.

With those 2 ping tests, we learn much and rule out the harder issues if they work.  The inxi command and output requested by  ajgreeny will be helpful.  This assumes inxi is installed. If not, try ```
lshw -C network
```.  If that isn't installed either, there are other, ugly commands to get the information.

When all this is handled, please, please, please, install both those tools. They are extremely helpful.

---

### Post by securitydad on 2022-08-27
Dear TheFu,

Your KungFu is strong, however my TaeKwonDo has Mangled the network.  Both of the Ping tests return the magical phrase Destination Host Unreachable.

Thank you for playing along.

---

### Post by securitydad on 2022-08-27
Dear TheFu,<br><br>Your KungFu is strong, however my TaeKwonDo has Mangled the network.&nbsp; Both of the Ping tests return the magical phrase Destination Host Unreachable.<br><br>Thank you for playing along.

---

### Post by securitydad on 2022-08-27
Looks like the option key (secret keystroke) is the SHIFT key.

[https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

Thank you, the older kernel works.  

I think that I need to remove the new kernel.

---

### Post by TheFu on 2022-08-27
> **securitydad said:**
>  
Thank you, the older kernel works.  

I think that I need to remove the new kernel.

I'd think the driver wasn't built for the new kernel, but at least you have a workaround for a bit.

Sorry I didn't see the "can't ping the local gateway" two posts above mine.  That makes me think it is a driver issue, so the inxi and lshw commands to see the working (old kernel) and non-working (new kernel) drivers would be helpful.

---

