---
title: "Why does my internet connection always dissconect on his own?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-29
i'm using this command to connect:
sudo poff -a && sudo pon dsl-provider

and it's works for a while but if i leave the computer for some time it disconnect on his own how can i stop this from happening?

and another thing the network manager icon disappeared from the top panel how can i get it back?
 
thanks in advance.

EDIT:it's not a problem with my isp period.

---

### Post by shindou01 on 2010-03-29
I'm having a similar problem but i think you should be more specific while stating your problem...for instance, in my own problem, I'm using a ZTE AC2726 usb modem using wvdial to connect and I constantly self disconnect after 50,6 minutes and then automatically reconnect...

now for anyone else, can anyone tell us what to do?

---

### Post by aviramof on 2010-03-30
I'm using azetrch adsl2 dsl-600e network router modem with pppoe connection.

---

### Post by QLee on 2010-03-30
> **shindou01 said:**
> I'm having a similar problem but i think you should be more specific while stating your problem...for instance, in my own problem, I'm using a ZTE AC2726 usb modem using wvdial to connect and I constantly self disconnect after 50,6 minutes and then automatically reconnect...

now for anyone else, can anyone tell us what to do?

If I saw a question with details like that I would suggest that the person check the lease time for the connection from the server that does DHCP. Constantly disconnecting and reconnecting with times that are consistent might be related to lease time handed out with the IP address. That would be the first thing I would check with those symptoms.

---

### Post by aviramof on 2010-03-31
How can i check it and how can i see a log of my Internet connection i really need to fix it and it's not a problem with my isp that's for sure it's something in the Linux itself.

---

