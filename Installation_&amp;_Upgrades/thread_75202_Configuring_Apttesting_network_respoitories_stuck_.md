---
title: "Configuring Apt/testing network respoitories stuck at 50% during install"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by LuckyPhil on 2005-10-13
I retried installing several times. dhcp configuration failed (as it should) and I specified a static IP, dns and gateway as I have for every other linux install I have done (including SUSE 10 which lasted on my computer a whole 3 hours (oh so slow!))

Anyhoo, after specifying a username and password the installer says configuring apt, then checks the CD and then says testing network repositories where it sits... and sits... and sits... on 50%

I am installing now and selected the option to not configure network now and I hope this goes better, I am past configuring apt and am rebooting where the setup is continuing as I speak.

I am posting this both to advise other having the same problem how to gix this, and also to advise the developers to have some sort of timeout so that should the network settings not work properly (i'm assuming it's because I have a wired as well as wireless lan) that this part can be skipped.

Cheers & beers.

---

### Post by agentgray on 2005-10-13
Same here.  However, I do have DHCP running. Could it just be the load cause of all the downloads?

---

### Post by Roman27 on 2005-10-13
It hung there for me a while too.  But then it proceeded to the next thing after 10-15 minutes or so.

---

### Post by devkelso on 2005-10-13
If you have a network proxy:

A very poorly documented feature of debian-installer is setting the proxy environment variable. To do this try the following:

* boot from cdrom (or any other install type but thats a different topic)
* at the "Boot: " prompt type "install http_proxy='<my proxy server ip or dns><proxy port>'"
* install as normal

---

### Post by agentgray on 2005-10-14
[QUOTE=devkelso]If you have a network proxy:

A very poorly documented feature of debian-installer is setting the proxy environment variable. To do this try the following:

* boot from cdrom (or any other install type but thats a different topic)
* at the "Boot: " prompt type "linux http_proxy='<my proxy server ip or dns><proxy port>'"
* install as normal[/QUOTE]
I don't have a network proxy.  However, I noticed that it is much quicker on all the other machines today.  Maybe 2-3 minutes compared to 10-15.

---

