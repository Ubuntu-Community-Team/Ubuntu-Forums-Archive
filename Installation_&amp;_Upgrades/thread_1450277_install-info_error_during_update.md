---
title: "install-info error during update"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by beemzet on 2010-04-08
Hi all, I'm using ubuntu 10.04 beta 1. when I try to update & upgrade I get the following error:

```

Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: LC-ALL=en_US.UTF-8: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info


```

Anyone knows how to fix this?
Thanks

---

### Post by beemzet on 2010-04-09
> **beemzet said:**
> Hi all, I'm using ubuntu 10.04 beta 1. when I try to update & upgrade I get the following error:

```

Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: LC-ALL=en_US.UTF-8: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info


```

Anyone knows how to fix this?
Thanks


Never mind, I figured it out.
In /etc/environment file I had to change this:

    4 LC-ALL="en_US.UTF-8"

to this:

    4 LC_ALL="en_US.UTF-8"

---

### Post by Fatman_UK on 2010-05-05
> **beemzet said:**
> Never mind, I figured it out.
In /etc/environment file I had to change this:

    4 LC-ALL="en_US.UTF-8"

to this:

    4 LC_ALL="en_US.UTF-8"

To my complete astonishment, this fixed my install-info woes. Thanks! In the same file, I commented out the line:

POVRAY_BETA=`povray --betacode 2>&1`

and all was well. I guess the upgrade doesn't like the broken povray beta.

---

### Post by TeAmigo on 2010-10-26
I was getting a very similar error, but with exit status 1. No reference to /etc/environment in the error message, very cryptic and lacking any helpful information. BUT, after reading a few posts where problems in /etc/environment were reported, looked at my own and discovered that there was a line in there that really should be in ~/.bashrc, but hadn't caused any trouble before. This:
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"
which is for the Ruby Version Manager. Took that out and install works again. So, taking EVERYTHING out of /etc/environment if this problem presents might be a good first approach.

> **beemzet said:**
> Hi all, I'm using ubuntu 10.04 beta 1. when I try to update & upgrade I get the following error:

```

Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: LC-ALL=en_US.UTF-8: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info


```Anyone knows how to fix this?
Thanks

---

### Post by juliayahf on 2011-01-08
> ** said:**
> It is exactly what I need, Thanks for your [[COLOR=#000000]analysis[/COLOR]](http://www.skyblank.com/sk/business/doorstep-loans-easy-credit-at-home.html)!

---

### Post by HariharanS on 2012-08-21
I was struggling with this problem for 5 days straight. I had to configure NTP server on my machine and it was not possible without this small change that changed the world for me. Even the updates on my machine were not happening due to this.

This is what I did:

I changed the first line of ***/etc/environment*** from: 

**VTYSH_PAGER = more**

to:

**VTYSH_PAGER=more**

And it started working. I hope this one could help.

---

