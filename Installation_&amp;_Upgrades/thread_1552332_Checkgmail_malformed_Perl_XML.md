---
title: "Checkgmail malformed Perl XML"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by benjabean1 on 2010-08-13
After installing checkgmail, I ran it under the command line, and it gave me this output:

```
not well-formed (invalid token) at line 15, column 25, byte 447 at /usr/lib/perl5/XML/Parser.pm line 187
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached
```

Running with the switch -v gives me the same output. If I run checkgmail like this:

```
checkgmail --profile=~/.checkgmail/prefs.xml
```

I get the settings window, but after I click OK, nothing happens.

---

