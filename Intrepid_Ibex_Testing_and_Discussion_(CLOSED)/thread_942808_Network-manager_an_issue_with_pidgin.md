---
title: "Network-manager an issue with pidgin"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-09
Hi all, 
 There is an issue with network-manager and pidgin. I had been having issues with pidgin, but thought that they were due to my rules in ufw but today realized it is network-manager which is behind all this. 

Pidgin was showing the following symptons before today&#347; updates.

a. Before today, I was able to log in all the IRC channels but was unable to log in jabber/gmail accounts. 

b. After today&#347; updates I am able to get the jabber/gmail accounts but no IRC channels as well as yahoo stuff. 

Workaround :- do 

```
sudo /etc/init.d/network-manager stop
```atleast this is what worked/works for me.

---

### Post by nystire on 2008-10-09
1.) Did you log a bug?
2.) Do you have another install which you can repeat this on?

---

### Post by go7Ul1ai on 2008-10-09
The developer.pidgin.im site is down so I can't get a link for you but I think this is a known bug that has already been fixed, it will be in Pidgin 2.5.2

Lee

---

