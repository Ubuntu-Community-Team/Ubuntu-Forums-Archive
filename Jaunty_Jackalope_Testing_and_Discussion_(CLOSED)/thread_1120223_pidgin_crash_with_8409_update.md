---
title: "pidgin crash with 8/4/09 update"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-04-08
i updated pidgin and now it refuses with correct
this is the debug output..


```
(02:01:27) util: requested to fetch (http://192.168.2.1:55345/), full=1, user_agent=((null)), http11=1
(02:01:27) dns: DNS query for '192.168.2.1' queued
(02:01:27) dns: Created new DNS child 9958, there are now 4 children.
(02:01:27) dns: Successfully sent DNS request to child 9958
(02:01:27) dns: Got response for '192.168.2.1'
(02:01:27) dnsquery: IP resolved for 192.168.2.1
(02:01:27) proxy: Attempting connection to 192.168.2.1
(02:01:27) proxy: Connecting to 192.168.2.1:55345 with no proxy
(02:01:27) proxy: Connection in progress
(02:01:27) proxy: Connecting to 192.168.2.1:55345.
(02:01:27) util: Request: 'GET / HTTP/1.1
Connection: close
Host: 192.168.2.1:55345

'
(02:01:27) docklet: embedded
(02:01:27) util: Response headers: 'HTTP/1.1 200 OK
Transfer-Encoding: chunked
CONTENT-TYPE:  text/xml; charset="utf-8"
Server: POSIX, UPnP/1.0, Intel MicroStack/1.0.1868

'
(02:01:27) dns: Got response for 'messenger.hotmail.com'
(02:01:27) dnsquery: IP resolved for messenger.hotmail.com
(02:01:27) proxy: Attempting connection to 65.54.239.140
(02:01:27) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(02:01:27) proxy: Connection in progress
(02:01:27) dns: Got response for 'scs.msg.yahoo.com'
(02:01:27) dnsquery: IP resolved for scs.msg.yahoo.com
(02:01:27) proxy: Attempting connection to 66.163.181.181
(02:01:27) proxy: Connecting to scs.msg.yahoo.com:5050 with no proxy
(02:01:27) proxy: Connection in progress
(02:01:27) dns: Got response for 'talk.google.com'
(02:01:27) dnsquery: IP resolved for talk.google.com
(02:01:27) proxy: Attempting connection to 209.85.137.125
(02:01:27) proxy: Connecting to talk.google.com:5222 with no proxy
(02:01:27) proxy: Connection in progress
dns[9958]: Oops, father has gone, wait for me, wait...!
Segmentation fault (core dumped)
dns[9956]: Oops, father has gone, wait for me, wait...!
dns[9955]: Oops, father has gone, wait for me, wait...!
dns[9954]: Oops, father has gone, wait for me, wait...!
```

---

### Post by go7Ul1ai on 2009-04-08
Yeah, my Pidgin always quits on me after the updates :/

---

### Post by Hakkatuka on 2009-04-08
It crashes for me too. I disabled GTalk account in pidgin before it crashed - it seems to be the problem.

---

### Post by go7Ul1ai on 2009-04-08
> **Hakkatuka said:**
> It crashes for me too. I disabled GTalk account in pidgin before it crashed - it seems to be the problem.

I managed to disable it too, well at least I now can keep online with MSN. I wonder what the changes made to Pidgin were anyway?

---

### Post by puccaso on 2009-04-08
i dont think its gtalk.
i removed the account.xml file and it still doesnt connect

---

### Post by amano on 2009-04-08
Pidgin is crashing for me as well. And I use it just for ICQ chats.

---

### Post by Polygon on 2009-04-08
lolwut, what does this error mean?

dns[9956]: Oops, father has gone, wait for me, wait...!

---

### Post by puccaso on 2009-04-08
i didnt know ubuntu was patriarchal!! hehe

---

### Post by LIB53 on 2009-04-08
I was only able to test Gtalk and Gfire. They both crash, and I've been editing the account.xml to test each separately. Meanwhile, i guess I'll be trying empathy.

---

### Post by FuturePilot on 2009-04-09
Yep it crashes every time after running for about 5 seconds.

---

### Post by crjackson on 2009-04-09
Wow, I sure hope this is fixed by release day. I have to ship a system and the plan was for Jaunty. Pidgin being broken with Jaunty could be a deal breaker for this guy.

---

### Post by FuturePilot on 2009-04-09
Looks like this bug
[https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/357949]("https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/357949")

---

### Post by iGama on 2009-04-09
Where is a solution for the problem:

Run pidgin in the Terminal with the -d flag:

  pidgin -d

In the debug messages, right before the end, on top of the :

  dns[9956]: Oops, father has gone, wait for me, wait...!
  dns[9955]: Oops, father has gone, wait for me, wait...!

You shoud see a message about a PNG, for example:

  /home/igama/.purple/icons/4fdd2f4206f5803c90c183eafdd717ae68ce7526.png

Just remove that file or 

  mv ~/.purple/icons .purple/icons-backup

And pidgin will start

---

### Post by LTBookman on 2009-04-09
> **iGama said:**
> You shoud see a message about a PNG, for example:
  /home/igama/.purple/icons/4fdd2f4206f5803c90c183eafdd717ae68ce7526.png
Just remove that file or 
  mv ~/.purple/icons .purple/icons-backup
And pidgin will start

You are right, that solves it. Thanks!

---

### Post by golusweet on 2009-04-09
Same here,Pidgin crashes a lot.:mad::mad:

---

### Post by go7Ul1ai on 2009-04-09
Latest updates have fixed the problems :)

---

### Post by crjackson on 2009-04-09
> **lee.jarratt said:**
> Latest updates have fixed the problems :)

Great news. Seems like the DEVS work 24/7 in the last few days. I Love It!!!:p

---

### Post by LIB53 on 2009-04-09
Sweet. My updates will finish in about 5 minutes. :)

---

