---
title: "Telnet is not working client to server, why?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by PhilKarras on 2008-04-15
Client to server Telnet is not working, why?

openbsd-inetd did not come with the initial installation of the Ubuntu Server but using:

"sudo apt-get install openbsd-inetd"

installed it & I've created the /etc/inetd.conf file & restarted openbsd-inetd.

When I try to Telnet to the Linux box from my XP laptop it hangs & never gets to user/pw prompts & entering anything simply returns me to the DOS prompt as does waiting long enough.

Both eth0 & lo are working, eth0 is at 192.168.2.75 & lo is at 127.0.0.1

I can ping 192.168.2.75 (the Linux Server) from the client DOS window.

What have I done wrong?

tnx,
pk

---

### Post by PhilKarras on 2008-04-15
After much research today I got to the linuxforums site & something there helped & it all clicked from the time I had built my first Ubuntu Linux Proxy Server:

After editing the file: sudo vi /etc/inetd.conf I got "command not found" so I had to install it using:

sudo apt-get install openbsd-inetd

then I restarted it using:

sudo /etc/init.d/openbsd-inetd restart

and it worked fine.

then I tried to telnet to the Linux box but the screen went blank for awhile & eventually returned to the DOS prompt line.

After much research, I found:

[http://www.linuxforums.org/forum/linux-newbie/116551-can-not-run-xinetd-telnet-client.html#post578172](http://www.linuxforums.org/forum/linux-newbie/116551-can-not-run-xinetd-telnet-client.html#post578172)

which, while not identical to Ubuntu, helped. I tried to install the telnet-server mentioned there but Ubuntu did not have it. However, it did find a number of "telnet" services available for installation. Since I had used "in.telnetd" in my inetd.conf file I selected to first try installing telnetd:

sudo apt-get install telnetd

During the installation a window popped up that said it found the "telnet stream..." entry that I had entered in the conf file & showed that it is trying to write the line:

telnet stream tcp nowait telnetd /usr/sbin/tcpd /usr/sbin/in.telnetd

I told it to leave the existing line & that did it! Once it was done installing I was able to telnet into the server from the XP PC just fine.

If anyone else has this problem I hope this helps.

---

