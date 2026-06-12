---
title: "Unable to update"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by tom17 on 2011-06-23
Hi,

I have 11.04 installed on a spare machine at work. All of a sudden, a couple of days ago, installing packages or updates started failing.

```
$ sudo aptitude update
Err http://ca.archive.ubuntu.com natty InRelease

Err http://ca.archive.ubuntu.com natty-updates InRelease

Err http://security.ubuntu.com natty-security InRelease

Err http://extras.ubuntu.com natty InRelease

Err http://ca.archive.ubuntu.com natty Release.gpg
  Unable to connect to 172.22.4.200:8080:
Err http://security.ubuntu.com natty-security Release.gpg
  Unable to connect to 172.22.4.200:8080:
Err http://ca.archive.ubuntu.com natty-updates Release.gpg
  Unable to connect to 172.22.4.200:8080:
Err http://extras.ubuntu.com natty Release.gpg
  Unable to connect to 172.22.4.200:8080:
Err http://dl.google.com stable InRelease

Err http://dl.google.com stable Release.gpg
  Unable to connect to 172.22.4.200:8080:

```

Now I checked with a browser and wget and I am able to get to all of the domains mentioned even though aptitude appears not to be able to. I am also able to use wget to fetch the files such as [http://ca.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg).

Now, we did recently change our internet access at work. It used to be proxies (which did not work too well with Ubuntu and updates) but we are now using some DPI firewall, I believe. From what I can tell, the URL that I go to with wget is the same URL that aptitude/apt-get is using, yet they fail and wget does not. Could the DPI be looking at the host header sent in the HTTP requests from aptitude? Is it possible to check/change what it sends as its host header? Do they use port 80? (i'm not sure where that 172.11.4.200:8080 is coming from).

Or could it just be another problem with aptitude? I saw some people with similar errors on here but nothing helpful to me.

Thanks,

Tom...

---

### Post by Elfy on 2011-06-23
Check if it's still looking for the proxy - maybe /etc/apt/apt.conf or have a look in the Settings> Preferences> Netowrk of synaptic.

Other than that not sure - wait for the next person along.

---

### Post by tom17 on 2011-06-23
haha

/etc/apt/apt.conf

```
ACQUIRE {
http::proxy "http://172.22.4.200:8080/"
}
```

And now it works!

I wonder why it suddenly broke. Looking again, I realise that proxy is one *i* set up and havent run for ages. Maybe I havent run aptitude for ages and didn't realise it.

Thanks for the help.

*slaps head*

Tom...
(Now I can't remember what I was trying to install 3 days ago lol)

---

### Post by Elfy on 2011-06-23
```
sudo apt-get install personal-memory-upgrade
```
was that it ? :lol:

Glad that helped anyway.

---

### Post by tom17 on 2011-06-23
Damn, unable to locate package. I can wish. Yeah, I have a **** memory :(

Thanks again!

Tom...

---

