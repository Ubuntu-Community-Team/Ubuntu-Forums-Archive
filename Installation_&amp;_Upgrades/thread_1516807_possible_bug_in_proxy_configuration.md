---
title: "possible bug in proxy configuration?"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by beanpole on 2010-06-24
I think I have encountered a problem in the way that lucid handles proxy servers.  I was having problems running apt-get update due to a firewall at my work.  I also noted that I was getting 403 Forbidden for wget.  So I went to System -> Preferences -> Network Proxy from my account (which has administrator privileges) and input the http address for the proxy server, and then clicked the button to "Apply Systemwide...". 

Following that change, wget worked from my account, but whenever I tried to sudo apt-get update, I got the 403 forbidden response again, even though I could wget the same files that apt-get reported as forbidden.  I figured that this was a problem with the root account, and so I typed

```
sudo -i
export http_proxy=[the http address of my proxy server]
apt-get update
```and voila, apt-get suddenly worked!  However, upon exiting from the root account, and trying to run sudo apt-get update again, I got the 403 forbidden code again!

So, it seems that the proxy settings are not being applied systemwide.

---

### Post by beanpole on 2010-06-24
note: using manual rather than automatic proxy configuration seemed to make the problem go away, I don't know why (since the same settings were used in both places)

---

