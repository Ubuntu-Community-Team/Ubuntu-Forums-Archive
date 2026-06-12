---
title: "IPV6 Help--disabliing it"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-10-16
How Can I tell if I have IPV6 installed & running in Karmic?  If It is running, I'd like to disable it to improve Opera 10's slow page loading.

---

### Post by @ntonius on 2009-10-16
I can help you disable ipv6 but only in firefox 

In the navigation bar (the bar were you write the address [www..]("http://www..")...) you write :
**about:config**    <--- (make sure there is no other text before or after that , no http or [www.)](www.))

a message apears and you have to press the button "**i ll be careful , i promise**"

you can now see a list of several configuration paramaters.
So you go to the **filter bar** and you type in that field **IPV6**

**network.dns.disableIPv6** will apear in the list below.
If under the tab **Value** you see the word **false** this means that IPV6 is enabled.To disable it just double click on it so that the value turns to **true**.

---

### Post by sports fan Matt on 2009-10-16
It is already true in Firefox...network.dns.disableIPv6;true

This only seems to effect opera's speed for some reason.  I just cant figure it out.

---

### Post by oboedad55 on 2009-10-16
> **sox fan Matt said:**
> It is already true in Firefox...network.dns.disableIPv6;true

This only seems to effect opera's speed for some reason.  I just cant figure it out.

I googled it and found this link, no guarantees. [http://my.opera.com/mastar2323/blog/2008/12/12/disable-ipv6-in-ubuntu](http://my.opera.com/mastar2323/blog/2008/12/12/disable-ipv6-in-ubuntu)

---

### Post by wojox on 2009-10-16
I just add ¨ipv6.disable=1¨ on the grub menu list like this:
kernel /boot/vmlinuz-2.6.30-020630-generic root=UUID=e706a870-ff71-4bee-9016-cb4c6712ee3e ro quiet splash ipv6.disable=1

---

### Post by ronacc on 2009-10-16
> **oboedad55 said:**
> I googled it and found this link, no guarantees. [http://my.opera.com/mastar2323/blog/2008/12/12/disable-ipv6-in-ubuntu](http://my.opera.com/mastar2323/blog/2008/12/12/disable-ipv6-in-ubuntu)

that doesn't work with karmic , IPV6 is built in to the kernel now ,not loaded as a module . Use wojox's method instead .

---

### Post by zevans on 2009-10-18
> **wojox said:**
> I just add ¨ipv6.disable=1¨ on the grub menu list like this:
kernel /boot/vmlinuz-2.6.30-020630-generic root=UUID=e706a870-ff71-4bee-9016-cb4c6712ee3e ro quiet splash ipv6.disable=1
 
Is there any way to make this persist across kernel updates? Otherwise every time you download a minor update to the kernel you have to do this again...

---

### Post by seeker5528 on 2009-10-21
There was another thread about this:

[http://ubuntuforums.org/showthread.php?t=1281820](http://ubuntuforums.org/showthread.php?t=1281820)

Later, Seeker

---

