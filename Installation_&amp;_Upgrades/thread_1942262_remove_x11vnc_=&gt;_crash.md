---
title: "remove x11vnc =&gt; crash"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by copeau on 2012-03-17
Hello all,
I'm new on this forum, and I hope this Thread is at the right place...

Well, I installed x11vnc recently, it worked quite well, but now I don't need it any more so I uninstalled it...
Now, ubuntu stops before displaying the login page...
I use tty1 to reinstall x11vnc package and ubuntu starts perfectly again.

I know this is not much information, but I could not find any log of what happens.

If anyone had already seen this behaviour, or knew how to fix it, that would be helpful.

Thanks!

---

### Post by raja.genupula on 2012-03-17
what are the packages removed while you done the uninstallation of x11vnc in your system .

---

### Post by copeau on 2012-03-17
Thanks for your reply,
At first i just remove x11vnc, then i tried to remove also x11vnc-data, and libvncserver0.
Nothing changed.

When x11vnc is installed, a server is automatically launched at startup... Maybe when I remove it, the system tries to start it and crash. But I couldn't find what script is calling it...
And, I'd be really surprised that a simple "file not found" error could crash like that...

---

### Post by raja.genupula on 2012-03-17
could you provide me that out things , that gonna help us .

---

### Post by copeau on 2012-03-17
There is no out thing, actually. 
Perhaps I havn't wrote it well, but the "File not found" was part of the hypotheses of the missing x11vnc that the system would try to launch.

The computer starts, displays the ubuntu logo as usual, then go back to black screen with 

xxxxxxxxx                          [OK]
xxxxxxxxx                          [OK]
xxxxxxxxx                          [OK]

stuff, but I didn't see anything relevant.
The last thing loaded has OK status, and there is no next one.
And amongst the different tests i've run, it is not always the same last thing loaded.

I'm sorry I'm not more precise, I admit I didn't write it down...

Well, that's no big deal. I installed x11vnc back and it's ok. I'll get rid of it if I have to make a clean install of the OS.

Thanks for your time, but let's save it for the threads with real blocking issues :)
Can you just tell me where are the conf files that might be involved in the starting process ?

---

### Post by raja.genupula on 2012-03-17
```
dmesg
```
will have the log . check out the log once for what causing the problem .

---

### Post by copeau on 2012-03-17
Ok, so I unsinstalled x11vnc again, restarted, and when it was stuck I swtiched to tty1 to log in and use dmesg

here is the end of the log :
> 
[   25.705349] type=1400 audit(1332005970.460:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=852 comm="apparmor_parser"
[   25.811429] ATL1E 0000:02:00.0: irq 45 for MSI/MSI-X
[   25.811648] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.812911] ATL1E 0000:02:00.0: eth1: NIC Link is Up <100 Mbps Full Duplex>
[   25.813020] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   25.825032] 8139too 0000:05:02.0: eth0: link down
[   25.826514] ADDRCONF(NETDEV_UP): eth0: link is not ready
[B][   25.849716] init: failsafe main process (775) killed by TERM signal
[   25.851255] init: apport pre-start process (900) terminated with status 1
[   25.862240] init: apport post-stop process (934) terminated with status 1
[   25.874971] init: kdm main process (917) killed by TERM signal
[   25.875480] init: gdm main process (929) killed by TERM signal
[/B][   25.987017] Bluetooth: Core ver 2.16
[   25.987048] NET: Registered protocol family 31
[   25.987049] Bluetooth: HCI device and connection manager initialized
[   25.987052] Bluetooth: HCI socket layer initialized
[   25.987053] Bluetooth: L2CAP socket layer initialized
[   25.987561] Bluetooth: SCO socket layer initialized
[   25.989761] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.989764] Bluetooth: BNEP filters: protocol multicast
[   25.994130] Bluetooth: RFCOMM TTY layer initialized
[   25.994136] Bluetooth: RFCOMM socket layer initialized
[   25.994137] Bluetooth: RFCOMM ver 1.11
[   26.562754] EXT4-fs (sda6): **re-**mounted. Opts: errors=remount-ro,commit=0
[   27.776368] init: lightdm main process (912) terminated with** status 1**

Is this any help ?

EDIT:
sda6 is the partition mounted on /

---

### Post by raja.genupula on 2012-03-17
[http://ubuntuforums.org/showthread.php?t=1150319&page=2](http://ubuntuforums.org/showthread.php?t=1150319&page=2)

last post .

command Num #4 no need if you not using nvidia .do remaining as usual .

---

### Post by copeau on 2012-03-20
Hello, I've done the xorg repair like you said.
The sartx command works but the opened xserver has no unity nor gnome... just the desktop with the few icons I've left there...
Tried to reboot and it crashes as usual.

I havn't much time for this stuff so I reinstalled x11vnc again, and I'll stop here.
Thx for your time.

---

