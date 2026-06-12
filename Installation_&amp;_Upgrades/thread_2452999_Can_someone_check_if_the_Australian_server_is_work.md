---
title: "Can someone check if the Australian server is working properly?"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by danimations on 2020-11-01
I'm trying to update a system running Ubuntu 18.4.5... nothing out of the ordinary... but I'm getting glacially slow download speeds. 

To give you an idea, a batch of <250 MB of downloads has taken over an hour and is only about one third complete. I gather the data is being pushed out from a server in Australia... is someone able to check to see if the server is running properly?

My internet service is otherwise fine on another machine, running off the same router. I'd like to figure out if the server is responsible for this, or if it's a hardware issue with the PC in question. I'm open to any other ideas you might have too, of course!

The problem is "live" now... as I said, I'm about 1/3rd through the process.

Thanks in advance!

---

### Post by dragonfly41 on 2020-11-01
Not sure if this helps but pinging from U.K. [this site]("https://mirror.aarnet.edu.au/pub/ubuntu/releases/focal/").

[FONT=monospace][COLOR=#000000]```
ping -c 4 mirror.aarnet.edu.au[/COLOR]
PING mirror.aarnet.edu.au (202.158.214.106) 56(84) bytes of data.
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=1 ttl=47 time=309 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=2 ttl=47 time=309 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=3 ttl=47 time=306 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=4 ttl=47 time=304 ms

--- mirror.aarnet.edu.au ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 304.138/306.920/309.052/2.079 ms
```
[/FONT]

---

### Post by danimations on 2021-01-04
Hi, I'm updating an Ubuntu 20.4 system at the moment and am getting  transfer speeds of 17-60 BYTES per second! These are staggeringly slow. Could someone please check the AU server and see what the problem is? I have other systems using the same internet connection for other purposes without any impediment. :(

Thanks in advance!

---

### Post by danimations on 2021-01-04
Do these figures look "normal" to you? I notice that your reply came in a day after I posted the problem. Thanks for your help, Dragonfly41.

The address in question is: au.archive.ubuntu.com

---

### Post by QIII on 2021-01-04
Here's what I'm getting from the west coast of the US:

```
PING mirror.aarnet.edu.au (202.158.214.106) 56(84) bytes of data.
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=1 ttl=65 time=199 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=2 ttl=65 time=200 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=3 ttl=65 time=189 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=4 ttl=65 time=197 ms
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=5 ttl=65 time=187 ms

```

---

### Post by danimations on 2021-01-04
When I pinged the server, within Australia just now, I got a time of 31 milliseconds... on two  different machines over the same connection. 

How or why else might the  connection be "choked" do you think? Pain persists with transfer speeds.

I don't think "ping" is telling the whole story here.

----

Update: while I was drafting this note, the floodgates appear to have opened.

The connection seems to have recovered now and is blazing along. Updates imminent!

I'd still like to read anyone's thoughts on possible causes.

---

### Post by QIII on 2021-01-04
Threads merged.

---

### Post by peterg17 on 2021-01-05
I updated yesterday evening. Through my tethered mobile phone. Worked well. ping time is 23-35 ms.

---

### Post by ActionParsnip on 2021-01-05
Is this now resolved please? If so, please mark as solved

---

