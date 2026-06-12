---
title: "ipmsg problem"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by stripling20 on 2010-02-17
[FONT=Verdana]Hi Fellas,

I'm new to linux. i like to have some help from you guys to solve my **g2ipmsg probem**.

Actually we are use windows n fedora flavors running **g2ipmsg** (lan messenger) to communicate in cross platform but  one of the machine having g2ipmsg is not working fine. It always gets hangs when we open or minimize ipmsg window. i had tried deleting the source file and tried to install new one but it never fix the problem 

NOTE: i guess lib file got affected but im not sure.[/FONT]:confused:
[FONT=Verdana]
so pls any one help me to fix this pbm... 
[/FONT]

Thanks in Advance :D

---

### Post by 3rdalbum on 2010-02-17
You might not find a fix. g2ipmsg has not been maintained for some time now. I couldn't even make a Debian package that worked on any computers except my own.

If you want cross-platform messaging, you might want to try the XMPP protocol which is supported by many chat clients on Windows and Linux, including Pidgin.

---

### Post by stripling20 on 2010-02-17
[B][@3rdalbum]("http://ubuntuforums.org/member.php?u=61044")

Thanks for your reply

[/B]i want to tell u that g2ipmsg is for cross platform communication in LAN and for communication in WAN, Pidgin is used..myself using **XMPP protocol **inpidgin for communication over internet with multi email client (gmail, yahoo, offical email ) interface...


i goggled a lot but could not find the replacement for g2ipmsg. if any one came to know the alternative for g2ipmsg. let me know.

---

### Post by stripling20 on 2010-02-17
Hi all,

i found that g2ipmsg is not working for only one user though its working 5n with other users. so can any one come up with the soln r idea to work my g2ipmsg for that user.

---

### Post by yogesh.girikumar on 2010-02-19
Hi,

       You can try installing the ipmsg package on Linux using wine. It worked fine for me. IPMSG2 project for GNOME is not active now. So there might be some incompatibility issues involved.

       BTW: WINE is a Windows emulator for linux. You can install windows applications in linux using wine. You have to install wine first and use the windows ipmsg installer file to install it on your linux system.

       See: [http://www.ipmsg.org/index.html.en](http://www.ipmsg.org/index.html.en)
See: [http://blog.taragana.com/index.php/archive/ipmsg-for-linux/](http://blog.taragana.com/index.php/archive/ipmsg-for-linux/)
[URL="http://blog.taragana.com/index.php/archive/ipmsg-for-linux/"]
[/URL]    Hope this is helpful.

---

### Post by peterpan7191 on 2011-10-11
I know this is an old post, but try iptux. Its good and hasn't got any problems even with inter operating systems. also interacts wonderfully with ipmsg in windows.

only known problem is its unable to transfer files over mac-book ipmsgs.

---

### Post by krishna_iyer on 2012-06-04
Was happily using Ipmsg when one fine day I decided to have it run as part of auto start. So Had the app added in the session mgt and thats when it all burst into problems. It would launch but no users detected. Reset the firewall but no use. Re-install, no good.

So went with the above and had iptux installed. Does a good job but lacks some features taht is present in win/linux ipmsg clients. Like the message read notification.

The screen layout and the chat history is good. The folder transfer still does not work here either while the file transfer works. Wonder if this is an ubuntu related problem.

---

### Post by nicolasforum89 on 2012-06-04
Can you give us more details about your problem?

---

### Post by coffeecat on 2012-06-04
2-year old thread - closed.

The OP mentions that they are using Fedora/Windows. If anyone needs support for an application mentioned in this thread and is using Ubuntu, please start a new thread.

---

