---
title: "problems in installing grub in Ubuntu"
date: 2023-04-26
forum: Installation &amp; Upgrades
---

### Post by artist1986 on 2023-04-26
I just have ubuntu 20.10 on my laptop. It's boot has problem and the grub must repair. But I did different ways but there are several errors. I use a usb live ubuntu 20.10. After boot lap top on that, at first I did the way on boot-repair page of [help.ubuntu.com ]("https://help.ubuntu.com/community/Boot-Repair"). But with first command I have traceback errors:


```
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 331, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 314, in main
    shortcut = handler(source, **shortcut_params)
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 40, in shortcut_handler
    return handler(shortcut, **kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 67, in __init__
    if self.lpppa.publish_debug_symbols:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 94, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 85, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 400, in login_anonymously
    return cls(credentials, None, None, service_root=service_root,
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 209, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 485, in __init__
    self._wadl = self._browser.get_wadl_application(self._root_uri)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 456, in get_wadl_application
    response, content = self._request(url, media_type=wadl_type)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 398, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 368, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1943, in request
    (response, new_content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 137, in _request
    response, content = super(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 193, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1650, in _request
    (response, content) = self._conn_request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1557, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1391, in connect
    raise socket_err
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1324, in connect
    sock.connect((self.host, self.port))
OSError: [Errno 101] Network is unreachable
```

I searched and found I have to find partitions consist of ubuntu and EFI, mount them and install again. So I did that but I got the error again:

grub-install: error: cannot find EFI directory.

I try to make it and mount again like the solution [here]("https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows") . I tried other way but they didn't work. 
How should I repair grub and fix it? Also, I have to repair grub and after that install a new version of Ubuntu? because as a solution I tried to do this but I got input/output error.

---

### Post by grahammechanical on 2023-04-26
Why are you using a version of Ubuntu that reached end of life October 2020? If you can boot 20.10 then backup your data. You can also do this by using the Ubuntu ISO image Try Ubuntu session. To get to a version of Ubuntu that is still supported you would need to do an online update from 20.10 to 21.04. Then to 21.10 and then finally to 22.04. It would be much easier to download and install 22.04 afresh.

I have no knowledge of trace back errors. I do know that versions of Ubuntu that have reached end of life have their software repositories closed and re-located elsewhere. So, the addresses in source.list are now inaccurate. The only way to update and then do an online upgrade to a version of Ubuntu that has reached end of life is to edit the sources.list file and change the repository addresses to the old-releases.ubuntu.com address.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by yancek on 2023-04-27
Support for 20.10 ended in the summer of 2021 and the repositories are no longer available.  This is explained in post 2 above. You should run boot repair with the Create BootInfo Summary option and post the link you get when it finishes here as that will contain details of your system needed for members here to help.  That is the general suggested method with boot problems but it is pretty pointless with an unsupported release like 20.10.

---

