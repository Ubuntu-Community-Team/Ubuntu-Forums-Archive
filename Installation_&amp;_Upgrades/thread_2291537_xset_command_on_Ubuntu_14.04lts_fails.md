---
title: "xset command on Ubuntu 14.04lts fails"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by jhetrick62 on 2015-08-20
I need to use the xset command to add a remote server directory for use in redirecting my pharmacy system software correctly.

I have run this on Ubuntu 12.04 LTS for 3 years and tested this again, so the issue isn't the remote server, it is the Ubuntu 14.04 LTS build.

On 12.04 I can run the following code:

```
 xset +fp tcp/10.100.0.254:7100 
```

It works fine and when running ```
xset q 
``` 
to review my settings, it has added the remote server properly.  After that I run
```
ssh -X user@10.100.0.254 
```
and have no issues, it tunnels the X screen back and it is proper.

On Ubuntu 14.04 LTS when I run the EXACT SAME xset command I get the following error, so there must be a permission issue with adding it to the x server on the 14.04, but I can't see it anywhere when I review the X files.

Error gotten:
[HTML]jhetrick@ms0419-rph:~$ xset +fp tcp/10.100.0.254:7100
xset:  bad font path element (#0), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
[/HTML]

Then I check the settings with ```
xset q
``` and sure enough, the setting was NOT added!

What has changed and/or what permissions need to be updated on the 14.04 LTS system?  Again, it works fine on 12.04 LTS.

Thank you!

---

### Post by steeldriver on 2015-08-21
Hmm... don't have any experience with fontservers, however if I was trying to diagnose this on my own network probably the first thing I'd try to check is basic connectivity to the port e.g. using telnet

```

telnet 10.100.0.254 7100

```

---

### Post by jhetrick62 on 2015-08-21
Yes, I can telnet into the server.  That is not the issue.  FInd this entire thing a problem as it has worked for 3 years, so now I dare not update the original boxes.

---

