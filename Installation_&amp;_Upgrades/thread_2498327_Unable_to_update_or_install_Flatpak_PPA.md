---
title: "Unable to update or install Flatpak PPA"
date: 2024-06-09
forum: Installation &amp; Upgrades
---

### Post by ianmoon on 2024-06-09
Been trying to add Flatpak Launchpad PPA as been documented, but it is not working for me on Ubuntu 22.04 LTS Pro, and it is not a network or internet connection issue. I receive this error when trying to add the PPA:

```
daniel@dkdt:~$ sudo add-apt-repository ppa:flatpak/stable
[sudo] password for daniel: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 364, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 347, in main
    shortcut = handler(source, **shortcut_params)
  File "/usr/lib/python3/dist-packages/softwareproperties/shortcuts.py", line 40, in shortcut_handler
    return handler(shortcut, **kwargs)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 82, in __init__
    if self.lpppa.publish_debug_symbols:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 494, in login_anonymously
    return cls(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 230, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 472, in __init__
    self._wadl = self._browser.get_wadl_application(self._root_uri)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 447, in get_wadl_application
    response, content = self._request(url, media_type=wadl_type)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 389, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 359, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1725, in request
    (response, content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 144, in _request
    response, content = super(LaunchpadOAuthAwareHttp, self)._request(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 184, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1441, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1363, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1153, in connect
    sock.connect((self.host, self.port))
TimeoutError: [Errno 110] Connection timed out
daniel@dkdt:~$ 
```

---

### Post by ne29914 on 2024-06-09
Here you go:
[https://phoenixnap.com/kb/add-apt-repository-command-not-found-ubuntu](https://phoenixnap.com/kb/add-apt-repository-command-not-found-ubuntu)

---

### Post by Xian on 2024-06-09
Advise to first verify connection to site:

$ ping launchpad.net
$ ping ppa.launchpadcontent.net


If no connection may try to disable IPv6.
[https://itsfoss.com/disable-ipv6-ubuntu-linux/](https://itsfoss.com/disable-ipv6-ubuntu-linux/)

---

### Post by Tadaen_Sylvermane on 2024-06-09
Is there a reason flatpak package in the repo isn't working? PPA's can cause problems occasionally. Best to keep their use to a minimum.

---

### Post by ianmoon on 2024-06-10
Thanks for the help. This is the terminal output:

```
daniel@dkdt:~$ sudo apt-get install software-properties-common
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
software-properties-common is already the newest version (0.99.22.9).
software-properties-common set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
daniel@dkdt:~$ sudo add-apt-repository "https://ppa.launchpadcontent.net/flatpak/stable/ubuntu/"
Repository: 'deb https://ppa.launchpadcontent.net/flatpak/stable/ubuntu/ jammy main'
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 364, in <module>
    sys.exit(0 if addaptrepo.main() else 1)
  File "/usr/bin/add-apt-repository", line 352, in main
    self.prompt_user_shortcut(shortcut)
  File "/usr/bin/add-apt-repository", line 140, in prompt_user_shortcut
    if shortcut.description:
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 132, in description
    return self.lpppa.description
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in lpppa
    self._lpppa = self.lpteam.getPPAByName(name=self.ppaname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in lpteam
    self._lpteam = self.lp.people(self.teamname)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in lp
    self._lp = login_func("%s.%s" % (self.__module__, self.__class__.__name__),
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 494, in login_anonymously
    return cls(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 230, in __init__
    super(Launchpad, self).__init__(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/resource.py", line 472, in __init__
    self._wadl = self._browser.get_wadl_application(self._root_uri)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 447, in get_wadl_application
    response, content = self._request(url, media_type=wadl_type)
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 389, in _request
    response, content = self._request_and_retry(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 359, in _request_and_retry
    response, content = self._connection.request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1725, in request
    (response, content) = self._request(
  File "/usr/lib/python3/dist-packages/launchpadlib/launchpad.py", line 144, in _request
    response, content = super(LaunchpadOAuthAwareHttp, self)._request(
  File "/usr/lib/python3/dist-packages/lazr/restfulclient/_browser.py", line 184, in _request
    return super(RestfulHttp, self)._request(
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1441, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1363, in _conn_request
    conn.connect()
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1153, in connect
    sock.connect((self.host, self.port))
TimeoutError: [Errno 110] Connection timed out
daniel@dkdt:~$ 
```

Also generated this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293849&stc=1[/IMG]

---

### Post by ianmoon on 2024-06-10
Thanks for the help. Here is the terminal output:

```
daniel@dkdt:~$ ping launchpad.net
PING launchpad.net(launchpad-net.ps5-frontend-0.canonical.com (2620:2d:4000:1009::f3)) 56 data bytes
^C
--- launchpad.net ping statistics ---
274 packets transmitted, 0 received, 100% packet loss, time 279550ms

daniel@dkdt:~$ ping ppa.launchpadcontent.net
PING ppa.launchpadcontent.net(ppa.launchpadcontent.net (2620:2d:4000:1::81)) 56 data bytes
^C
--- ppa.launchpadcontent.net ping statistics ---
119 packets transmitted, 0 received, 100% packet loss, time 120839ms

daniel@dkdt:~$ 
```

I can however connect to the PPA via web browser:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293850&stc=1[/IMG]

I am going to try disabling IPv6 as suggested by Xian

---

### Post by ianmoon on 2024-06-10
@[**[COLOR=#000000]Xian[/COLOR]**]("https://ubuntuforums.org/member.php?u=37") , Thank you so very much!! You Rock!!

1. Disabled Ipv6:

```
daniel@dkdt:~$ sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
[sudo] password for daniel: 
net.ipv6.conf.all.disable_ipv6 = 1
daniel@dkdt:~$ sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6 = 1
daniel@dkdt:~$ sudo sysctl -w net.ipv6.conf.lo.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6 = 1
```

2. Added Flatpak PPA:

```

daniel@dkdt:~$ sudo add-apt-repository ppa:flatpak/stable
[sudo] password for daniel: 
Repository: 'deb https://ppa.launchpadcontent.net/flatpak/stable/ubuntu/ jammy main'
Description:
Latest stable versions of Flatpak.

Support policy
--------------

This PPA is provided as a convenience for Ubuntu users, with no guarantee of support. If you are an Ubuntu developer and would like to volunteer to maintain packages for this PPA, please contact us via <https://github.com/flatpak/ppa-flatpak/issues>.

Packages in this PPA are built for LTS branches of Ubuntu, currently
22.04 'jammy' and 20.04 'focal'. The newest LTS branch is treated as the highest priority for updates.

Packages for Ubuntu 18.04 or older are no longer updated. Branches that have reached EOL for non-subscription-based updates are likely to stop receiving updates, or be removed from this PPA, when backports to those branches become too difficult.

Non-LTS branches such as groovy and hirsute are not currently supported by this PPA. If you are an Ubuntu developer and would like to volunteer to maintain packages for this PPA, please contact us via <https://github.com/flatpak/ppa-flatpak/issues>.

Source code for the packages used here
--------------------------------------

* https://github.com/flatpak/ppa-flatpak
* https://github.com/flatpak/ppa-flatpak-builder
* https://github.com/flatpak/ppa-xdg-desktop-portal
* https://github.com/flatpak/ppa-xdg-desktop-portal-gtk

These packages are built from the ppa/stable/jammy, ppa/stable/focal branches.

Development versions of these packages
--------------------------------------

https://launchpad.net/~flatpak/+archive/ubuntu/development provides newer prereleases of Flatpak from its development branch.
More info: https://launchpad.net/~flatpak/+archive/ubuntu/stable
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/flatpak-ubuntu-stable-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/flatpak-ubuntu-stable-jammy.list
Adding key to /etc/apt/trusted.gpg.d/flatpak-ubuntu-stable.gpg with fingerprint 5C6D153A17C02C337EF6C663B8B9D41229DFA5F5
Hit:1 http://za.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://za.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                     
Hit:3 http://za.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                   
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                      
Get:5 https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy InRelease [18.1 kB]                                        
Hit:6 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease
Hit:7 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease
Get:8 https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy/main i386 Packages [1,320 B]
Get:9 https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy/main amd64 Packages [4,704 B]
Hit:10 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Get:11 https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy/main Translation-en [2,792 B]
Hit:12 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Fetched 26.9 kB in 2s (12.4 kB/s)
Reading package lists... Done
daniel@dkdt:~$ sudo apt update
Hit:1 http://za.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://za.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                     
Hit:3 http://za.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                   
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                      
Hit:5 https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy InRelease                                                  
Hit:6 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease
Hit:7 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease
Hit:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:9 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
daniel@dkdt:~$ 
```

3. Checked Flatpak version after updating:

```
daniel@dkdt:~$ flatpak --version
Flatpak 1.14.6
daniel@dkdt:~$ 
```

---

