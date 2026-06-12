---
title: "Command &quot;add-apt-repository&quot; hangs and then outputs errors in newly installed Jammy"
date: 2022-05-02
forum: Installation &amp; Upgrades
---

### Post by liam.gutierrez on 2022-05-02
Hi friends,

Today, I encountered an error with the command [B]add-apt-repository
[/B]
When I issue this command, it hangs a while and then outputs this error:

```
sudo add-apt-repository ppa:gerardpuig/ppa
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
```

I tried this **sudo apt install --reinstall software-properties-common **but that didn't fix it. I also checked for missing python3 packages but couldn't find any.

Thanks for helping.

```
./+o+-       liam@komputilo
                  yyyyy- -yyyyyy+      OS: Ubuntu 22.04 jammy
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 5.15.0-27-generic
           .++ .:/++++++/-.+sss/`      Uptime: 3h 28m
         .:++o:  /++++++++/:--:/-      Packages: 2480
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 5.1.16
       .:+o:+o/.          `+sssoo+/    Resolution: 3720x1080
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 41.4
 /+++//+:`oo+o               /::--:.   WM: Mutter
 \+/+o+++`o++o               ++////.   WM Theme: 
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Yaru-viridian-dark [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Yaru-viridian
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      Disk: 113G / 797G (15%)
           .o:`.syhhhhhhh/.oo++o`      CPU: Intel Celeron J4115 @ 4x 2.5GHz [53.0°C]
               /osyyyyyyo++ooo+++/     GPU: UHD Graphics 600
                   ````` +oo+++o\:     RAM: 5963MiB / 7768MiB
                          `oo++.
```

---

### Post by tea for one on 2022-05-02
> **liam.gutierrez said:**
> ```
   OS: Ubuntu 22.04 jammy DE: GNOME 41.4
```

Gnome 42 is the current version for Ubuntu 22.04 and you have Gnome 41.4.
Have you run [COLOR="#0000FF"]sudo apt update[/COLOR] and [COLOR="#0000FF"]sudo apt upgrade[/COLOR] recently?

---

### Post by Vidyutk on 2022-05-02
I have the same problem. Everything is updated. Gnome is 42. No broken packages. Recent upgrade to Ubuntu 22.04 is the only thing changed.

---

### Post by liam.gutierrez on 2022-05-03
It's a clean install. In the settings app, it shows Gnome version 42. I guess screenfetch notices that Ubuntu didn't switch all gnome apps to version 42 like the calculator app still on 41.1. No idea how screenfetch detects gnome version. And I did apt update and upgrade commands many times over. I still can't add any new repositories :(

[IMG]https://i.ibb.co/fF0Jm7n/Screenshot-from-2022-05-03-02-54-28.png[/IMG]

---

### Post by tea for one on 2022-05-03
You could investigate further by booting into a [COLOR="#0000FF"]live[/COLOR] session of 22.04 and see if the ppa repository loads.

If the warning [COLOR="#FF0000"]TimeoutError: [Errno 110] Connection timed out[/COLOR] appears, then that may be worth further research.

I cannot reproduce your error, as I have successfully added the gerardpuig/ppa to both Ubuntu 22.04 and Xubuntu 22.04.

---

### Post by ActionParsnip on 2022-05-03
Could add it manually
```

echo "deb https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ubuntu-cleaner.list > /dev/null
echo "deb-src https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy main"  | sudo tee -a /etc/apt/sources.list.d/ubuntu-cleaner.list > /dev/null
sudo apt update 2>&1 1>/dev/null | sed -ne 's/.*NO_PUBKEY //p' | while read key; do if ! [[ ${keys
[*]} =~ "$key" ]]; then sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net:80 --recv-keys "$key"; keys+=("$key"); fi; done
sudo apt update

```

---

### Post by liam.gutierrez on 2022-05-03
The command "add-apt-repository" is working again. 

I didn't do anything to the system except installing **python-is-python3**. Not sure if that solved it  &#128533;

```
sudo add-apt-repository ppa:gerardpuig/ppa
Repository: 'deb https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/ jammy main'
Description:
Official Ubuntu Cleaner stable repository
More info: https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa
Adding repository.

```

---

### Post by liam.gutierrez on 2022-05-24
The issue reappeared: add-apt-repository not working again :(

---

### Post by liam.gutierrez on 2022-05-24
Here's the output I get of command **sudo add-apt-repository ppa:gerardpuig/ppa**:

```
$ sudo add-apt-repository ppa:gerardpuig/ppa
[sudo] password for liam: 
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
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1693, in request
    (response, new_content) = self._request(
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
```

---

### Post by #&amp;thj^% on 2022-05-24
I can't reproduce your findings:
```
sudo add-apt-repository ppa:gerardpuig/ppa
[sudo] password for me: 
Repository: 'deb https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/ jammy main'
Description:
Official Ubuntu Cleaner stable repository
More info: https://launchpad.net/~gerardpuig/+archive/ubuntu/ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-jammy.list
Adding key to /etc/apt/trusted.gpg.d/gerardpuig-ubuntu-ppa.gpg with fingerprint E2CBBCC339FED83BCAE8E4B55F841B74A892A73C
Hit:1 http://dl.google.com/linux/earth/deb stable InRelease
Hit:2 https://linux.teamviewer.com/deb stable InRelease
Get:3 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                      
Get:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease [109 kB]     
Get:6 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy InRelease [18.1 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]  
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [210 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [98.8 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [53.1 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [57.4 kB]
Get:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [3,488 B]
Get:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [98.8 kB]
Ign:14 https://mkvtoolnix.download/ubuntu jammy InRelease                      
Get:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [37.2 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [32.3 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [87.8 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 48x48 Icons [33.6 kB]
Get:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 64x64 Icons [44.5 kB]
Get:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [1,628 B]
Get:21 http://ca.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [1,196 B]
Hit:22 https://mkvtoolnix.download/ubuntu jammy Release                        
Hit:23 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease
Get:25 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [123 kB]
Get:26 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [40.3 kB]
Get:27 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [31.4 kB]
Get:28 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [11.4 kB]
Get:29 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [1,744 B]
Get:30 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [121 kB]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [18.2 kB]
Get:32 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy/main i386 Packages [500 B]
Get:33 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy/main amd64 Packages [500 B]
Get:34 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy/main Translation-en [188 B]
Fetched 1,445 kB in 3s (454 kB/s)        
Reading package lists... Done
```
```
me@me-Standard-PC-Q35-ICH9-2009:~$ sudo apt update
Hit:1 http://dl.google.com/linux/earth/deb stable InRelease
Hit:2 https://linux.teamviewer.com/deb stable InRelease                        
Hit:3 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:5 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:6 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:7 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy InRelease   
Ign:8 https://mkvtoolnix.download/ubuntu jammy InRelease                       
Hit:9 https://mkvtoolnix.download/ubuntu jammy Release                         
Hit:10 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```
```
sudo apt install ubuntu-cleaner
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  python3-bs4 python3-html5lib python3-lxml python3-soupsieve
  python3-webencodings
Suggested packages:
  python3-genshi python-lxml-doc
The following NEW packages will be installed:
  python3-bs4 python3-html5lib python3-lxml python3-soupsieve
  python3-webencodings ubuntu-cleaner
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,424 kB of archives.
After this operation, 5,555 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
```
install:
```
apt policy ubuntu-cleaner
ubuntu-cleaner:
  Installed: 1.1.4-1
  Candidate: 1.1.4-1
  Version table:
 *** 1.1.4-1 500
        500 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status

```
EDIT: and this:
```
 apt policy python3
python3:
  Installed: 3.10.4-0ubuntu2
  Candidate: 3.10.4-0ubuntu2
  Version table:
 *** 3.10.4-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by liam.gutierrez on 2022-06-02
Update: the command "add-apt-repository" worked again **for just one instance**. Now it's **not** working. I simply can't understand why. I didn't do any fancy stuff like editing config files related to apt.


Below is the output with lots of error messages:

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
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
  File "/usr/lib/python3/dist-packages/httplib2/__init__.py", line 1693, in request
    (response, new_content) = self._request(
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

```


Any help greatly appreciated!

---

### Post by MAFoElffen on 2022-06-02
I actually think there is a network connection problem at launchpad going on right now...

Try these:
```

ping launchpad.net
sudo install traceroute
traceroute -m 50 launchpad.net

```
I have a great ISP connection. And at the moment, me pinging launchpad.net hangs. If I set the TTL hops of traceroute to 200, every hop after hop #16 (64.125.31.25) is timed out or not configured...

Just saying. The "Connection timed out" error gave me a hint that something else was going on.

---

### Post by liam.gutierrez on 2022-06-03
Oh no, maybe I have something blocking the connection to launchpad. Thanks for hinting me to the right direction:

```
$ ping launchpad.net
PING launchpad.net(2620:2d:4000:1001::8003) 56 data bytes
^C
--- launchpad.net ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```

---

### Post by liam.gutierrez on 2022-06-03
** traceroute -m 50 launchpad.net:**


```
$ traceroute -m 50 launchpad.net
traceroute to launchpad.net (185.125.189.222), 50 hops max, 60 byte packets
 1  _gateway (192.168.1.1)  0.697 ms  0.674 ms  0.849 ms
 2  10.146.241.66 (10.146.241.66)  38.554 ms  38.732 ms  38.720 ms
 3  68.85.97.181 (68.85.97.181)  17.402 ms 68.85.96.49 (68.85.96.49)  16.574 ms po152-rur02.wolferd.fl.naples.comcast.net (68.85.97.181)  17.543 ms
 4  68.85.59.234 (68.85.59.234)  17.531 ms 68.85.64.221 (68.85.64.221)  16.729 ms  24.653 ms
 5  68.85.59.217 (68.85.59.217)  28.489 ms  28.674 ms 68.85.64.221 (68.85.64.221)  24.819 ms
 6  96.110.45.93 (96.110.45.93)  31.312 ms 96.110.45.89 (96.110.45.89)  23.666 ms 68.85.59.217 (68.85.59.217)  23.865 ms
 7  be-33913-cs01.miami.fl.ibone.comcast.net (96.110.45.81)  23.777 ms be-3101-pe01.nota.fl.ibone.comcast.net (96.110.36.82)  22.975 ms be-3401-pe01.nota.fl.ibone.comcast.net (96.110.36.94)  22.961 ms
 8  be-3301-pe01.nota.fl.ibone.comcast.net (96.110.36.90)  23.112 ms be-3201-pe01.nota.fl.ibone.comcast.net (96.110.36.86)  22.936 ms be-3401-pe01.nota.fl.ibone.comcast.net (96.110.36.94)  22.673 ms
 9  * 72.52.92.50 (72.52.92.50)  34.636 ms 184.105.64.94 (184.105.64.94)  30.727 ms
10  184.105.64.94 (184.105.64.94)  29.751 ms * 72.52.92.50 (72.52.92.50)  27.002 ms
11  216.66.49.97 (216.66.49.97)  32.886 ms *  33.617 ms
12  100ge1-1.core1.nyc4.he.net (184.105.223.166)  51.990 ms * 184.105.80.161 (184.105.80.161)  55.330 ms
13  100ge1-1.core1.nyc4.he.net (184.105.223.166)  60.791 ms * port-channel1.core1.lon6.he.net (184.104.198.170)  128.859 ms
14  * * port-channel1.core1.lon6.he.net (184.104.198.170)  128.822 ms
15  swp9.il3-core1.canonical.com (216.66.93.14)  131.587 ms port-channel1.core1.lon6.he.net (184.104.198.170)  121.991 ms  122.091 ms
16  swp9.il3-core1.canonical.com (216.66.93.14)  121.896 ms swp9.il3-core2.canonical.com (216.66.89.222)  122.511 ms 185.125.190.12 (185.125.190.12)  123.406 ms
17  * 185.125.190.12 (185.125.190.12)  130.339 ms *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
31  * * *
32  * * *
33  * * *
34  * * *
35  * * *
36  * * *
37  * * *
38  * * *
39  * * *
40  * * *
41  * * *
42  * * *
43  * * *
44  * * *
45  * * *
46  * * *
47  * * *
48  * * *
49  * * *
50  * * *



```

---

### Post by MAFoElffen on 2022-06-03
See, like mine... It is getting to canonical.com and then timing out within their own network infrastructure. This usually resolves itself, once someone there is aware of that they have a problem...

---

### Post by liam.gutierrez on 2022-06-03
Thanks

---

### Post by sturn42 on 2022-06-26
I want to add one other solution that I found. My issue was that I could add the repository I needed to my main desktop and laptop, but not a 2nd desktop I use for giggles. The 2nd desktop is connected to a router acting as a wirelss bridge. IPv6 address resolution is not available in this configuration, but I rarely have to disable IPv6 as there's usually a fallback to IPv4. It took the advice on this thread to ping launchpad.net when I realized it was probably trying got resovle an IPv6 address only and not falling back to IPv4. I disabled IPv6 on that computer and was able to add the key without it timing out.

---

### Post by ipkpjersi on 2022-07-02
Funnily enough, I also had this issue. I had to disable IPv6 for my connection (currently using WiFi) in order for add-apt-repository command to work properly. The weird thing is I wasn't able to get a ping response from launchpad.net via IPv4 or IPv6, but disabling IPv6 at least fixed adding repositories.

---

### Post by dyopiac on 2022-08-30
I had this issue and disabling IPv6 resolved it, thanks very much!

---

### Post by e-jani on 2022-10-14
Same, launchpad resolves with IPv6 but seems to only serve PPA with IPv4 :(

---

### Post by csae2608 on 2023-04-25
also various ppa do not function with different python error when added (only seen after interrupting with ctrl+c)

this in fresh install of ubuntu 20.04 LTS

like in> sudo add-apt-repository ppa:team-xbmc/ppa

sudo add-apt-repository ppa:team-xbmc/ppa
^CTraceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 137, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 885, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 469, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 426, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 380, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 110, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 104, in get_info_from_lp
    return get_info_from_https(lp_url, True)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 96, in get_info_from_https
    data = func(lp_url=url, accept_json=accept_json, retry_delays=retry_delays)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 138, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request,
  File "/usr/lib/python3.8/urllib/request.py", line 222, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.8/urllib/request.py", line 525, in open
    response = self._open(req, data)
  File "/usr/lib/python3.8/urllib/request.py", line 542, in _open
    result = self._call_chain(self.handle_open, protocol, protocol +
  File "/usr/lib/python3.8/urllib/request.py", line 502, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.8/urllib/request.py", line 1397, in https_open
    return self.do_open(http.client.HTTPSConnection, req,
  File "/usr/lib/python3.8/urllib/request.py", line 1354, in do_open
    h.request(req.get_method(), req.selector, req.data, headers,
  File "/usr/lib/python3.8/http/client.py", line 1256, in request
    self._send_request(method, url, body, headers, encode_chunked)
  File "/usr/lib/python3.8/http/client.py", line 1302, in _send_request
    self.endheaders(body, encode_chunked=encode_chunked)
  File "/usr/lib/python3.8/http/client.py", line 1251, in endheaders
    self._send_output(message_body, encode_chunked=encode_chunked)
  File "/usr/lib/python3.8/http/client.py", line 1011, in _send_output
    self.send(msg)
  File "/usr/lib/python3.8/http/client.py", line 951, in send
    self.connect()
  File "/usr/lib/python3.8/http/client.py", line 1418, in connect
    super().connect()
  File "/usr/lib/python3.8/http/client.py", line 922, in connect
    self.sock = self._create_connection(
  File "/usr/lib/python3.8/socket.py", line 796, in create_connection
    sock.connect(sa)
KeyboardInterrupt




EDIT:

it seems that the "add-apt-repository" still function,

but it takes very long times to elaborate it, somthing feels not right.

in my case it would look like

```
sudo add-apt-repository ppa:team-xbmc/ppa
 Official Team Kodi stable releases
 More info: https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Error: retrieving gpg key timed out.

```

but afterwards it be able to install updated Kodi package from PPA repo.

---

### Post by feridi on 2023-11-05
For me, the issue lies with the computer attempting to use IPv6 for connection without proper configuration. Disabling IPv6 by running the following steps and then trying again worked for me.

> sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.lo.disable_ipv6=1

---

### Post by abteenz on 2024-08-23
Fixing the DATE and TIME on my machine fixed this annoying issue.

[FONT=var(--theme-post-body-font-family]sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"


[/FONT]
[FONT=inherit][FONT=inherit][COLOR=#0C0D0E][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]
[/FONT]
[/FONT]

---

### Post by coffeecat on 2024-08-23
Back to sleep, ancient thread.

Closed.

---

