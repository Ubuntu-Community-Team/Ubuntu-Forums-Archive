---
title: "PHP 5.6 PPA Fails"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2015-07-02
All,
I'm running Uubntu 14.10 32bit, and I am unable to install PHP 5.6...

Here's what I want to do, but I get error messages after I try to install the PPA.

```
$ sudo apt-get install python-software-properties  (WORKS)
$ sudo add-apt-repository ppa:ondrej/php5-5.6 (FAILS)
$ sudo apt-get update (HAVEN'T EXECUTED THIS STEP YET)
$ sudo apt-get install -y php5 (HAVEN'T EXECUTED THIS STEP YET)
```

```
radsat@radsat-VirtualBox:~$ sudo add-apt-repository ppa:ondrej/php5-5.6
[sudo] password for radsat: 
Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 321, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 91, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:](https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:) [Errno -2] Name or service not known'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 119, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 839, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 382, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 346, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 333, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 292, in _get_suggested_ppa_message
    lp_user = get_info_from_lp(LAUNCHPAD_USER_API % user)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej:](https://launchpad.net/api/1.0/~ondrej:) [Errno -2] Name or service not known'
radsat@radsat-VirtualBox:~$ sudo add-apt-repository ppa:ondrej/php5-5.6
Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 321, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 91, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:](https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:) [Errno -2] Name or service not known'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 119, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 839, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 382, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 346, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 333, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 292, in _get_suggested_ppa_message
    lp_user = get_info_from_lp(LAUNCHPAD_USER_API % user)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej:](https://launchpad.net/api/1.0/~ondrej:) [Errno -2] Name or service not known'
radsat@radsat-VirtualBox:~$ clear
[3;J
radsat@radsat-VirtualBox:~$ sudo apt-get install python-software-properties
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-software-properties is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
radsat@radsat-VirtualBox:~$ clears
No command 'clears' found, did you mean:
 Command 'clear' from package 'ncurses-bin' (main)
clears: command not found
radsat@radsat-VirtualBox:~$ clear
[3;J












radsat@radsat-VirtualBox:~$ sudo add-apt-repository ppa:ondrej/php5-5.6
Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 321, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 91, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:](https://launchpad.net/api/1.0/~ondrej/+archive/ubuntu/php5-5.6:) [Errno -2] Name or service not known'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.4/urllib/request.py", line 1174, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.4/http/client.py", line 1090, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.4/http/client.py", line 1128, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.4/http/client.py", line 1086, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.4/http/client.py", line 924, in _send_output
    self.send(msg)
  File "/usr/lib/python3.4/http/client.py", line 859, in send
    self.connect()
  File "/usr/lib/python3.4/http/client.py", line 1221, in connect
    super().connect()
  File "/usr/lib/python3.4/http/client.py", line 836, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python3.4/socket.py", line 491, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
  File "/usr/lib/python3.4/socket.py", line 530, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -2] Name or service not known

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.4/urllib/request.py", line 153, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.4/urllib/request.py", line 455, in open
    response = self._open(req, data)
  File "/usr/lib/python3.4/urllib/request.py", line 473, in _open
    '_open', req)
  File "/usr/lib/python3.4/urllib/request.py", line 433, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.4/urllib/request.py", line 1217, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.4/urllib/request.py", line 1176, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [Errno -2] Name or service not known>

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 119, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 839, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 382, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 346, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 333, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 292, in _get_suggested_ppa_message
    lp_user = get_info_from_lp(LAUNCHPAD_USER_API % user)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 87, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 107, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~ondrej:](https://launchpad.net/api/1.0/~ondrej:) [Errno -2] Name or service not known'
radsat@radsat-VirtualBox:~$ 
```

Any help is greatly appreciated.

---

### Post by PaulW2U on 2015-07-02
Please use code tags. 

If you are using New Reply button - highlight text and use the # button in the text box header. 

The use of code tags also removes unwanted smileys.

---

### Post by webusr1 on 2015-07-03
Okay. Thank you.

---

