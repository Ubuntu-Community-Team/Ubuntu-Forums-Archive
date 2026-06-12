---
title: "Fiesty Fawn does not recognise the internet"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by NutrOn on 2007-06-26
:confused:I have PPP set up for dial up, The machine dial out on boot, receives connection successfully, but then no applications such as firefox or synaptic will not successfully negotiate the connection. Page not found or repo unavailable. If I query my logs I am in fact connected.  Some kind of funky net error? 
     I am on a dual boot system (2 HD) using the admin network tool it seems to be correct to what is suggested on posts. I also have Gnome PPP and have created an empty etc resolv file. The name servers are comeing up though.
Any thoughts, help?

---

### Post by nyvalbanat on 2007-06-26
Can you run "route" to display the routing table? If it's empty, your requests won't know how to reach the internet.

---

### Post by NutrOn on 2007-06-27
How do you fix that or check?
NutrOn

---

