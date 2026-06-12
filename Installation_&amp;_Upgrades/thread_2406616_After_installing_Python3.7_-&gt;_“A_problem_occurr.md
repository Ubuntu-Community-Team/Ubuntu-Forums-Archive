---
title: "After installing Python3.7 -&gt; “A problem occurred when checking for the updates”"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by alvarade on 2018-11-23
Hello,

       I recently installed Python3.7, and after that a red icon (stop sign)  appears in my task bar with the message  "A problem occurred when  checking for the updates".
  As far as I could inform myself, some link for Python is missing, and  now everything is a mess among versions of Python in my computer.

When I do [HTML]python -V[/HTML] I receive python3.7 as output, and when I type [HTML]python3 -V[/HTML], I also receive python3.7.

  After typing[HTML] sudo update-alternatives --config python[/HTML] I obtain the following:
```

There are 3 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python2.7   2         auto mode
  1            /usr/bin/python2.7   2         manual mode
  2            /usr/bin/python3.5   1         manual mode
  3            /usr/bin/python3.6   2         manual mode
```

After typing [HTML]sudo update-alternatives --config python3[/HTML] I obtain the following:

```
There is only one alternative in link group python3 (providing /usr/bin/python3): /usr/bin/python3.6
Nothing to configure.
```

I just want by Python default, the version Python2.7, and by Python3  default, Python3.7. The others versions of Python, if I can remove them  and are not needed is better.
  How can I do that? Thanks.

**Edit**: I just wanted to add that all this started when I installed Python3.7 and Anaconda. Actually, when I write just ```
python
``` in the terminal, it opens the following:

[HTML]Python 3.7.0 (default, Jun 28 2018, 13:15:42) 
[GCC 7.2.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>[/HTML]

---

