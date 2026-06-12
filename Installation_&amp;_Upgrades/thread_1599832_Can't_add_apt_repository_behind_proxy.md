---
title: "Can't add apt repository behind proxy"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by deesto on 2010-10-18
My machine is sitting behind an HTTP proxy.  I have apt-get, aptitude, etc., all working by setting http_proxy in wgetrc and in apt.conf.  But when I try to add a repo using add-apt-repository, it fails with "Connection Refused", whether I try as myself with sudo or as root.  I've also tried explicitly exporting http_proxy before running the command, but it doesn't help:
```
# **export http_proxy=http://*my.proxy.host:port***
# **add-apt-repository ppa:freenx-team**
Error reading https://launchpad.net/api/1.0/~freenx-team/+archive/ppa: <urlopen error [Errno 111] Connection refused>
```

I think I've already covered all the information given here:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

What else can I try?

---

### Post by efflandt on 2010-10-18
Did you try setting System > Preferences > Network Proxy?  That is where you would set a general proxy instead of having to set it in each application.  See if or what that sets in env.

Otherwise, all env variable "names" seem to be capitalized, so maybe try export HTTP_PROXY=...

---

### Post by deesto on 2010-10-18
Hi efflandt,
> **efflandt said:**
> Did you try setting System > Preferences > Network Proxy?  That is where you would set a general proxy instead of having to set it in each application.  See if or what that sets in env.Yes; in my system-wide prefs, I have all protocols set to the same proxy, so this sets a bunch of *_proxy env values.

> Otherwise, all env variable "names" seem to be capitalized, so maybe try export HTTP_PROXY=...True that most system-wide variables have caps names, but not always the case with proxy stuff, it seems.  At any rate, exporting HTTP_PROXY with my proxy value didn't work either.  I saw also a value called ALL_PROXY, and tried setting that (lowercase as well as upper), but no luck.

---

### Post by vicky.it.bhu on 2010-10-27
Same Problem

---

### Post by KernelKludge on 2010-11-04
System > Preferences > Network Proxy sets all the *_proxy environment variables that most apps use. However, the APT system often runs outside your user environment and needs to be configured separately. Seemingly from your experience, some APT programs don't exactly use those environment variables. :-(

I suggest adding the following to /etc/apt/apt.conf.

```
Acquire::http::Proxy "http://my.proxy.host:port";
```

Ref. [http://manpages.ubuntu.com/manpages/intrepid/man5/apt.conf.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/apt.conf.5.html)

Annoyingly, it seems the 10.10 desktop installer no longer has the capability to configure an network proxy and, thus, create /etc/apt/apt.conf for you.

---

### Post by deesto on 2010-11-05
> **KernelKludge said:**
> http://manpages.ubuntu.com/manpages/intrepid/man5/apt.conf.5.html[/url]Thanks, but I tried that from the beginning (see 1st post).  Doesn't help at all.

---

### Post by mahdif62 on 2010-11-26
The workaround is here:

[http://gurrier.wordpress.com/2010/10/02/downlolading-repo-keys-from-behind-a-corporate-firewall/](http://gurrier.wordpress.com/2010/10/02/downlolading-repo-keys-from-behind-a-corporate-firewall/)

---

### Post by deesto on 2010-12-06
> **mahdif62 said:**
> The workaround is here:

[http://gurrier.wordpress.com/2010/10/02/downlolading-repo-keys-from-behind-a-corporate-firewall/](http://gurrier.wordpress.com/2010/10/02/downlolading-repo-keys-from-behind-a-corporate-firewall/)
Hmmm ...
```
$ **sudo gpg –keyserver hkp://keyserver.ubuntu.com:80 –recv-keys 0A5174AF** 
gpg: WARNING: unsafe ownership on configuration file `/home/me/.gnupg/gpg.conf'
usage: gpg [options] [filename]
```

---

### Post by T.Ephraim on 2011-05-24
> **deesto said:**
> Hmmm ...
```
$ **sudo gpg &#8211;keyserver hkp://keyserver.ubuntu.com:80 &#8211;recv-keys 0A5174AF** 
gpg: WARNING: unsafe ownership on configuration file `/home/me/.gnupg/gpg.conf'
usage: gpg [options] [filename]
```

Just remove the sudo and change &#8211;keyserver and &#8211;recv-keys to --keyserver and --recv-keys.
```
gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0A5174AF
```

Stupid Encoding!

However for me this doesn't fix the problem:
> Error reading ..... <urlopen error [Errno 111] Connection refused>

Ciao Epraim

---

### Post by T.Ephraim on 2011-05-24
Finally! :)

you need to set httpS_proxy via
```
export https_proxy=....
```
only set http_proxy is not enough.
And I needed to execute the add-apt-repository command as root, NOT via sudo.

```

sudo su
add-apt-repository ppa:........

```

Ciao Ephraim

---

### Post by awi on 2011-07-27
Thank you, worked for me too.

> **T.Ephraim said:**
> Finally! :)

you need to set httpS_proxy via
```
export https_proxy=....
```
only set http_proxy is not enough.
And I needed to execute the add-apt-repository command as root, NOT via sudo.

```

sudo su
add-apt-repository ppa:........

```

Ciao Ephraim

---

### Post by deesto on 2011-08-01
> **T.Ephraim said:**
> Finally! :)

you need to set httpS_proxy via
```
export https_proxy=....
```
only set http_proxy is not enough.
And I needed to execute the add-apt-repository command as root, NOT via sudo.

```

sudo su
add-apt-repository ppa:........

```

Ciao Ephraim

Are you sure this wasn't due to some change between 10 and 11?  Are you still running 10.04 (or 10.10)?

My first question was going to be why setting `ALL_PROXY=` wouldn't cover HTTPS, but it seems in 11.04 that `ALL_PROXY` does not exist (at least not by default).

---

