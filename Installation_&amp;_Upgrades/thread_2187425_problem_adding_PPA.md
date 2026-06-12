---
title: "problem adding PPA"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by prkhr4u on 2013-11-12
I am trying to add a PPA repository using this command:

```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
```

I am getting this error:
```
Traceback (most recent call last):  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")
```

I've seen one such similar post,but couldn't understand what is the solution.
Pl some1 tell how to add this PPA?

---

### Post by Frogs Hair on 2013-11-12
I had no problem adding the repository on 13.10 and I would suggest running the following command and try adding the repository again. ```
sudo apt-get update  
``` Of the five releases listed in the PPA  10.04(Desktop)  is no longer supported and its repository closed. Linking the other thread you wrote about might be helpful if you are not understanding the solution. 


[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by u2nTu on 2013-11-12
Is the problem that you get a bunch of errors as shown at top of page [here]("http://askubuntu.com/q/151494/165265")?

Just got this working myself and very happy to have the real ffmpeg installed. **Works great! **And it's really easy to do.

Made [this post]("http://askubuntu.com/a/373509/165265") in hopes of sharing with many. Have yet to find any incompatibilities with anything.

Hope it works for you.

---

### Post by prkhr4u on 2013-11-12
@Frogs Hair:
I had already updated all the packages with 
```
sudo apt-get update
```
and then only tried and using ubuntu 12.04 (desktop)

@u2nTu:
I went according to your post and agin getting the same errors on :
```
sudo apt-get purge libav-tools
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
```

Now going with the static build

---

### Post by u2nTu on 2013-11-13
@prkhr4u, Sorry, should have read your post more closely. The last line of output indicates that the problem originates not in software, but with your net connection. Specifically, you're not connecting to the PPA. So don't give up on the easy solution yet!

New mantra: "When I make a way to connect to the PPA, all will be ok."

First, are you using a proxy? If yes, check that both http_proxy and https_proxy environment vars are set, also their counterparts in ALL CAPS.

In more rare cases, the DNS server is the problem. To fix, assuming system defaults remain unchanged, you can try going into your router's interface and changing the DNS server to Google's, at 8.8.8.8. If that does the trick, then it's clear your ISP's DNS server was at fault.

Here's the thing: There's a problem connecting to the PPA, which means other connection problems await you. Installing the static build of ffmpeg is a workaround here, but if you don't resolve the underlying connection problem, what happens next time?

---

### Post by prkhr4u on 2013-11-13
yes i am using a proxy and have set http_proxy and https_proxy and also HTTP_PROXY AND HTTPS_PROXY.
I have checked all four and all are set correctly.
In fact i am using the setting saved in /etc/apt/apt.conf and also set ftp and socks also. So there is no problem with the proxy.
I am able to use internet in terminal and elsewhere.

Also,i am behind a company's proxy..so dont have access to the router's interface.
I do not feel the DNS server is at fault,because using the same network I am able to resolve the same address in my browser..so DNS should be correctly working

Any other solution??
will be greatly appreciated

---

### Post by prkhr4u on 2013-11-13
yes i am using a proxy and have set http_proxy and https_proxy and also HTTP_PROXY AND HTTPS_PROXY.
I have checked all four and all are set correctly.
In fact i am using the setting saved in /etc/apt/apt.conf and also set ftp and socks also. So there is no problem with the proxy.
I am able to use internet in terminal and elsewhere.

Also,i am behind a company's proxy..so dont have access to the router's interface.
I do not feel the DNS server is at fault,because using the same network I am able to resolve the same address in my browser..so DNS should be correctly working

Any other solution??
will be greatly appreciated

---

### Post by u2nTu on 2013-11-14
Ah, that changes the picture. Thought this was a home setup. At work, you're at the mercy of the sometimes-unhelpful network people. :evil:

Business firewalls implement measures (frequently out of paranoia) that often break things. That's likely what you're dealing with.

So while you could do some cursory diagnostics like:
```
nslookup launchpad.net
# Alternatively substitute 'dig' or 'host -v' for nslookup in the previous line.

```and
```
tracepath -b launchpad.net
```
, even if the trouble becomes apparent, you'd still have to approach a sysadmin to ask for a fix. Hope you work with good people there!

---

