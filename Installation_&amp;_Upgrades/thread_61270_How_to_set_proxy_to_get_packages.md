---
title: "How to set proxy to get packages?"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by snpz on 2005-08-31
Hi folks,
i installed ubuntu base system. After PC reboot i can't get packages to install, because for me internet works only through proxy server. Is it possible to set proxy server address before geting all packages?

---

### Post by snpz on 2005-08-31
Anyone?

---

### Post by odin on 2005-08-31
It's a pleasure for me to answer this question(well I think you are asking about how to use apt or synaptic through a proxy) but now I understand why other people in this forum told sometimes before to look a thread that can help me before starting a new one.So next time try to look a bit because as far as I remember this is answerd in at least 2 or 3.

well after telling you all this crapy things(I sounded like a teacher I had in high school I really hated ;-) ) here is the answer I think.


edit /etc/apt/apt.conf.d/proxy

then write this:

Acquire::http::Proxy "http://your_proxy_IP : port_used_by_the_proxy";

that's for apt.In synaptic just go to preferences to tell synaptic where is your proxy.

Hope it helps and sorry for my introduction.

---

### Post by snpz on 2005-08-31
At first thank u for your reply!:) I will try to check out how it works!
Next time i will search through the topics to find out is there already aswer to question i'm interested in!:)

---

### Post by yesidh on 2005-09-30
But I require Authentification in the proxy, where I can write my username and password in Synaptic?, I have it working with apt-get

---

### Post by johnfound on 2005-10-07
[QUOTE=yesidh]But I require Authentification in the proxy, where I can write my username and password in Synaptic?, I have it working with apt-get[/QUOTE]

Hi, all. There is a big problem with these proxies. The trick: username:password@proxy doesn't work for me neither in apt-get nor synaptic. There is an error message: " 407 Proxy Authentication Required". The proxy is some MS ISA server of something similar...
In the same time, Mozilla Firefox works just fine...it simply asks me about the username and password and I use the format: "domain\username" for the username.
Help, please.

Regards.

---

### Post by johnfound on 2005-10-07
Hm, did someone knows is it possible to set synaptic to work with MS proxy in principle???

---

### Post by johnfound on 2005-10-08
Again after 23 hours with no response... :(
I suppose it is imposible... too sad... did I have to try Linux after several years again? Maybe then it will be possible to install software other than in distribution CD...

---

### Post by odin on 2005-11-15
well you can install everything you want with apt.I couldnt tell you about synaptic cause I never use it,I've been a kind of busy all this time....

---

### Post by josuemb on 2005-11-16
Set http_proxy:

export http_proxy=http://user:password@proxy:port

this works for me but i dont know how to stablish this value for future sessions.

Somebody knows?

Thank you.

---

### Post by ankush_jhalani on 2005-11-16
Tht was exactly the question i wanted to knw, but a friend helped me..
the 
export http_proxy thing works fine for me, now if someone can tell how to set these path value for all future session..:rolleyes:

---

### Post by SnEptUne on 2005-11-18
[QUOTE=ankush_jhalani]Tht was exactly the question i wanted to knw, but a friend helped me..
the 
export http_proxy thing works fine for me, now if someone can tell how to set these path value for all future session..:rolleyes:[/QUOTE]

How about putting the "http_proxy thing" in /etc/environment?  That would set the environment variable globally.

---

