---
title: "checkgmail error"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by christooss on 2006-10-22
I have instlled checkgmail with sudo apt-get install checkgmail and when running in terminal I get this error


```
Updating translations file ...
Wide character in print at /usr/bin/checkgmail line 3485.
 ... done!
Can't use an undefined value as a HASH reference at /usr/bin/checkgmail line 3500.
A thread exited while 2 threads were running.
```

---

### Post by skymt on 2006-10-22
That appears to be a bug in the localization support. Try this (just to help debug):```
export LANG=EN_US
checkgmail
```

---

### Post by christooss on 2006-10-23
Nope this doesn't fix the problem :(

---

### Post by owenjm on 2006-10-29
Hi,

I'm the developer of CheckGmail, and I don't generally visit these forums.  So this is not directed at you specifically, but to anyone having a problem with CheckGmail:

**If you want support, please use the CheckGmail website!!**

[http://checkgmail.sf.net]("http://checkgmail.sf.net")

There are links there to enable you to email me directly, or use the forums there (which I read) or to lodge bug reports.  That way I'll hear about the problem, which means that (a) you have a much better chance of getting the problem solved, and (b) if it's caused by a bug which I haven't discovered, then I can fix it!  It's really shocked me that whenever a problem with my software is mentioned on these forums, not once has any reply suggested contacting the developer, regardless of what the issue was!!

As regards your particular problem - I haven't seen this before.  But as a first step I'd recommend deleting the file ~/.checkgmail/lang.xml ...  If that doesn't fix the problem, then please submit a bug report on the checkgmail sf.net pages and I can take it from there.  Chances are, if you're seeing this problem, others are too - and I'd like this software to be as bug-free as possible.

---

### Post by Kobalt on 2007-06-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/90984](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/90984) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It is a known bug, happening when you select a language that uses special characters. They won't be displayed properly and you won't be able to launch checkgmail again. 
The only solution I found was to delete the .checkgmail folder in my /home and then relaunch it, this time leaving the locale to English.

---

