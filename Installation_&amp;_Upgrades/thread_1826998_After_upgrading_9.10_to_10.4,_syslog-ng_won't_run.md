---
title: "After upgrading 9.10 to 10.4, syslog-ng won't run"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by isthisyournacho on 2011-08-17
I upgraded our postfix server from 9.10 to 10.4 and since then Postfix won't email one domain.  Since then nothing gets logged to /var/log/mail.info and syslog-ng does this when I try to start it:

root@Internal1:/var/log# /etc/init.d/syslog-ng start
 * Starting system logging syslog-ng                                                                                                                          Error binding socket; addr='AF_INET(10.1.1.123:5140)', error='Cannot assign requested address (99)'
Error initializing source driver; source='r_src'
  
The IP listed there is to another server.  I'm kinda a newbie with syslog.

I found this in /etc/syslog-ng/syslog-ng.conf:

#Listen for remote connections on port 5140
source r_src { tcp(ip("10.1.1.123") port(5140)); };

What could it be?  I thought this post was helpful:  [http://www.linuxquestions.org/questions/linux-software-2/problem-with-remote-syslog-server-operation-632477/](http://www.linuxquestions.org/questions/linux-software-2/problem-with-remote-syslog-server-operation-632477/)

But not sure how to "change the s_udp setting" or if that's the problem.

---

### Post by dino99 on 2011-08-17
i'm not used with it but:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog)

[https://encrypted.google.com/webhp?hl=fr#hl=fr&cp=16&gs_id=1q&xhr=t&q=ubuntu+syslog-ng&pf=p&sclient=psy&site=webhp&source=hp&pbx=1&oq=ubuntu+syslog-ng&aq=0&aqi=g1g-v1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=2335a469b4b03610&biw=1470&bih=856](https://encrypted.google.com/webhp?hl=fr#hl=fr&cp=16&gs_id=1q&xhr=t&q=ubuntu+syslog-ng&pf=p&sclient=psy&site=webhp&source=hp&pbx=1&oq=ubuntu+syslog-ng&aq=0&aqi=g1g-v1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=2335a469b4b03610&biw=1470&bih=856)

---

