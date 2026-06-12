---
title: "dialup"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by Chris Sharman on 2006-08-24
Installed Ubuntu 6.06
From [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) wiki:
 Download & run latest scanmodem from [http://www.linmodems.org/](http://www.linmodems.org/).
 $ sudo sh -c "echo ltserial >> /etc/modules"
 $ sudo sh -c "echo ltmodem >> /etc/modules"

 create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:
  #ltmodem 
  KERNEL="ttyLTM0", SYMLINK="modem"

 $ sudo modprobe ltserial
 $ sudo modprobe ltmodem

... that's the modem installed.

Configuring dialup connection
 $ sudo adduser USERNAME dip
 $ sudo adduser USERNAME dialout
(already a member)

Then setup via system>admin>network:
got error back "LCP: timeout sending Config-Requests"
Tried pppconfig. pon failed to get connect.
Tried wvdial. Hung waiting for prompt after connect. Turned on stupid mode. Gets connect 52000 NoEC, and the same LCP timeout as above.
Tried the linmodems group - MarvS suggested pci=routeirq after the kernel line in the boot menu, and/or asyncmap 0xffffffff in the ppp options file.
Also tried replacedefaultroute and a handful of other things.

Nothing seems to work.
More detail in the attachments.
Any suggestions ?
And how do I enable use of dialup without admin privs & password, for my kids ?

Thanks
Chris

---

### Post by Chris Sharman on 2006-08-25
Now online.
Needed the new martian drivers from MarvS (at linmodems.org).
It's a bit clunky though, and requires admin privilege+password to run both martian_helper and wvdial. Modem monitor doesn't work.

Any advice ?
I'd really like a one-click passwordless connection/disconnection, otherwise it's just too clunky (and insecure) to let the kids loose on.

Thanks,
Chris

To dial in:
$ sudo martian_helper --daemon /dev/modem
Password:
$ sudo wvdial
ATDT179
CONNECT 52000 V42bis
--> Carrier detected.  Waiting for prompt.
CVX Access Switch.
Access is restricted to authorized users only.
login:
--> Looks like a login prompt.
--> Sending: USERNAME
USERNAME
password:
--> Looks like a password prompt.
--> Sending: (password)
Exiting shell, and starting PPP session.
~[7f]}#@!}!}!} }<}!}$}%\}"}&} }*} } }%}&N}7p[01]}'}"}(}"}1}$}%b{A~
--> PPP negotiation detected.
--> Starting pppd at Fri Aug 25 10:25:31 2006
--> Pid of pppd: 8458
--> Using interface ppp0
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> local  IP address 213.48.230.83
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> remote IP address 213.48.230.2
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> primary   DNS address 193.38.113.3
--> pppd: p&#65533;[05][08]8&#65533;[05][08]
--> secondary DNS address 194.117.157.4
--> pppd: p&#65533;[05][08]8&#65533;[05][08]

After this, it goes quiet, and everything just works.

---

### Post by zxee on 2006-08-25
Did you use the pppconfig command from a terminal to set up your modem and user? I see you did a lot of commandline, but the pppconfig script creates some required files in /etc/ppp/peers.
Also what does your /etc/chatscripts file look like?
I'm a long time dial up linux user so I can give you other suggestions but think you should try pppconfig.
If-given that you're using a winmodem with linmodem drivers you want a different interface or can't get gnome-ppp working try chestnut dialer [http://freshmeat.net/projects/chestnut-dialer/](http://freshmeat.net/projects/chestnut-dialer/)
(you'll have to hand install that because it isn't in the repos) Hope that helps.

---

