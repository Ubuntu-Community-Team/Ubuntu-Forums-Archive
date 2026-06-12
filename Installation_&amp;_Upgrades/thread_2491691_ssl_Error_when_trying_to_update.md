---
title: "ssl Error when trying to update"
date: 2023-10-17
forum: Installation &amp; Upgrades
---

### Post by arthurhetem on 2023-10-17
I'm trying to update to 23.04, i've already installed all available updates and when i run 
sudo do-release-upgrade -m desktop
i get a bunch of errors about ssl and python3.11:

```
Checking for a new Ubuntu release
Exception in thread Thread-1 (download):
Traceback (most recent call last):
  File "/usr/lib/python3.11/threading.py", line 1038, in _bootstrap_inner
    self.run()
  File "/usr/lib/python3.11/threading.py", line 975, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 364, in download
    uri = urlopen(req, timeout=20)
          ^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 216, in urlopen
    return opener.open(url, data, timeout)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 519, in open
    response = self._open(req, data)
               ^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 536, in _open
    result = self._call_chain(self.handle_open, protocol, protocol +
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 496, in _call_chain
    result = func(*args)
             ^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 1391, in https_open
    return self.do_open(http.client.HTTPSConnection, req,
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/urllib/request.py", line 1317, in do_open
    h = http_class(host, timeout=req.timeout, **http_conn_args)
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/http/client.py", line 1425, in __init__
    context = ssl._create_default_https_context()
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/ssl.py", line 761, in create_default_context
    context = SSLContext(PROTOCOL_TLS_CLIENT)
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.11/ssl.py", line 500, in __new__
    self = _SSLContext.__new__(cls, protocol)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
ssl.SSLError: unknown error (_ssl.c:3093)

```

---

### Post by deadflowr on 2023-10-17
To 23.04 from what?

---

### Post by MAFoElffen on 2023-10-17
And what is the current Edition of that release? <-- I noticed that you, for some reason used the -m ,or --mode= option, which I don't think anyone has used in years, that I have seen... So I am very curious about what the original source OS is, and why you are trying to transform it.

Let's say for example you had started as Ubuntu Desktop 22.04 LTS... And the apt.conf file said prompt=normal, then you would just do:
```

sudo do-release-upgrade

```
The other pending implied question would be, If you are on 22.04 LTS (Long Term Support)... Why are you wanting to upgrade the release to 23.04 (a development release) which only has 3 months of support left? 24.04 LTS rolls out in 6 months... We start Dev testing for it in about 1-2 weeks.

---

### Post by arthurhetem on 2023-10-17
Sorry about that, i'm on 23.04 trying to update to 23.10, i've tried without -m, the error is the same.

---

### Post by MAFoElffen on 2023-10-17
Please post the output from the following between Code Tags
```

apt list update-manager-core --installed

```

---

### Post by arthurhetem on 2023-10-18
There is:
```

Listing... Done
update-manager-core/lunar,lunar,now 1:23.04.2 all [installed,automatic]

```

---

### Post by MAFoElffen on 2023-10-18
Dang. That is the latest version.

The only thing I can think of trying before that is to reinstall that package and see if you have the same errors
```

sudo apt install --reinstall update-manager-core
sudo update
sudo do-release-upgrade

```
If it does have the same error on a release upgrade, then please do
```

ubuntu-bug update-manager-core

```
And submit a bug against it. Include the errors you posted. Something is wrong with that on your combination of what is existing in your install. You semed have done everything right and am doing the correct things. There is something there that is crashing.

---

### Post by arthurhetem on 2023-10-18
I've tried, same error happened again, submit the bug report with all info.
Thanks for the help.

---

