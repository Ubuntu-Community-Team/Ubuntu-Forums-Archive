---
title: "Modem slow + times out"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by ironscf on 2005-04-28
Good day,

I am a new Linux user  needing help because both FireFox and Evolution work painfully slowly and then time-out breaking the connection.  Apart from that I find the Hoary Hedgehog great and as a pensioner, I seriously need to avoid MS products.

A friend who uses Redhat helped me to load, as dual boot,
 Windows XP (some sites are still incompatible) and 
Ubuntu Linux Hoary Hedgehog 5.04 (bought from Obsidian in Randburg) 
onto  my new PC (2.4 GHz Pentium, 512 Mb RAM, 40 Gb HDD). 
Luckily this way I can use XP to ask your help.

When we did the install, the modem (Duxbury external K56E) was not connected to the serial port. We added it in Network Settings/Properties by Autodetect as /dev/ttyS0 and can dial-up OK.

We tried Firefox, Edit, Preferences, General, Connection Settings to Autodetect proxy settings and also Automatic proxy configuration URL which both work but terribly slowly.  The Direct Connection to the Internet option did not work.

When I compare access to web-site home pages I get these times :
joburg.org.za  via FF = 140 secs, via Int.Expl. = 70 secs.
thestar.co.za  via FF = 400 secs, via Int.Expl. = 90 secs.
absamail.co.za  via FF = 110 secs, via Int.Expl. = 40 secs. (I logon to check mail before I  fetch/download with Evolution)

What settings should I change for absa.co.za and other sites?  Evolution mail client also runs very slowly for about 25 mins to fetch about 300 Kb then times out.

My Redhat friend also helped to change the etc/ppp/peers/provider setting for default modem to /dev/ttyS0 and speed to 115200. This had no effect.

I hope I have included all you need, to be able to advise me. Thanks for your time and expertise.

Chas. IRONS[SIZE=7]size=12[/SIZE][FONT=Arial]font=arial[/FONT][COLOR=Black]color=black[/COLOR]

---

### Post by alastair on 2005-04-28
It might be worth looking at some log file for a connection. Sometimes connection details (handshake/speed etc.) is printed - plus any warnings, errors etc.

e.g.

Before dialling up - open a shell and :

sudo tail -f /var/log/syslog

(this will show syslog messages as they happen)

Then, dial out - and look at the messages printed from that time. Maybe there is some indication.

---

### Post by ironscf on 2005-04-30
Thanks for your advice Ian. The syslog showed an error that I hope can be fixed by further advice.

These two lines  in the log copy below I assume need some remedy.

Apr 30 09:46:02 localhost pppd[7352]: Receive serial link is not 8-bit clean:
Apr 30 09:46:02 localhost pppd[7352]: Problem: all had bit 7 set to 0

************
Copy of syslog when I dialled out.

Apr 30 09:45:11 localhost udev[7344]: creating device node '/dev/ppp'
Apr 30 09:45:11 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Apr 30 09:45:11 localhost kernel: PPP generic driver version 2.4.2
Apr 30 09:45:11 localhost pppd[7352]: pppd 2.4.2 started by root, uid 0
Apr 30 09:45:12 localhost chat[7355]: timeout set to 60 seconds
Apr 30 09:45:12 localhost chat[7355]: abort on (ERROR)
Apr 30 09:45:12 localhost chat[7355]: abort on (BUSY)
Apr 30 09:45:12 localhost chat[7355]: abort on (VOICE)
Apr 30 09:45:12 localhost chat[7355]: abort on (NO CARRIER)
Apr 30 09:45:12 localhost chat[7355]: abort on (NO DIALTONE)
Apr 30 09:45:12 localhost chat[7355]: abort on (NO DIAL TONE)
Apr 30 09:45:12 localhost chat[7355]: abort on (NO ANSWER)
Apr 30 09:45:12 localhost chat[7355]: send (ATZ^M)
Apr 30 09:45:12 localhost chat[7355]: send (AT&FH0M0^M)
Apr 30 09:45:12 localhost chat[7355]: expect (OK)
Apr 30 09:45:12 localhost chat[7355]: ATZ^M^M
Apr 30 09:45:12 localhost chat[7355]: OK
Apr 30 09:45:12 localhost chat[7355]:  -- got it
Apr 30 09:45:12 localhost chat[7355]: send (ATDT0113407501^M)
Apr 30 09:45:12 localhost chat[7355]: timeout set to 75 seconds
Apr 30 09:45:12 localhost chat[7355]: expect (CONNECT)
Apr 30 09:45:12 localhost chat[7355]: ^M
Apr 30 09:45:31 localhost chat[7355]: ATDT0113407501^M^M
Apr 30 09:45:31 localhost chat[7355]: CONNECT
Apr 30 09:45:31 localhost chat[7355]:  -- got it
Apr 30 09:45:31 localhost pppd[7352]: Serial connection established.
Apr 30 09:45:31 localhost pppd[7352]: Using interface ppp0
Apr 30 09:45:31 localhost pppd[7352]: Connect: ppp0 <--> /dev/ttyS0
Apr 30 09:46:02 localhost pppd[7352]: LCP: timeout sending Config-Requests
Apr 30 09:46:02 localhost pppd[7352]: Connection terminated.
Apr 30 09:46:02 localhost pppd[7352]: Receive serial link is not 8-bit clean:
Apr 30 09:46:02 localhost pppd[7352]: Problem: all had bit 7 set to 0
Apr 30 09:46:03 localhost pppd[7352]: Hangup (SIGHUP)
Apr 30 09:46:03 localhost pppd[7352]: Exit.
Apr 30 09:46:17 localhost anacron[6814]: Job `cron.daily' started
Apr 30 09:46:17 localhost anacron[7449]: Updated timestamp for job `cron.daily' to 2005-04-30
Apr 30 09:46:48 localhost exiting on signal 15
***************************

---

### Post by alastair on 2005-04-30
Your logs show that the connection does not really happen i.e. you will not end up with any working internet here (rather than just a slow connection). 

So - is it a general connection problem like above mainly? Rather than just a slow speed once connected?

The "Receive serial link is not 8-bit clean" probably means that the login process to your ISP has failed for some reason.

How do do login? You need to know the sequence - username, password, protocol (perhaps) etc. This login process - what we are /sent/ from the ISP (e.g. "username" prompt), and what we /send/ to the ISP (i.e. our username) etc. might be a "chat script" problem (see the "chat" process above.

Have a look at where and how you login (username,password etc.). Make sure you know what the ISP expects for authentication.

If you need to, you can install a termonal program like "minicom", use it to dial the ISP, and watch what it prompts you for.

Some links that might be useful :

thread : [https://www.redhat.com/archives/redhat-list/2000-May/msg01619.html](https://www.redhat.com/archives/redhat-list/2000-May/msg01619.html)
[http://axion.physics.ubc.ca/ppp-linux.html](http://axion.physics.ubc.ca/ppp-linux.html)
[http://rsc.anu.edu.au/General/linux_ppp/ANU-PPP-HOWTO.html](http://rsc.anu.edu.au/General/linux_ppp/ANU-PPP-HOWTO.html)
[http://library.n0i.net/linux-unix/faq/ppp-2.x/](http://library.n0i.net/linux-unix/faq/ppp-2.x/)

Hope some of that helps. Tell us how you dial out, and how you have configured this.

---

### Post by ironscf on 2005-05-03
Hi again (is it Alastair or Ian?)

My Redhat buddy says the log I sent you just showed a telecoms failure.

I logged on again and got the log below. This time it did interact slowly with the web site.
 But I am wondering if I should re-install Ubuntu with the modem connected to see if the problem is cleared that way?
You realise I am a simple user NOT a Linux "command" user.

I also cannot use the floppy disk to transfer data to WIN XP because it is not configured correctly in Ubuntu despite the options being set to mount automatically.

Your advice is vital. Maybe you can tell me how to get phone support in South Africa?

Thanks again. Chas IRONS
***********************************
chas@ubuntu:~$ sudo tail -f /var/log/syslog
Password:
May  3 08:10:34 localhost syslogd 1.4.1#16ubuntu6: restart.
May  3 08:10:34 localhost anacron[6646]: Job `cron.daily' terminated
May  3 08:10:34 localhost anacron[6646]: Normal exit (1 job run)
May  3 08:13:13 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
May  3 08:13:13 localhost kernel: PPP generic driver version 2.4.2
May  3 08:13:13 localhost udev[7423]: creating device node '/dev/ppp'
May  3 08:13:13 localhost pppd[7444]: pppd 2.4.2 started by root, uid 0
May  3 08:13:14 localhost chat[7445]: timeout set to 60 seconds
May  3 08:13:14 localhost chat[7445]: abort on (ERROR)
May  3 08:13:14 localhost chat[7445]: abort on (BUSY)
May  3 08:13:14 localhost chat[7445]: abort on (VOICE)
May  3 08:13:14 localhost chat[7445]: abort on (NO CARRIER)
May  3 08:13:14 localhost chat[7445]: abort on (NO DIALTONE)
May  3 08:13:14 localhost chat[7445]: abort on (NO DIAL TONE)
May  3 08:13:14 localhost chat[7445]: abort on (NO ANSWER)
May  3 08:13:14 localhost chat[7445]: send (ATZ^M)
May  3 08:13:14 localhost chat[7445]: send (AT&FH0M0^M)
May  3 08:13:14 localhost chat[7445]: expect (OK)
May  3 08:13:14 localhost chat[7445]: ATZ^M^M
May  3 08:13:14 localhost chat[7445]: OK
May  3 08:13:14 localhost chat[7445]:  -- got it
May  3 08:13:14 localhost chat[7445]: send (ATDT0113407501^M)
May  3 08:13:14 localhost chat[7445]: timeout set to 75 seconds
May  3 08:13:14 localhost chat[7445]: expect (CONNECT)
May  3 08:13:14 localhost chat[7445]: ^M
May  3 08:13:31 localhost chat[7445]: ATDT0113407501^M^M
May  3 08:13:31 localhost chat[7445]: CONNECT
May  3 08:13:31 localhost chat[7445]:  -- got it
May  3 08:13:31 localhost pppd[7444]: Serial connection established.
May  3 08:13:31 localhost pppd[7444]: Using interface ppp0
May  3 08:13:31 localhost pppd[7444]: Connect: ppp0 <--> /dev/ttyS0
May  3 08:13:33 localhost pppd[7444]: PAP authentication succeeded
May  3 08:13:33 localhost kernel: PPP BSD Compression module registered
May  3 08:13:33 localhost kernel: PPP Deflate Compression module registered
May  3 08:13:34 localhost pppd[7444]: Cannot determine ethernet address for proxy ARP
May  3 08:13:34 localhost pppd[7444]: local  IP address 196.39.92.150
May  3 08:13:34 localhost pppd[7444]: remote IP address 196.26.208.143
May  3 08:13:34 localhost pppd[7444]: primary   DNS address 168.210.2.2
May  3 08:13:34 localhost pppd[7444]: secondary DNS address 196.14.239.2
May  3 08:13:34 localhost postfix/master[6484]: reload configuration

chas@ubuntu:~$ sudo tail -f /var/log/syslog
May  3 08:13:33 localhost pppd[7444]: PAP authentication succeeded
May  3 08:13:33 localhost kernel: PPP BSD Compression module registered
May  3 08:13:33 localhost kernel: PPP Deflate Compression module registered
May  3 08:13:34 localhost pppd[7444]: Cannot determine ethernet address for proxy ARP
May  3 08:13:34 localhost pppd[7444]: local  IP address 196.39.92.150
May  3 08:13:34 localhost pppd[7444]: remote IP address 196.26.208.143
May  3 08:13:34 localhost pppd[7444]: primary   DNS address 168.210.2.2
May  3 08:13:34 localhost pppd[7444]: secondary DNS address 196.14.239.2
May  3 08:13:34 localhost postfix/master[6484]: reload configuration
May  3 08:17:01 localhost /USR/SBIN/CRON[7688]: (root) CMD (   run-parts --report /etc/cron.hourly)

---

### Post by alastair on 2005-05-04
OK - that looks better. But I do not know why it is slow.

How do you connect? What do you type in a shell? (pon <something>?).

If you use "pon <isp>", the PPP options will be taken from the file :

/etc/ppp/peers/myisp

If you just type "pon", then the config file is :

/etc/ppp/peers/provider

These are text files.

There /is/ an error in your logs :

  Cannot determine ethernet address for proxy ARP

Which means one of the config files has a line "proxyarp" perhaps. Worth commenting out probably.

Depending on connection method, it might be worth posting the PPP config file used.

I used :

man pon

man pppconfig

To see what files might be used here (by default, pppd uses /etc/ppp/options).

P.S. My name is Alastair. Where's the Ian come from?

---

### Post by ironscf on 2005-05-07
Good day Alastair, (Idon't know where the Ian came from; confused old man!)

Problem solved by using  a terminal session to create a connection using pppconfig and now I use pon to dial and poff to disconnect \\:D/ .  Modem speed is fine now.

Thanks for your help. Of course the problem arose by not having the modem connected when I installed Hoary, but it could not be fixed using the GUI. Maybe the release notes or installation instructions could warn newbies like me to have all equipment connected.
 \\:D/  \\:D/ 
Have fun today, Chas

---

