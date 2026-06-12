---
title: "Dhcp"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by katie-xx on 2010-03-12
I just wanted to ask:....
There were lots of people reporting what they thought were DNS problems with 9.10.
I actually thought the problem was DHCP and had to disable IPV6 on my machine to get a lease.
Thats still the case with 9.10 ..if I re-enable IPV6 I cant get a lease.
However, no such problems with 10.04. Not for me anyhow.
I think a chap called DigiKid was most vocal about it but I wonder has anyone else noted an improvement?

Kate

---

### Post by k3lt01 on 2010-03-13
There have been dns issues for a few releases (the .10 releases in my case) and for me 10.04 has been no different but then again that would be because my 10.04 install was a straight upgrade from a week old 9.10 install. There did seem to be a couple of different work arounds to fix what seemed to be multiple issues that looked similar. For some, me included, setting dns through the dhclient.conf file worked for others it didn't.

I'm thinking about doing a clean install when beta 1 is released. If history is anything to go by (for me the .04 releases just worked) I won't have to change any settings at all and it will work ootb.

---

### Post by ronacc on 2010-03-13
there is a new section in network connections that lets you set how it handles IPV6  ( and 4)  . prior to 10.04 I too had to disable ipv6 for one of my connections . see screenshot , it seems to default to ignore .

---

### Post by k3lt01 on 2010-03-13
Your screenshot is, apart from the device, the exact same as mine and that is on my 9.10 install. I'll take a look at my 10.04 tomorrow morning and see what it's like.

Edit: Just thought I'd try the IPV6, with it set to Auto I cannot connect to my router. Change it back to Ignore and it reconnects automatically. However I must have the dns set in the dhclient.conf file to get a connection at all.

---

### Post by ronacc on 2010-03-13
I had never seen that section before 10.04 , but then I hadn't really looked , I've been disabling ipv6 on first boot since they built it into the kernel because I knew that router didn't like it . but then with 10.04 the wireless came up without me having to do that .

---

