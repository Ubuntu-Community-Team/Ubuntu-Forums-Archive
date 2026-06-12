---
title: "KPPP Dialup with RCN.COM company"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by jamiefoxer on 2005-04-30
Hey guys,

I've about had it with dialup.  I personally don't use it, but my dad still lives in the stone age and won't change to Cox cable.  

So. I put Hoary on his computer, and had MAJOR problems just getting the damn Lucent Winmodem working (it is now).  When I try to dial RCN.com's access number, complete with my father's User ID and password, I get this bullshit.  I can't figure it out for the life of me.  Tried Pap, CHAP, Script Based authentications, and I can't seem to connect.  In windows, it just works.  In Linux, it's throwing me out with this error.  I'm only here setting up my dad's computer for the next hours.  I need very quick help.

Here's the error on the log.

"The remote system is required to authenticate itself"
"but I couldn't find any suitable secret (password) for it to use to do so."
"(None of the available passwords would let it use an IP address)"

Based on this error message, I'm guessing that RCN uses the "two-way authentication method" described in the KPPP Handbook, but I have NO idea how to enable the necessary settings for two-way authentication.  Any thoughts?

BTW - RCN won't give support for Linux.

---

### Post by jodef on 2005-04-30
I ran into this same problem a few days ago and while browsing the forums I found the solution taken from the [Kppp FAQ](http://docs.kde.org/en/3.4/kdenetwork/kppp/faq.html) 

> 10.1.2.	

pppd died - The remote system is required to authenticate itself ...
	

Typical error message in system log:

pppd[699]: The remote system is required to authenticate itself
pppd[699]: but I couldn't find any suitable secret (password) for it to use to do so.
pppd[699]: (None of the available passwords would let it use an IP address.)

As far as I can tell there are two causes for this problem:

*/etc/ppp/options contains the auth option. Simply put a # comment in front and try again.
    
*Your system already has a default route. Have you set up a local network? In this case recent versions of pppd will behave as if auth had been specified. To override this you may add noauth to the pppd arguments in kppp' setup dialog. Alternatively you could take down the local network prior to dialing in. I'd be thankful if someone could provide instructions on how to peacefully combine the two network connections.  

For me the first solution did the trick.

---

