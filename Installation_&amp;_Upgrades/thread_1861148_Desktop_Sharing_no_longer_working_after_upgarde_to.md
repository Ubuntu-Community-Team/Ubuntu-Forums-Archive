---
title: "Desktop Sharing no longer working after upgarde to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by kcny on 2011-10-15
Hello,

I have two computers that have been running on 11.04 and I use the built-in Desktop Sharing program on both (and use VNC to remote connect to them).

After I upgraded both computers to 11.10, it seems that Desktop Sharing isn't working on either machine?  If I launch the Desktop Sharing program, all of my settings are present from pre-upgrade (password, checked to always show icon) -- yet I do not see any icon that the program is running and when I try to connect to them it immediately fails.

How can I check to see that Desktop Sharing is actually running and/or what steps should I take to troubleshoot this?

- Thank you

---

### Post by pmla on 2011-10-15
Same problem here in 2 machines :(

---

### Post by Pepehillo on 2011-10-15
Same thing here. Any ideas?

---

### Post by ejuden on 2011-10-15
Same here, I hope someone figures it out soon, I will keep trying as well.  :(

---

### Post by kcny on 2011-10-15
It looks like Pepehillo opened a case for it:

[https://answers.launchpad.net/ubuntu/+question/174568](https://answers.launchpad.net/ubuntu/+question/174568)

---

### Post by ejuden on 2011-10-15
I did this and finally got it to work.

I had my IPv4 Settings to Manual, I set temporarily to DHCP, rebooted.  I then test connecting to the IP address assigned and was successful.  I then change the IPv4 settings back to Manual and re-entered the previous assigned IP address.  All works well now.

Who knows why.

---

### Post by kcny on 2011-10-15
Interesting, because both of my machines are on two different subnets with static addresses too.

I'll have to try your fix.

I set PC to DHCP (but since I only have static on my network didn't get an address).  Rebooted and then set back to static and rebooted again -- did not resolve issue.

---

### Post by ejuden on 2011-10-15
One more thing I noticed is that my shared printer on this machine was also no longer accessible via other computers or internet, I had to re-enable sharing for it again.

---

### Post by Pepehillo on 2011-10-15
Thanks ejuden. It worked for me too. I just updated the case I opened with the workaround you suggested. Anyway, I hope they find a "real" solution...

---

### Post by kcny on 2011-10-15
OK, worked for me to0 (I had to set DHCP on my network).

The icon still does not show up though.

---

### Post by gabhroo on 2011-10-15
Are you guys talking about assigning static IP addresses within Ubuntu or through the router? 
For me, Ubuntu is using DHCP, but my router is assigning a static IP address (corresponding to the MAC address).
I tried taking out the static IP assignment through router, but that did not help either.

---

### Post by kcny on 2011-10-16
I use static addresses assigned within Ubuntu.  I had to turn DHCP on on my router, change Ubuntu to DHCP (then reboot), then I set Ubuntu back to static and turned DHCP back off on my router.

---

### Post by xpavement on 2011-10-17
I had both a manual IP and the IP set on my router, and I still can't get desktop sharing to work after upgrading. I've tried setting to DHCP alone, restarting, and I still can't connect even though it's getting the right IP. How do I check the sharing service itself at the command line to see if it is running properly, and where are all the configs for desktop sharing stored?

---

### Post by stephensheppard on 2011-10-17
Thanks for posting your suggestions. I was in a panic. I had upgraded to 11.10 and desktop sharing went totally silent. 

In my case, I already had Automatic DHCP set, but tried changing it to: 

Automatic (DHCP) addresses only

I then rebooted and it now works.

This upgrade really seems like it wasn't ready for prime time. 

Cheers!

---

### Post by Phil Usher on 2011-10-25
I am still unable to make Remote Desktop Sharing work again after upgrade from 11.04 to 11.10.   My setup is complicated by the Ubuntu 11.10 install running as a virtual machine under VMWare Player.

In my case the network connection has always been (IPv4) DHCP and the router assigns the consistent IPv4 address based on the Mac address.   I tried changing to static (didn't work) and then back to DHCP (didn't work).

Summary of problem:
Following upgrade from 11.04 to 11.10 Remote Desktop Access via VNC (now called Desktop Sharing) stopped working. 


[LIST]
[*]Remote VNC connection (Ultra VNC) - "Failed to connect to server !".
[*]Notification Area Icon - Not present
[/LIST]


[LIST]
[*]Desktop sharing set as follows:
[/LIST]
[INDENT]_Sharing_
[/INDENT][INDENT]
[LIST]
[*](yes) Allow other users to view your desktop
[*](yes) Allow other users to control your desktop
[/LIST]
_Security_

[LIST]
[*](no) You must confirm each access to this machine
[*](yes) Require the user to enter this password *******
[*](yes) Automatically configure UPnP router to open and forward ports
[/LIST]
_Show Notification Area Icon_

[LIST]
[*](selected) Always
[/LIST]
[/INDENT]If anyone has learned more about this problem I would welcome any additional insight.  Currently I am accessing the desktop via VNC to the Host operating system - not ideal at all.

Thanks.

---

### Post by cripperz on 2011-11-23
Facing the same issue after upgrading 11.04 to 11.10 as well. Its on 64bit. Im testing a 32bit using vbox installation.

---

### Post by Phil Usher on 2011-11-25
FYI - A recent set of updates corrected his problem.

---

