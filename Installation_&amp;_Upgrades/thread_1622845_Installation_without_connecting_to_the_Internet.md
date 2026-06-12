---
title: "Installation without connecting to the Internet"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-16
Hi there,
for security reason, I would try install Ubuntu 10.10 alternate CD without connecting to the Internet. Only after setup correctly then connect to the Internet. I'm wondering if this is good? At what point do you think is the best time to initially connect to the Internet?

---

### Post by Herman on 2010-11-16
If you install Ubuntu while the computer is not connected to the internet it will be okay, you will not be able to get updates during installation and the installation time will be a little bit quicker.

---

### Post by zhaotianwu on 2010-11-16
> **Herman said:**
> If you install Ubuntu while the computer is not connected to the internet it will be okay, you will not be able to get updates during installation and the installation time will be a little bit quicker.


Can I get update later? Is it the same update or it is recommended to update during installation?

---

### Post by Herman on 2010-11-16
Yes, you can get the same updates after the installation, and you will still end up with the same operating system and software in the end, so it doesn't really matter whether you get the updates during installation or later. 
If you feel you have a security related reason for doing so, it's quite alright to do it that way. I cannot promise you it will make any difference to your security,maybe a security expert can comment?

---

### Post by holiday on 2010-11-16
It depends on what ports you have open, what services you're running. Are you open to the internet in any way or are you behind a router? 

Your router will protect you. If you don't have one then get one. Out of the box, Ubuntu doesn't open any public ports - except to their repositories. (Someone correct me) You're going to have to trust them at some point. 

If you're protecting information for which you are liable, then you should learn a lot more about security than your question suggests you have done. 

As home users we can worry too much about security. This is not Windows. Really - hardly anyone uses Ubuntu and Ubuntu is fairly hardened and its users mostly domestic so cracking a standard Ubuntu install is much effort for small effect. 

If you like, there are many interesting articles on this site, and other Unix sites, about intrusion-detection. 

I suggest that you do what we all do, or most of us do: plug in and download.

---

### Post by zhaotianwu on 2010-11-17
> **holiday said:**
> It depends on what ports you have open, what services you're running. Are you open to the internet in any way or are you behind a router? 

Your router will protect you. If you don't have one then get one. Out of the box, Ubuntu doesn't open any public ports - except to their repositories. (Someone correct me) You're going to have to trust them at some point. 

If you're protecting information for which you are liable, then you should learn a lot more about security than your question suggests you have done. 

As home users we can worry too much about security. This is not Windows. Really - hardly anyone uses Ubuntu and Ubuntu is fairly hardened and its users mostly domestic so cracking a standard Ubuntu install is much effort for small effect. 

If you like, there are many interesting articles on this site, and other Unix sites, about intrusion-detection. 

I suggest that you do what we all do, or most of us do: plug in and download.

Thank you holiday. Could you please explain a bit about the router, is it true that ANY router (including those featuring WIFI wireless ones) can protect you, without you even having to do some settings? Why?

---

### Post by holiday on 2010-11-17
> **zhaotianwu said:**
> Thank you holiday. Could you please explain a bit about the router, is it true that ANY router (including those featuring WIFI wireless ones) can protect you, without you even having to do some settings? Why?


Any router will protect you more than a direct connection to the internet will. Your router will assign to your computer a network address that the internet cannot see. If you want to open a port on your computer you will have to tell your router to forward to your computer's private address. 

Connections initiated by your computer will go through, however. If you initiate a connection with a Ubuntu repository your router will permit the communication. 

If you browse the web, the router will permit that communication. 

But if some rogue tries to invade, it will not be able to find your computer's address - because only your router knows what it is and will pass through only those communications that you tell it, explicitly, to allow.

---

### Post by zhaotianwu on 2010-11-17
> **holiday said:**
> Any router will protect you more than a direct connection to the internet will. Your router will assign to your computer a network address that the internet cannot see. If you want to open a port on your computer you will have to tell your router to forward to your computer's private address. 

Connections initiated by your computer will go through, however. If you initiate a connection with a Ubuntu repository your router will permit the communication. 

If you browse the web, the router will permit that communication. 

But if some rogue tries to invade, it will not be able to find your computer's address - because only your router knows what it is and will pass through only those communications that you tell it, explicitly, to allow.

Thank you very much. But how can I tell if I'm using a router? For example, if I am on campus and the whole campus was covered by wifi, is it a router, or just Internet? How about Starbucks?

---

### Post by Mark Phelps on 2010-11-18
> **zhaotianwu said:**
> Thank you very much. But how can I tell if I'm using a router? For example, if I am on campus and the whole campus was covered by wifi, is it a router, or just Internet? How about Starbucks?

In those situations, you're going through a Router.

The only time you're NOT going through a Router of some type is when your PC is plugged directly into a cable/dsl "modem" which does not have multi-port output.  

There are some router/modem combinations out there that connect directly to the Internet and have output ports in the back for cable connections to PCs.

---

