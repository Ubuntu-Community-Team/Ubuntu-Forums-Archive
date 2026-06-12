---
title: "[SOLVED] 111 connection refused during update?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2008-04-29
I recently upgraded from dapper to gutsy, and was advised to upgrade not to hardy, which I am no opposed to at this point. I am, however, confused as to why I am unable to install the updates when they are available. I have 8 updates ready at this moment, but continue to get this error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

I don't understand this. Please help me to know what this means and how to fix it.

---

### Post by Monicker on 2008-04-29
> **sp0nge said:**
> I recently upgraded from dapper to gutsy, and was advised to upgrade not to hardy, which I am no opposed to at this point. I am, however, confused as to why I am unable to install the updates when they are available. I have 8 updates ready at this moment, but continue to get this error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

I don't understand this. Please help me to know what this means and how to fix it.

Hrmm. Somebody had the same issue in another thread earlier today.  Are you configured to go through a proxy server?

---

### Post by sp0nge on 2008-04-29
Sorry if I'm posting repetitive issues, I searched and haven't found anything to help thus far. 

No. I am not configured through a proxy server.

---

### Post by Monicker on 2008-04-29
> **sp0nge said:**
> Sorry if I'm posting repetitive issues, I searched and haven't found anything to help thus far. 

No. I am not configured through a proxy server.

But it is attempting to connect to localhost on port 4001, unless you are running some type of proxy service, that connection won't leave your local machine.

---

### Post by sp0nge on 2008-04-29
Is there a way to change this? I have not modified any of the repository info since I upgraded. In fact, I have done little more than install dapper from the live CD and upgrade to Gutsy through Synaptic. How do I change this so the update manager can install the updates?

---

### Post by sp0nge on 2008-05-02
Just a bump for new asnwers. I suppose I'm just not *nix literate enough to understand Gutsy. I will hold off in hopes someone can help me address this issue through the weekend, but I am prepared to revert back to Fiesty so I can have the updates and can install packages without this craziness. This is only the second error with Ubuntu that I have not been able to overcome, still much better than the track reccord windows has with me.

Please offer suggestions or education as to why the update manager is looking at the local machine for these updates. I just don't understand how that happens, as I have changed nothing about the system. 

Thanks in advance.

---

