---
title: "Synaptic proxy: special characters"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by zagor on 2005-11-28
Hi all,

I'm trying to let synaptic work behind my company firewall.
I've read all the stuff saying to fill in the proxy like
[http://my.user:mypassw@my.host:port](http://my.user:mypassw@my.host:port)
but I still have problems, probably because my user name to access the proxy contains a space.
I've tried something like:
my user:passw@my.host:port
my\ user:passw@my.host:port
'my user':passw@my.host:port
"my user":passw@my.host:port

and similar, but always without success.
Any suggestion?

Freshly installed Breezy on a IBM T40 laptop.

---

### Post by zagor on 2005-11-29
I've found the solution, by chance.
The trick is not to write "http://" in the field.
So to let it work I just had to write in the HTTP proxy field this:
my name:passwd@my.host
the port should only be indicated through the dedicated field.

So now synaptic is working, but apt-get is not.
I've followed several of the indications found on the internet, but none seems to work, with my username containing spaces.
This link was especially useful: [http://ubuntuforums.org/archive/index.php/t-1575.html](http://ubuntuforums.org/archive/index.php/t-1575.html)

any suggestion?

---

### Post by zagor on 2008-01-21
I've found the solution long ago, but forgot to post it.
Here it is, in case someone cares:

Edit /etc/apt.conf.
In my case it was empty.
I've added the following:
```
};
ACQUIRE {
http::proxy "http://my username:password@my.server.address:portnumber/"
}

```

Also, edit /etc/wgetrc and uncomment lines 76 and 80 and edit with yout parameters.
My file now shows:

```
# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = http://my username:password@my.server.address:portnumber/
#ftp_proxy = http://proxy.yoyodyne.com:18023/

# If you do not want to use proxy at all, set this to off.
use_proxy = on

```

---

