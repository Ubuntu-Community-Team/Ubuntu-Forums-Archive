---
title: "Network connection dead after todays update &amp; restart"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swoll1980 on 2010-03-09
Any help would be appreciated. I would file a bug report but I have no idea what went wrong. I know the other Systems on my comp still work, so it's not hardware. nic is a realtek RTL8168D/8111D wired.

---

### Post by executorvs on 2010-03-10
and here I was blaming my desktop. does your's just keep trying to connect over and over?

Edit: to be clear I have a Timeline and use a shared connection from my desktop when I need it online at home. yesterday it went very buggy and I thought it was the windows partition on the desktop(only on it to use a picky activex dependent website that demands IE) being dumb.

---

### Post by executorvs on 2010-03-10
I wonder is any other people have noticed this problem? I know it didn't affect my wireless as I can still post.

---

### Post by TBABill on 2010-03-10
Was the update a kernel update or application update? If it was a kernel update can you revert in grub to the older kernel and try a restart to see if it's back on?

---

### Post by itsjustarumour on 2010-03-10
> **swoll1980 said:**
> Any help would be appreciated. I would file a bug report but I have no idea what went wrong. I know the other Systems on my comp still work, so it's not hardware. nic is a realtek RTL8168D/8111D wired.

Try opening a terminal and running:

> sudo dhclient eth0 

Forced my PC to pick up an IP address when I had a similar problem (no ethernet, but wireless working) a couple of days ago, and its been OK ever since.

---

### Post by swoll1980 on 2010-03-11
I figured out what went wrong with mine. I stat-ed my /etc/resolv.conf file
```
sudo chattr +i /etc/resolv.conf
```
because the network manager kept adding my routers address as a dns server. This would cause my name resolution to be extremely slow. For some reason when I updated this became a bad thing, and it wouldn't connect. I unstat-ed the file
```
sudo chattr -i /etc/resolv.conf
```
restarted, and all was good. I found out that I can now do address only DHCP which permanently solved my resolv.conf problem. Sorry this doesn't help with your problem.

---

### Post by xlash on 2010-03-12
I had the same problem, and the proposed solution with chattr +i then -i and to renew then the DHCP lease worked for me!

Thanks

---

### Post by fastjunk on 2010-03-12
Manually starting dhclient worked for me as well.

However, the chattr -i did not. 

"Operation not supported while reading flags on /etc/resolv.conf"

Network management in toolbar still says networks disabled.

---

