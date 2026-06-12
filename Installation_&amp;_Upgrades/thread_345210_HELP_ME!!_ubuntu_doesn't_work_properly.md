---
title: "HELP ME!! ubuntu doesn't work properly"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by frogger fodder on 2007-01-24
Hey there

Just so you know im new to linux and know very little about it.  When i run the edgy live cd, nothing works properly. For example:


*Ubuntu clearly tells me there is an active internet connection, but mozilla cannot connect to any web pages.
*I cannot get into anything (eg "computer") without the "bug buddy" coming up saying it crashed. except for some applications.  I can use games, but i cant get into the word program.
*upon start up, bug buddy is brought up straight away.

So yeah i have no idea why it doesn't work.  I continued with the installation process (hoping that it would somehow fix the problem) but after it installed it had the same problems.  I ran windows xp again and formatted my entire computer and then tried ubuntu again, but it still has all the same problems.  please please help me.

 
some specs of my computer...
Pentium D 3ghz
2gb ram
radeon x600
2 x 250gb hdd

---

### Post by hscottyh on 2007-01-24
Let's work on one thing at a time. Can we start with the internet connection.

Can you give us more details. Are you behind a router? How does it clearly let you know you have an internet connection?

from a terminal type:
ifconfig

and post back what it says. You may want to put in xxx's for the ip addresses, since this is a public forum. That will help us know about your connection. And determine if that is the problem. If it's not then we can concentrate on Firefox.

---

### Post by frogger fodder on 2007-01-24
okay, well i have to go to work now so i dont have time to do much but i can tell u that im behind a router, and when i type the router address into firefox it brings it up saying that it is connected to the net and its all fine. and i went into network settings or something in ubuntu and i pinged google and it worked.  im not very computer literate so i dont know if u can make sense of that. but im pretty sure that the router is connected to the net.

but i have to go to work now so i wont be back for like 5 hours, but if you could please chek this post later when i have time to chek it and reply properly then it would be greatly appreciated.

thanx heaps

---

### Post by hscottyh on 2007-01-24
Yes, you definately have a connection if you pinged google. That's good it gives us something to try without totally stabbing in the dark. Your router may not handle ipv6 correctly. I've seen it a couple of times. Is it an Actiontec? To turn it off ipv6 in Firefox (you really don't need it) do this:

type *about:config* for the address in Firefox this shows you all of Firefox's settings.

Then type *ipv6* for the filter. Double on the option shown _network.dns.disableIPv6_. This will disable IPV6 (Internet Protocol Version 6) and allow you to surf with Firefox if that is the problem.

Post back and let us know if this fixes that issue. If it does, we should probably disable IPV6 for the entire OS, which is a little more envolved, but not hard. I post a howto link on this soon.

---

### Post by hscottyh on 2007-01-24
Here's a decent link for totally disabling ipv6:

[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

Follow the instructions on post #6. That is if my instructions above allowed you to surf with Firefox.

---

### Post by frogger fodder on 2007-01-24
Hey there

i disabled the "IPv6" thing on firefox and the internet works now.  Thankyou.  But unfortunatly there is still many more problems...

I cannot accsess anything in the "places" menu, such as "home folder" and "computer"

Also, i cannot sign into Gaim.

---

### Post by hscottyh on 2007-01-24
I've never heard of the problem you are having. 

I would guess it has something to do with the bug buddy errors you are getting. I haven't had a crash in a long time, so I don't remember all the info bug buddy gives you. Does it give you any details about the crash? 

Goto System -> Administration -> System Log
Look for any errors, if you find any post them back and hopefully me or someone else can help.

Good Luck.

---

