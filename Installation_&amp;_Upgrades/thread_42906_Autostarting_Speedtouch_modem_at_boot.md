---
title: "Autostarting Speedtouch modem at boot?"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by reddeathdrinker on 2005-06-19
Well, I finally got my Speedtouch modem working with Hoary (Warty was a stroll in the park by comparison!)

I found that the speedtouch.conf script was the only way round the whole mess.

Anyway, at the end of the script, after it's connected me, I get the following messages...

```

Looks like we're online...
Hey look, I can see the Net from here!
Configuration finished.
Any potential problems are listed below:
[COLOR=Red]To automatically dial-in when the PC boots up :
/usr/lib/lsb/install_initd /etc/init.d/speedtouch
Do you want to set this up now? (Yes / No)
y
Traceback (most recent call last):
  File "/usr/lib/lsb/install_initd", line 46, in ?
    headers = initdutils.scan_initfile(initfile)
  File "/usr/lib/lsb/initdutils.py", line 78, in scan_initfile
    inheaders = RFC822Parser(strob=headerlines)
  File "/usr/lib/lsb/initdutils.py", line 17, in __init__
    raise ValueError, 'need a file or string'
ValueError: need a file or string
init command failed[/COLOR]
You can still stop and start the interface with
  /etc/init.d/speedtouch stop
  /etc/init.d/speedtouch start
You are now connected. There is no need to run this
speedtouchconf.sh script again.
Congratulations.

```

Anyhow, the bit in RED above is the bit I'm on about. How can I work round this, and get my connection to start at boot?

Cheers,

Ali

---

