---
title: "terminal won't launch after upgrade to 15.04 vivid vervet"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by rclocher3 on 2015-04-24
Hi all,

I just upgraded my computer to Ubuntu 15.04 "Vivid Vervet", and now I can't launch a terminal.  Shift+Ctrl+T doesn't seem to do anything; nor does typing "terminal" into the dash.  xterm works though.  "ps aux | grep gnome-terminal" shows some defunct instances of gnome-terminal.

rob@esprimo:~$ ps aux | grep gnome-terminal
rob       2757  0.0  0.1 286744 17916 ?        Sl   14:50   0:00 /usr/bin/python3 /usr/bin/gnome-terminal
rob       2762  0.0  0.0      0     0 ?        Z    14:50   0:00 [gnome-terminal-] <defunct>
rob       2869  0.0  0.1 286736 17960 ?        Sl   14:54   0:00 /usr/bin/python3 /usr/bin/gnome-terminal
rob       2873  0.0  0.0      0     0 ?        Z    14:54   0:00 [gnome-terminal-] <defunct>
rob       3381  0.0  0.0   9464  1748 pts/5    S+   15:11   0:00 grep --color=auto gnome-terminal

Can anybody help?

- Rob

---

### Post by jonoinsa on 2015-04-24
Same for me, knew I should have held off to upgrade :( . Luckily there's heaps of other options......

---

### Post by rclocher3 on 2015-04-24
I don't know if this qualifies as a clue or not, but Backup isn't working either.

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1500, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1494, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1327, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 1047, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 221, in get_backend
    obj = get_backend_object(url_string)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 207, in get_backend_object
    return factory(pu)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/_boto_single.py", line 161, in __init__
    self.resetConnection()
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/_boto_single.py", line 183, in resetConnection
    self.conn = get_connection(self.scheme, self.parsed_url, self.storage_uri)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/_boto_single.py", line 97, in get_connection
    assert scheme == 's3'
AssertionError

---

### Post by rclocher3 on 2015-04-25
Apparently the problem has to do with my custom locale.  I changed back to the en_US.UTF-8, and now I can launch a terminal.  I'm also stuck with AM/PM time, MM/DD/YYYY dates, and inches, grrrr...  If users can't define custom locales, then we might as well admit that the locale system is well and truly broken.  Oh well, I'll report the bug.

---

### Post by rclocher3 on 2015-04-25
The bug has been reported, have a look at it here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1448563](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1448563)

---

