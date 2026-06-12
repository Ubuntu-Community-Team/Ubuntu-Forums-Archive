---
title: "Firewalls?"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by beforewisdom on 2006-03-12
Hi;

This is bit of an ignorant question, but I have never had a high speed connection at home before.  I got a cable modem today.   I tried out the live ubuntu cd and I was incredibly impressed.   I would like to install it.

If I install ubuntu will it come with a firewall?  If yes, will the firewall be operational with or without input from me?

Thanks much in advance

---

### Post by eriefisher on 2006-03-12
I don't think one is installed by default but you could install Guarddog or firestarter. I used Guarddog on another distro and had some trouble with it and had to keep disableing it. I'm also not sure if a firewall is entirely needed. there are different opinions here on this but one is available.

eriefisher

---

### Post by munga_bill on 2006-03-12
I think the firewall that is installed by default is an excellent one, and even better, it's a 'silent one'. 
 (Because they don't actually need to make their living by scaring you into parting with your hard-earned dough, they don't feel the need to bother you with alerts every little while to make you feel like you are getting your money's worth.)
 Nevertheless, the 'firewall' is there. It's called ['iptables'.]("http://en.wikipedia.org/wiki/Iptables")  Just try a firewall test at [Sheilds Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2") or [Sygate Online Security.]("http://scan.sygatetech.com") and see if your system will pass or not. Try every test they have! Mine passes them all 100% stealth. 
Regards, munga_bill

---

### Post by eriefisher on 2006-03-12
The "iptables" never occured to me. I was thinking of some front end gui stuff.
but your right "STEALTH". Nice and quiet.

eriefisher

---

### Post by alamba on 2006-03-12
Most opinions for not needing a firewall after a typical install of ubuntu is because it doesn't open any ports. You can check this by running apt-get install nmap and then nmap localhost.

Incase you still want one, IPTable is already built in, just download firestarter as a GUI frontend and u'll be up and about in no time.

A

---

### Post by beforewisdom on 2006-03-12
Thanks for the great info about iptables and firestarter!

Now I can take back the router I bought(unopened), it is just me and since a firewall is built in I don't need it.

I installed firestarter and I like it  very much.  I have more piece of mind being able to easily see what is going on with it.

Thanks again!

Steve

---

