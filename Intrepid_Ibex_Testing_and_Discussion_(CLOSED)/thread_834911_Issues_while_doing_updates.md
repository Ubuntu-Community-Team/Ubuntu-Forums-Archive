---
title: "Issues while doing updates"
date: 2008-06-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-06-19
Hi all, 
 There have been few issues while doing updates 

```

Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                             [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                             [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1

```

As well as these 

```

/usr/bin/mandb: warning: whatis for libcucul-ruby-api.3caca.gz exceeds 2048 bytes, truncating.

```

And lastly, 

```

update-rc.d: warning: multiuser is deprecated; specify runlevels manually

```

Now I know all the 3 cases should have different investigations and ways of finding out what the problems are. 

1. Timidity :- Is this the problem that is due to me moving to pulseaudio or something else altogether?

2. /usr/bin/mandb :- Is this truncation due to me using localepurge for deleting uncessary locales ?

3. update-rc.d :- Is this due to things moving to upstart?

So I may be on the right or the wrong track, please lemme know.

---

