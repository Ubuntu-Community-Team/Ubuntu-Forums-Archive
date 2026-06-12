---
title: "What does this &quot;sed&quot; command do?"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by ufuser01 on 2011-11-15
Hi,
 I am trying to understand what this command does. It looks like, it extracts something (/usr/prog1/bin) from the PATH and appends it to /etc/environment . Please let me know if this is right:

sudo sed -i 's/\(PATH=\"\)/\1\/usr\/prog1\/bin:/' /etc/environment

Thanks.

---

### Post by crazy bird on 2011-11-15
You can find the answer here:
[http://linux.about.com/od/commands/l/blcmdl1_sed.htm](http://linux.about.com/od/commands/l/blcmdl1_sed.htm)
 
If you want to learn more about Linux commands, just use google and type "linux commands":
[http://www.google.nl/search?q=linux+command&hl=nl&source=hp&gs_sm=e&gs_upl=1469l4672l0l7031l16l14l0l2l2l0l297l2111l2.5.5l12l0&oq=linux+command&aq=f&aqi=g10&aql=](http://www.google.nl/search?q=linux+command&hl=nl&source=hp&gs_sm=e&gs_upl=1469l4672l0l7031l16l14l0l2l2l0l297l2111l2.5.5l12l0&oq=linux+command&aq=f&aqi=g10&aql=)
 
Everything you want to know is available on the internet.

---

### Post by Vaphell on 2011-11-15
replace (**s**///) in place -i (as in 'modify file', sed by default only prints out to terminal)
PATH= -> PATH=/usr/prog1/bin:
(PATH=) in parentheses is a selection group - it means that you can get that 'PATH=' with \1 in the replacement. If there are more () you go in order \1 \2 \3...

btw why the hell people do all that escaping -_-
-r removes the need for that in case of ()[] etc and you can use different separator than / (any symbol put after **s** will be used to separate the parts)
```
$ echo PATH=$PATH
PATH=/home/me/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$ echo PATH=$PATH | sed -r **'s_(PATH=)_\1/what/ever:_'** 
PATH=/what/ever:/home/me/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

