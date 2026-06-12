---
title: "URGENT HELP NEEDED: upgrade to 9.10 spamd and amavisd broken in perl"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2009-12-13
Ok, I'm in dire need of perl expertise.

I had a working mail/web server under Ubuntu 9.04 with ISPConfig 3. Everything worked fine. I tested upgrade on a notebook that is pretty close, but doesn't have most of the e-mail stuff and that went fine. So, I tried to update the server and its nothing but problems.

So, I'm now down to the final 2 problems and they seem to be related.

Spamassassin (spamd) and amavis (amavisd) are puking big time in perl and filling up the system log with the same message(s) and using 100% cpu.

Here's the error:

```
from amavisd in debug mode

Use of uninitialized value $fam_listen in numeric ne (!=) at /usr/share/perl5/IO/Socket/INET6.pm line 182

from spamd in /var/log/syslog

Dec 13 16:15:35 inferno spamd[2805]: Use of uninitialized value $fam_listen in numeric ne (!=) at /usr/share/perl5/IO/Socket/INET6.pm line 182.
```

---

### Post by DantePasquale on 2009-12-13
OK, I got spamassassin working by telling it to only use IPv4 in the defaults file:

```
 /etc/default/spamassassin
# Duncan Findlay

# WARNING: please read README.spamd before using.
# There may be security risks.

# Change to one to enable spamd
ENABLED=1
# ENABLED=0

# Options
# See man spamd for possible options. The -d option is automatically added.

# SpamAssassin uses a preforking model, so be careful! You need to
# make sure --max-children is not set to anything higher than 5,
# unless you know what you're doing.

OPTIONS="**--ipv4-only** --create-prefs --max-children 5 --helper-home-dir"
```

---

### Post by DantePasquale on 2009-12-13
Ok. I found a post on zimbra forums and I needed to install a cpan ipv6 module:

```
run perl -mIO::Socket::INET6 -e ''

if it returns "Can't locate IO/Socket/INET6.pm in @INC ", then you need to install the perl module.

perl -MCPAN -e shell
cpan[1]> install IO::Socket::INET6
```

Here's where I found the info: [http://forums.cpanel.net/f5/spamassassin-missing-library-128705.html]("http://forums.cpanel.net/f5/spamassassin-missing-library-128705.html")

---

### Post by phillw on 2009-12-13
> **DantePasquale said:**
> OK, I got spamassassin working by telling it to only use IPv4 in the defaults file:

```
 /etc/default/spamassassin
# Duncan Findlay

# WARNING: please read README.spamd before using.
# There may be security risks.

# Change to one to enable spamd
ENABLED=1
# ENABLED=0

# Options
# See man spamd for possible options. The -d option is automatically added.

# SpamAssassin uses a preforking model, so be careful! You need to
# make sure --max-children is not set to anything higher than 5,
# unless you know what you're doing.

OPTIONS="**--ipv4-only** --create-prefs --max-children 5 --helper-home-dir"
```

IMHO - upgrading a server from 9.04 --> 9.10 is a risky business. Mine went fine, but I only have a bog standard LAMP installation.

I've skipped putting a mail server onto 9.10, as I see 9.10 as nothing more than a stepping stone to 10.04 LTS for the server side of things & I wanted to get used to Grub2 & ext4. (Don't flame me on this one - I'm not the only one using 9.10 as an upgrade route to see how our kit gets on with the 'new' stuff).

You could always do a force complete remove of your 2 packages and re-install them - that way they'd be 9.10 savvy. 

I've got the joys of popping this --> [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)  onto my LAMP server on 10.04 Alpha.  Should keep me out of trouble for a while ;-)

The guyz & galz over on the Server Area --> [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Will, most likely, be better able to assist you. One of them has probably had the same problem.

Regards,

Phill.

---

### Post by DantePasquale on 2009-12-15
Most of the issues I had in the upgrade were mitigated by disable IPv6 in the kernel, buy updating the grub menu.lst for the kernel with the param to disable IPv6. Having one more issue but will post to server forum as suggested. Thanks for the ideas on LTS ... I try to be an early adopter 'cause I enjoy pain ;)

---

