---
title: "Problem with apt-get proxy on ubuntu server ed"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by damoek on 2008-01-15
I have an issue, I am trying to install the xubuntu-desktop on a ubuntu server system i have at work. Since its command line only i'm having trouble with getting an ssh proxy to work. We have web filtering software that causes some of the updates using apt-get to fail. I have an ssh server at  home that I can tunnel through. I have read how to configure the http_proxy so that i can use this to get my apt-get updates. My problem is that when I ssh to my home server using

```
ssh -D 8080 server.myhomeubuntu.org 
``` it connects me on the first tty to my home ubuntu bash shell

from the second tty i then attempt to connect to the proxy

```
http_proxy="http://127.0.0.1:8080"
export http_proxy
sudo apt-get update
```

I always get connection failed. 
It seems like the tunnel is only live on tty1 so when i connect to tty2 i get nothing. 

Am I doing something wrong?

---

### Post by damoek on 2008-01-18
It has been a couple of days... 

I guess what I really want to know is, is it possible to ssh to a remote server bind a port to SOCKS using the -D command and then use that port as a proxy for apt get, all strictly from the command line? 

I have seen a lot of threads that refer to this, but mostly everyone is running some type of graphical user interface and has no issue going into synaptic and configuring a proxy. I haven't seen a single thread that deals with a user going strictly through ttys on a server install.

---

### Post by damoek on 2008-02-01
I'm going to bump this one up as I would really like an answer to it... Could someone help? I'd be glad to give additional information, or just be directed somewhere if possible.

---

