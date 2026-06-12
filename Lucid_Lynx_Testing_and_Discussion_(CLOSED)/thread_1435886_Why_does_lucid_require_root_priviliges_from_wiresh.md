---
title: "Why does lucid require root priviliges from wireshark?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-22
i have a software a network analyzer a legit software who you can call a web sniffer when i run it simply from application i can't see my netwrok cards ip address and etc only via terminal sudo wireshark i can do that why is that?

thanks in advance.

---

### Post by MacUntu on 2010-03-22
What does this have to do with "Lucid Lynx Testing and Discussion"?

Usually you'll know which functions need root privileges if you read the documentation of the software (eg. [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges))...

---

### Post by psyke83 on 2010-03-22
> **aviramof said:**
> i have a software a network analyzer a legit software who you can call a web sniffer when i run it simply from application i can't see my netwrok cards ip address and etc only via terminal sudo wireshark i can do that why is that?

thanks in advance.

Because wireshark needs to perform priviledged operations. Most applications that interface with hardware require such privileges (or if not, are separated at the service level and interface level, such as with NetworkManager).

For example, try the following (I'm assuming your wireless is designated as wlan0):
```
$ iwconfig wlan0
```

This will check the status of your wireless card, and doesn't require privileges.

Now try this:
```
$ iwconfig wlan0 power off
```

This should instruct the wireless card to disable power management (i.e. maximum performance mode), but it won't work unless you run with root/sudo privileges.

In the case of NetworkManager, there is a daemon running that handles the real operations (and this runs at startup, similar to a Windows service). When you make changes using the NetworkManager interface, the instructions are passed to the daemon (without requiring privileges, since the daemon is already running with the necessary privileges).

AFAIK, Wireshark does not separate into a daemon and interface, so it requires privileges to access your wireless card properly. Does that make sense?

---

### Post by aviramof on 2010-03-22
thank you very much.:)

---

### Post by Gerald Combs on 2010-03-22
[Wireshark doesn't need root privileges to capture, and it should never, ever be run as root]("http://brainstorm.ubuntu.com/idea/14140/"). The same goes for Tshark. Both of them run a program called [dumpcap]("http://www.wireshark.org/docs/man-pages/dumpcap.html") in order to capture packets. At a minimum dumpcap needs the CAP_NET_ADMIN and CAP_NET_RAW capabilities to do its job. You can give it these capabilities by:

[LIST]
[*]Running Wireshark as root. Again, don't try this at home. *Ever*.
[*]Running dumpcap setuid root. This method is much better.
[*]Giving dumpcap CAP_NET_ADMIN and CAP_NET_RAW. This is the preferred method, and it's what you should be doing on Lucid.
[/LIST]
If your distribution is running Wireshark as root, that is a serious bug and it should be fixed.

---

### Post by aviramof on 2010-03-22
i don't understand how to use it if i use [dumpcap]("http://www.wireshark.org/docs/man-pages/dumpcap.html") in termianl in root how can i see what i capture on wireshark itself?

if i open wireshark without root i can't see the interfaces i have i have two network cards.

---

### Post by Gerald Combs on 2010-03-22
You shouldn't have to run dumpcap directly. Instead you should grant it capture privileges and make it runnable by you. Try following the steps in this howto: [http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

---

