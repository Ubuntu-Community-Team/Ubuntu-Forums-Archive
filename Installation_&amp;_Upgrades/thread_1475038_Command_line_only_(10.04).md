---
title: "Command line only? (10.04)"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by IAmNoodle on 2010-05-06
This is a follow on from a previous problem I posted about:

> 

Just installed Lucid from CD ROM. I have 2 HDDs. When the install screen came to ask about partitions, it didn't seem to want me to install it onto the same HDD as my XP/Ubuntu 9.10 partitions, so I installed it onto my other HDD. After it finished, I restarted and it appeared on GRUB. 

It takes me to a command line where it asks me for my desktop login and then my password. It allows me to type in my login, but the password isn't so easy. It won't let me type it in. It's as if the keyboard stops working apart from the return key. 

I have no understanding of command line so any help would be appreciated

So a helpful forumer helped me out of this one, but then once I'd got past that, I wasn't taken to a desktop. As soon as I'd entered my password, it went on to tell me that there were no packages to install, and then stayed on command line as if I'd just opened a terminal. How would I get it to take me to my desktop? or is there something else I need to do here?

---

### Post by frantid on 2010-05-06
once logged in try:

[B]/etc/init.d/xdm stop

then 

startx
[/B]

---

### Post by kansasnoob on 2010-05-06
> **IAmNoodle said:**
> This is a follow on from a previous problem I posted about:



So a helpful forumer helped me out of this one, but then once I'd got past that, I wasn't taken to a desktop. As soon as I'd entered my password, it went on to tell me that there were no packages to install, and then stayed on command line as if I'd just opened a terminal. How would I get it to take me to my desktop? or is there something else I need to do here?

It sounds like you're not getting the normal gdm screen so the next time you reboot try again entering your username, then password, then type **startx** and see what happens.

---

### Post by IAmNoodle on 2010-05-08
Thanks, the startx command worked. Just need to work out how to get my wireless adaptor to work again now...

---

