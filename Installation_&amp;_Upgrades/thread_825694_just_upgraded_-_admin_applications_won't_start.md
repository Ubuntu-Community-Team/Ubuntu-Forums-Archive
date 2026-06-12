---
title: "just upgraded - admin applications won't start"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by kstella on 2008-06-11
I upgraded to Hardy only yesterday. When I started up again, I saw that there were updates waiting. There were also other things I wanted to do: install programs, change settings, etc.

Every time I try to do those things, I see the little button/bar at the bottom that says "Starting Administrative Application." But nothing ever comes afterward. No window, nothing. :| Any ideas?

---

### Post by PmDematagoda on 2008-06-11
Post the outputs of:-
```
hostname
```
and
```
cat /etc/hosts
```

---

### Post by kstella on 2008-06-12
> stella

and

> 
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.10 stella.CERSA

I'm not using that IP anymore, though, so now I also wonder why that came out. :p

---

### Post by PmDematagoda on 2008-06-12
First boot Ubuntu in Recovery Mode, then backup the hosts file with:-
```
cp /etc/hosts /etc/hosts.bak
```
and after that's done, open the hosts file for editing with:-
```
nano /etc/hosts
```
and edit it to look like this:-
```
127.0.0.1 localhost
**127.0.1.1 stella**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Then save the file and see if the problems are now solved.

---

### Post by kstella on 2008-06-12
Okay. Which option do I choose at the end of the recovery mode sequence? I chose "resume with normal boot" but couldn't get past the first step in the terminal; I got "permissions denied."

Also, what's nano?

Thanks.

---

### Post by PmDematagoda on 2008-06-13
Don't choose "resume with normal boot", instead press the option that allows you to be dropped to a terminal.

And nano is a command line text editor built-in to Ubuntu.

---

### Post by kstella on 2008-06-13
It didn't work. :( I'm sure I did everything that you said.

---

### Post by PmDematagoda on 2008-06-13
Post the outputs of:-
```
hostname
```
and
```
cat /etc/hosts
```
again.

---

### Post by kstella on 2008-06-13
```
stella
```

and

```
127.0.0.1 localhost
127.0.1.1 stella

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The first time I read your reply, I saw that I'd forgotten to write "stella" at the end of the second line. Guess I wasn't so sure after all, sorry. :) So, I went back and added it.

The next time I tried starting an admin application, it was about ten minutes between entering the password and the actual appearance of the window. When the window DID appear, though, the system crashed! :(

But everything seems to be working fine now; no more gap between. Would you know what happened and if I should still be worried?

Thanks.

---

### Post by PmDematagoda on 2008-06-13
Does the system still crash when starting administrative applications? If not then all should be fine.

---

### Post by kstella on 2008-06-13
No longer. Thank you very much, PmDematagoda! :D

---

