---
title: "Update-manager problem"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by educamero on 2010-07-27
When I run the update-manager from terminal the following process is displayed: 

```

update-manager -d
Unhandled exception in thread started by <bound method MetaRelease.download of <MetaRelease object at 0x9881a04 (UpdateManager+MetaReleaseGObject+MetaRelease at 0x9e189c0)>>
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 229, in download
    uri=urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 381, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 399, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1107, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1064, in do_open
    h = http_class(host) # will parse host:port
  File "/usr/lib/python2.5/httplib.py", line 639, in __init__
    self._set_hostport(host, port)
  File "/usr/lib/python2.5/httplib.py", line 651, in _set_hostport
    raise InvalidURL("nonnumeric port: '%s'" % host[i+1:])
httplib.InvalidURL: nonnumeric port: ''

```

and basically the new distributions available to updating are not shown. I've been looking up for this in the forum but not response. 

Any idea to solve it is very welcome.

Detail which might be important is that I have to use a proxy server within the university I work in to have contact with the world. 


Thanks.

---

### Post by tommcd on 2010-07-27
Are you still running Ubuntu 8.10 as it says in your profile?
If you are, you should be aware that 8.10 reached end of life on April 30, 2010:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
And the version that you would have the option to upgrade to, which is 9.04, will reach EOL in just 3 months. As far as I know though, the 9.04 repos should still be available to you, since 9.04 has not reached EOL yet.
See these links for upgrading 8.10 to 9.04:
[http://www.ubuntugeek.com/how-to-upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty.html)
[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server)
If you are running a newer version of Ubuntu than 8.10, then please update your profile, or say what version you are running in your post. This will avoid any confusion, so others can more effectively help you with problems like this.

Anyway, if this is your situation (8.10 ==> 9.04), you would be well advised to just do a clean install of Ubuntu 10.04, which is the current version.
Ubuntu 10.04 is a LTS version. So it will be supported for at least 3 years for the desktop version.

---

### Post by educamero on 2010-07-30
Thank you. Well, yep, I was a little bit obsolete. Basically I did a new clean installation (Karmic Koala), and then I did the upgrade to 10.04. Cheers.

---

