---
title: "Problem with external Alcatel DSL modem(SpeedTouch)"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by sshahir on 2006-09-06
I cannot establish connection with ISP through my external Alcatel DSL modem(SpeedTouch).
I have used ADSLPPPOE thread ([https://wiki.ubuntu.com/ADSLPPPoE)](https://wiki.ubuntu.com/ADSLPPPoE)).
After configuring PPPoE, the message says the connection is established,
but when I try Firefox browser or ping, it is clear that the connection has not established yet.
Then I tried "dpkg -s pppoeconf", and received the following message.


---------------------------------------------------------------------------------
Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 308
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: all
Version: 1.8ubuntu2
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
Userfriendly tool for initial configuration of a DSL (PPPoE) connection.
---------------------------------------------------------------------------------------

I don&#8217;t know what is wrong with the Internet connection.

Even though external DSL ALCATEL modem is connected to my computer through RJ-45 but not USB, I have tried USBADSLMODEM/SPEEDTOUCH thread. When I try &#8220;grep &#8221; command to determine the REV=X.00, no result is obtained. So I couldn't continue with the instruction.

Can you please let me know how I can establish my Internet connection through External DSL ALCATEL modem. Thank you.

Shahed

---

### Post by John.Michael.Kane on 2006-09-06
Is your modem configured under System > Administration > Networking ? if so is the default gatway set to use the modem,and not eth0?

---

### Post by whizbaby on 2006-09-06
(1) only one pppd daemon can run at a time, so you have to kill the running before you start another one (won't do much)
(2) when you do **sudo pppoeconf** and it says that the connection thinks it's there, what is the output of **plog**?

---

### Post by sshahir on 2006-09-06
> **SD-Plissken said:**
> Is your modem configured under System > Administration > Networking ? if so is the default gatway set to use the modem,and not eth0?

Actually, I have gone through the procces explained in  ADSLPPPOE thread ([https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)) step by step in command line but not through System > Administration > Networking.


I am wonddering that if the connection is established through "sudo pppoeconf", it means that I am connected to ISP network (Internet) or not. 

Thanks,
Shahed

---

### Post by sshahir on 2006-09-06
> **whizbaby said:**
> (1) only one pppd daemon can run at a time, so you have to kill the running before you start another one (won't do much)
(2) when you do **sudo pppoeconf** and it says that the connection thinks it's there, what is the output of **plog**?



There is no information coming from &#8220;plog&#8221; command, 
[COLOR="Blue"]**>plog**[/COLOR]
**>**

but when I tried &#8220;pon&#8221;, system says the provider is not recognized 
**[COLOR="Blue"]>pon[/COLOR]**
**[COLOR="Red"]>/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'[/COLOR]**

Please let me know if you have any solution for this scenario in your mind.

Thanks,
Shahed

---

