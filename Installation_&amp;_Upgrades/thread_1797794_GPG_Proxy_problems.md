---
title: "GPG Proxy problems"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by mebigfatguy on 2011-07-05
I'm trying to install FreeNX, by first doing

sudo add-apt-repository ppa:freenx-team

I get 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv F3A662B57D580D3A2E98E5152A8E3034D018A4CE
gpg: requesting key D018A4CE from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: No route to host
gpgkeys: HTTP fetch error 7: couldn't connect: No route to host

I'm assuming that this is because i'm going through (or should be going through) a proxy. 

I have exported http_proxy and https_proxy, but it doesn't seem to do anything.

I've seen similar problems on this and other forums suggesting solutions, none of which for me do anything. Rather than keep trying the shotgun approach i was wondering if my basic assumptions are true.

1) GPG should use http_proxy and/or https_proxy
2) keyserver.ubuntu.com is in fact up (it is up thru http protocol)
3) the problem is with the proxy

(this is on natty)

---

### Post by Toz on 2011-07-05
Try this:
```
sudo visudo
```
and replace the line **Defaults env_reset** with:
```
Defaults env_keep += “ftp_proxy http_proxy https_proxy”
```

This should pass on your proxy settings.

---

### Post by mebigfatguy on 2011-07-06
no joy

gpgkeys: HTTP fetch error 7: couldn't connect: No route to host

---

### Post by Toz on 2011-07-06
Did you export http_proxy before running sudo? 

Another thing to try, for apt only, you can add:```
Acquire::http:proxy "http://MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
```to /etc/apt/apt.conf

Otherwise, you can always:
```
sudo bash
```
to start a root terminal, then
```
export http_proxy="<proxy_info>"
```
and then run any commands you require.

---

### Post by mebigfatguy on 2011-07-07
Yes, that's what my

/etc/apt/apt.conf

looks like

I know that my proxy is correct because i can hit

[http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/)

in a browser, and it works fine.

My hypothesis is, that GPG doesn't use http_proxy.

i tried export hkb_proxy=http://{my_proxy_server}

and that caused gpg to take a huge amount of time, but fail in the same way.

---

### Post by Toz on 2011-07-07
This looks relevant: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/733029]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/733029")

---

