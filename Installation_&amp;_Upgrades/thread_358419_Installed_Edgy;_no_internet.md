---
title: "Installed Edgy; no internet"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2007-02-10
Here's the deal:

I have 2 SATA hard drives. On the first, I have Windows XP and Ubuntu Dapper. Last night I installed Edgy on the second. Everything went smoothly, as far as I could tell. I can boot into any of them, so the triple boot setup worked out fine for me.

However, I get no internet connection in Edgy. I cannot connect with Firefox, nor through Synaptic. Can't upgrade. Both Windows and Dapper have internet connection.

My internet connection is high-speed cable via a D-Link DI604 router. No other computers connected.

Anyone have any suggestions? Feel free to ask for further info if you need it. Please bear in mind that I'm not a techno geek, so use small words. ;)

---

### Post by corstar on 2007-02-10
I think you may need to do 2 things.

1/ Go to Firefox, and type "about:config" then you type in "network.dns" and double click on it so you change the "IPV6" to "off"

2/ Go to System>Administration>Networking and click on the "DNS" tab. You should already have a local address in the top box, called a nameserver(mine is 10.1.1.1 for eg). This is the address used to get access to your router.

In the bottom box, type the name of your ISP. This fixes my internet problems.

I hope this helps you.

---

### Post by Coelocanth on 2007-02-10
Thanks for the reply, Corstar. I've done both and still no joy.

---

### Post by corstar on 2007-02-10
Maybe try using a different lan cable. Aside from that, I'm stumped.

---

### Post by Coelocanth on 2007-02-10
Yeah, I'm stumped too (obviously). New cable shouldn't make any difference, as the other two OSes on this same machine can connect, so it's got to be a problem with Edgy. Question is: what?

Thanks for the suggestion though.

---

### Post by maxamillion on 2007-02-10
In a Terminal window:
```
ifconfig
```

make sure the ethernet port is there (should be "eth0")

if not then do:
```
sudo ifup eth0
```

and now try:
```
sudo dhclient
```

I have heard of rare occasions when people have trouble getting a DHCP lease from their routers on boot time, I am not entirely sure of the reason for it though. Post back with your results from this, if need be we can try a few more things.

---

### Post by Coelocanth on 2007-02-10
Max: thanks for the response. Here's what I get with ifconfig:

```

lo          Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:2550.0.0
            inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16346 Metric:1
            RX packets:2 errors:0 dropped: 0 overruns:0 frame:0
            TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueueleu:0
            RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)
```

I tried the sudo ifup eth0 command and got this:

```
sudo: must be setuid root
```

I'm lost.

(note: the message in the first code block may have a couple typing errors (no way to copy/paste, so I had to write it down and type it out).

---

### Post by Tanker Bob on 2007-02-10
Your setup doesn't seem to recognize your network card.  Your response to ifconfig should have included another block of data for eth0.

Check your /etc/network/interfaces file.  You'll need to edit it as root.  Some folks use nano for that, which works pretty well from the shell terminal.  The file is probably missing some lines like:
> 
auto eth0
iface eth0 inet dhcp


Add them in, save the file, then try rebooting.  That should key the system to look for an eth0 connection.

For some reason, my wired connection never obtains an IP address on reboot.  I always have to go into the network setup, disable the eth0 connection, then immediately reenable it for it to acquire an IP address.  I don't know why, and apparently no one else does either from all the unaswered queries I've found on this subject.

---

### Post by Coelocanth on 2007-02-10
Bob: I checked out the file, and it has those lines already.

Any ideas why I get the "sudo: must be setuid root" message every time I try to use the sudo command in the terminal?

---

### Post by Tanker Bob on 2007-02-10
I've never seen that and I'm fairly new to Linux, but...it sounds like you are not in the admin group.  Are you the original user?  Have you checked the user manager to see if you are in the administration group?  I believe that the first user created is automatically put in the admin group, but subsequent ones are not.

---

### Post by Coelocanth on 2007-02-11
Yeah, I'm the original user (I installed Edgy myself less than 24 hours ago). Thanks for the help, though. I've done a little searching and am going to try a couple things. If it goes down the toilet, I'll just reinstall and see if it fixes things. I've no data whatsoever on this particular distro, so reinstalling isn't going to be a big deal. Thanks again.

---

### Post by Rumpty on 2007-02-11
> **Coelocanth said:**
> Yeah, I'm the original user (I installed Edgy myself less than 24 hours ago). Thanks for the help, though. I've done a little searching and am going to try a couple things. If it goes down the toilet, I'll just reinstall and see if it fixes things. I've no data whatsoever on this particular distro, so reinstalling isn't going to be a big deal. Thanks again.

I have just got going on broadband, and I'm using a D-Link DSL-504T router

I also couldn't browse the web with Firefox, and using about:config in Firefox and setting "network dns disable IPv6" to True certainly fixed that.

Then apt-get for updating wouldn't work. To fix that there is a very helpful comment by Python (from 2 years ago) at

[http://ubuntuforums.org/showthread.php?t=11544](http://ubuntuforums.org/showthread.php?t=11544)

Just try what he suggests - it might work for you? Something to do with the DSL-504T modem/router not handling IPv6 mapped addresses?

---

### Post by Coelocanth on 2007-02-11
Rumpty: thanks for the suggestion, but no love. I think I'll just reinstall the bloody thing and see if it makes a difference.

---

### Post by Coelocanth on 2007-02-13
Just an update for anyone that finds this thread and is experiencing a similar problem: I re-installed Edgy from the same CD as the original install (edgy alternate) and I had internet right away. So something was borked in the first install. Heh, now I have Beryl up and running on a clean OS. Woo hoo!

Thanks for all the suggestions for those of you who posted in the thread. It's much appreciated.

---

