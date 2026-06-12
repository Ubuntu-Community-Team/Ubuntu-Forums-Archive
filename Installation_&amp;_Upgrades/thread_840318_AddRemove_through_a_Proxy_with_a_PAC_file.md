---
title: "Add/Remove through a Proxy with a PAC file"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by LookUpSeeBlu on 2008-06-25
Hi,

We have a proxy and it uses a .pac file.  How can I get this information so that Add/Remove Programs will work?  I have set the .pac file in system->preferences->network proxy but this is not working, though I can ping out from the terminal, which is actually kind of odd since the proxy requires authentication and I have no where to put that in.  apt-get is not working either.  

I found an online post stating that if you put in the proxy settings in synaptic this will work with Add/Remove as well.  I tried this but there is no where to put in a .pac file.  

Does anyone have any suggestions on how to get around this?

Thanks.

Kevin

---

### Post by LookUpSeeBlu on 2008-06-25
I added the Acquire lines to a created apt.conf file in /etc/apt/ but this does not work for apt-get either, probably because we use a .pac file.

Any suggestions?

Thanks.

Kevin

---

### Post by LookUpSeeBlu on 2008-06-25
Not as urgent now as I went around the .pac file directly to the proxy.  If anyone knows if this is possible, I would love to hear ideas still.

Thanks.

Kevin

---

### Post by xuanhua on 2009-03-09
PAC file is some kind of javascript and it may not be interpreted other programs besides explorer.

---

