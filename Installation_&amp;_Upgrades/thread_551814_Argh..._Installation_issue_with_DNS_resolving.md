---
title: "Argh... Installation issue with DNS resolving"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jrdelaney on 2007-09-15
Okay, so, I bought a new router yesterday, and it changed my IP address.

However, I thought I had changed everything to the new IP address so that it could resolve correctly when I type in my domain name.

It didn't work, to say the least.  I can get to my page just fine typing in the new IP address, but the URL still resolves to the old IP.

I've tried the /etc/hosts file, the /etc/networking/interfaces file, the /etc/resolv.conf file, and nothing yet...

Any help?  I've raked my brain over this and can't think of anything...

Thanks in advance!

---

### Post by t3hi3x on 2007-09-15
there is probably some issues with port fowarding. have you checked this?

what is the domain name? and what is your ip address?

---

### Post by jrdelaney on 2007-09-15
I've set all the port forwarding up, so that's not the issue, I don't believe.

DN:  [www.fbcbax.com](www.fbcbax.com)
IP:  75.75.26.105

If the port forwarding wasn't setup correctly, then you wouldn't be able to see anything using the IP address...  I think...

---

### Post by t3hi3x on 2007-09-15
what service are you using to update your DNS? your domain isnt redirecting to your IP

You are right about the forwarding. i wanted to make sure you werent using a local ip.

---

### Post by jrdelaney on 2007-09-16
I'm currently using no-ip, but I also have DynDNS setup as well, forwarding to the new IP address.

---

### Post by t3hi3x on 2007-09-17
try redoing the redirection. make sure you have it all configured correctly. if it doesnt work, contact that service to make sure you're doing it right.

---

### Post by jrdelaney on 2007-09-17
I think I'm just going to return the new N router and use my old one...  I'm having more issues with this Belkin model than I ever did with even dial-up modems...  It won't stay connected to my cable modem.  Got to love technology...  Feels like Belkin is the new Microsoft in terms of "updates"...

---

