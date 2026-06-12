---
title: "Edgy 6.10 : why 127.0.1.1 is set to the local host name ? Annoying and not required."
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by mswoon on 2006-10-29
I have kerberos set up for my Drapper machines (three) and got them all installed (fresh install, upgrade failed on two computers and I am not trying that again) with Edgy and thankfully, kerberos worked. So, ssh from host A to hosts B and C worked fine, no password required. But ssh from host A to host A failed! Why? Because host A is defined in /etc/hosts as 127.0.1.1 and therefore it got confused! My hosts are all, say, toshiba.example.com and defined that way for kerberos. I have a local DNS so that ssh toshiba is translated to the FQDN, but obviously if the localhost name is defined in /etc/hosts, ssh does not query DNS. So ssh toshiba fails on toshiba but ssh toshiba.example.com works on toshiba (yes, my host keys for toshiba is host/toshiba.example.com, has to, as otherwise other hosts can't get to it). Why is this definition necessary? I commented it out and things appear to work fine.

---

### Post by Najand on 2006-10-29
127.0.0.1 is the standard IP address used for a loopback network connection.
This means that if you try to connect to 127.0.0.1, you are immediately looped back to your own machine. If you don&t need that or if it conflicts with other IP addresses on your network, just remove it. There is not a big deal about that.

---

### Post by mswoon on 2006-10-30
Thanks for replying. But I am already aware that 127.0.0.1 is the loopback address. That's not what I am pointing out. 

What am I pointing out then? Please read the post title and text again :-). 

> **Najand said:**
> 127.0.0.1 is the standard IP address used for a loopback network connection.
This means that if you try to connect to 127.0.0.1, you are immediately looped back to your own machine. If you don&t need that or if it conflicts with other IP addresses on your network, just remove it. There is not a big deal about that.

---

### Post by sgornick on 2006-11-10
FYI, I see the same thing in Dapper,

$ cat /etc/hosts
127.0.0.1 localhost myhostname
127.0.1.1 myhostname

[snipped]

I see lots of discussion on this on the Debian bug tracking system:
[http://www.us.debian.org/Bugs/](http://www.us.debian.org/Bugs/)
#247734
#316099
#267321

The part that explained it for me:
"most services that listen locally listen on all 127/8 addresses, not just on 127.0.0.1."

But then the system hostname was added as an alias to localhost which makes moot, as far as I can tell, the assignment for 127.0.1.1 -- so I have no idea why the 127.0.1.1 would still be put in there.

---

