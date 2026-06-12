---
title: "How to get working LTSP on Xubuntu10.04"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by pravindra.kumar on 2010-06-05
Dear All,
I have installed Xubuntu10.04 Desktop and installed ltsp-server-standalone also, then built the ltsp client, after that updated sshkeys and image.
But client is unable to start, it's getting IP from dhcp server but it get hang after booting dhcp server.
can you make me understand step by step how to get working with LTSP in Xubntu 10.04.

---

### Post by pravindra.kumar on 2010-06-05
Do i have to configure nbd-server?
if yes then how can i do ?

---

### Post by pravindra.kumar on 2010-06-07
Hi,
Now i have switched back to Xubuntu9.10 and configured ltsp successfully but client is unable to load nbi.img.
i have dell server with 64 bit, so i followed the following options:-
(1) First i installed ltsp stand alone
sudo apt-get install ltsp-server-standalone openssh-server
(2) Second i build client
sudo ltsp-build-client --arch i386
(3) And then run the below commands
sudo ltsp-update-sskeys
sudo ltsp-update-image

---

### Post by pravindra.kumar on 2010-06-16
Now i configured LTSP on Xubuntu9.04 and it's working fine.

Thanks

---

### Post by pravindra.kumar on 2010-06-19
Hi,
Now I have installed LTSP server on Edubuntu10.04 but i am facing problem while booting client.
On client machine shows everything successfully loaded/OK but login screen is not appearing.
Then i checked syslog and found some message, plz guide me where i am making mistakes:-

Jun 19 20:49:10 edubuntu-desktop dhcpd: DHCPDISCOVER from 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:10 edubuntu-desktop dhcpd: DHCPOFFER on 192.168.9.96 to 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:13 edubuntu-desktop dhcpd: Dynamic and static leases present for 192.168.9.96.
Jun 19 20:49:13 edubuntu-desktop dhcpd: Remove host declaration ws096 or remove 192.168.9.96
Jun 19 20:49:13 edubuntu-desktop dhcpd: from the dynamic address pool for 192.168.9/24
Jun 19 20:49:13 edubuntu-desktop dhcpd: DHCPREQUEST for 192.168.9.96 (192.168.9.8) from 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:13 edubuntu-desktop dhcpd: DHCPACK on 192.168.9.96 to 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:13 edubuntu-desktop in.tftpd[1725]: tftp: client does not accept options
Jun 19 20:49:20 edubuntu-desktop dhcpd: DHCPDISCOVER from 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:20 edubuntu-desktop dhcpd: DHCPOFFER on 192.168.9.96 to 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:20 edubuntu-desktop dhcpd: Dynamic and static leases present for 192.168.9.96.
Jun 19 20:49:20 edubuntu-desktop dhcpd: Remove host declaration ws096 or remove 192.168.9.96
Jun 19 20:49:20 edubuntu-desktop dhcpd: from the dynamic address pool for 192.168.9/24
Jun 19 20:49:20 edubuntu-desktop dhcpd: DHCPREQUEST for 192.168.9.96 (192.168.9.8) from 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:20 edubuntu-desktop dhcpd: DHCPACK on 192.168.9.96 to 00:c0:9f:79:da:0d via eth0
Jun 19 20:49:20 edubuntu-desktop nbdrootd[1741]: connect from 192.168.9.96 (192.168.9.96)
Jun 19 20:49:20 edubuntu-desktop nbd_server[1742]: connect from 192.168.9.96, assigned file is /opt/ltsp/images/i386.img
Jun 19 20:49:20 edubuntu-desktop nbd_server[1742]: Size of exported file/device is 573607936
Jun 19 20:49:41 edubuntu-desktop ldminfod[1744]: connect from 192.168.9.96 (192.168.9.96)


Thanks

---

### Post by nolo on 2010-06-19
I had similar problems with LTSP on 10.04.  I have had 5 NT era PC's running as Thin Clients on 8.04.  After building a new LTSP server with 10.04, my older machines seemed to hangup on the splash screen while a newer  machine (Dell Vostro 200) booted up nice and quick the first time but after that it successfully booted about half the time. With quiet splash  disabled, I can see that my NT machines boot right up to "Start Thin  Clent" but then every 2 minutes a new error message displays: task  blocked for more than 120 seconds.

After increasing the memory on the server from 1GB to 2GB, my newer machine booted reliably.  Finally, by increasing the memory in the older PC's to a minimum of 96MB, I was able to get them all booted, but the boot time was painfully long which became very apparent after a power failure.  It took over 10 minutes for the 5 older PC's to boot.  That is unacceptable.  I gave up on 10.04 and am staying with 8.04 for now.

The only other thing I can think of is to change distros to something with a smaller image.

Sorry I can't be more positive about LTSP on 10.04.  I would be happy to answer any questions about my install, hope you find a solution for yours.  I would be delighted to hear about it if you do.

Nolo

---

### Post by pravindra.kumar on 2010-06-22
As a thin client i am using Compaq Prisarion M2000 Laptop, which configuration is 256 MB of RAM and Celeron 1.50 GHz processor.
While booting it shows:-
* Setting up LTSP client [OK]
* Starting LTSP client [OK]
and after that it goes for login screen but login screen is not appearing, only blank screen is there.
And when i am using another Conpaq laptop with 1 GB of RAM and Core2duo 3.0 processor then i can see login screen as well i can login an user also.

But it's hard to upgrade my all thin clients, so please help me how can i get worked with my P-II & P-III systems with 128/256 MB 0f RAM.

Thanks

---

### Post by nolo on 2010-06-22
How much memory do you have in the server?  I found that after adding 1GB RAM to make a total of 2GB, I was able to successfully boot P-II and P-III machines with at least 96 MB RAM on my Lucid LTSP server.  And it was a usable situation as long as I didn't try to log all 5 clients at once.

Nolo

---

### Post by teknoman on 2010-07-22
Hi all.

pravindra.kumar: 
I have exactely the same issue as you. In my case it is Kubuntu 10.04 instead of Xubuntu 10.04.
However, I have also tried with Ubuntu 10.04 with the same result.

Have you solved this issue?
If affirmative, could you publish here how you did?

I have tried all sort of methods I have found in Internet, but none of them works. It's a lot of days since I began to try it. Right now I'm tired and desperated as I will need it in my school soon.

Thank you in advance.

---

### Post by pravindra.kumar on 2010-07-30
Dear teknoman,
Not yet any solution founded but one thing i checked that i replaced my thin-client from P-III to Dual core system and that system was working fine with LTSP server.
But this solution does not solve my purpose.

Thanks

---

