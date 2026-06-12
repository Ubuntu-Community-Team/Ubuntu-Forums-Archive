---
title: "Internet OK, but synaptics freezes on updating?"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Mendokuse on 2008-09-22
Hi all,

A bit of a n00b to ubuntu and linux in general, and I've hit a pretty strange problem: 

I've just moved to the UK and am on Virgin broadband now. Internet connection seems to be peachy EXCEPT for the synaptics package manager, which gets stuck whenever it tries to check the repositories. 

What's even more strange is that there is no timeout and as far as I know there's no network proxy.

Also, when I try to manually wget a package which the manager has failed to get, it downloads ok!

I really have no clue what's going on and don't even know where to start.

If anyone has any ideas I'd be infinitely grateful.

---

### Post by leg on 2008-09-22
I had something similar to this once before and I found that I had to open System > Administration > Network and enter the dns address located on my router each time. I no longer have this problem though and mine works nicely now. Have a look and see if it helps.

---

### Post by Mendokuse on 2008-09-22
UPDATE - I've manage to get a partial fix on apt-get by editing out the proxy settings in /etc/apt/apt.conf; turns out that apt-get carried over the proxy settings from my previous connection (which used a proxy server) and Preferences>Network Proxy does not in fact so a system-wide change.

So now apt-get works but Synaptics still fails to download package lists. Checked synaptic's proxy settings and they are clean. Not sure what to think now.

Leg- thanks very much for the input, but how do you do what you described? I've not played with DNS settings before and don't have a clue how it works or where to begin.

---

### Post by leg on 2008-09-23
In my situation I took one of the DNS addresses that are set in my router and added it through the Network settings mentioned above. If you don't use a router then I am not sure where you would get the address from. If you do have a router log on to its admin web page (the ip to use will be in the documentation for it) and search around until you see an ip address that is listed as DNS (there will probably be two of them that only differ in the last part). These are the dns servers for your isp and may help you. I can't guarantee this will work for you as I am pretty sure that whatever caused this on my machine has been fixed since the last release (I am on 8.04) but it worked for me before but I did need to do it every time I wanted to use synaptic.

---

