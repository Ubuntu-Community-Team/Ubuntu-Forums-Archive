---
title: "Installing flashplugin-installer package in ubuntu 14.04"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by dietwo on 2014-09-15
I am trying to install the above mentioned package but getting the following error output:

Processing triggers for update-notifier-common (0.154.1) ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.406.orig.tar.gz)
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 239, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 94, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 240, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 345, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 969, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 829, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 791, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 772, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 553, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
IOError: [Errno socket error] [Errno -2] Name or service not known
Setting up flashplugin-installer (11.2.202.406ubuntu0.14.04.1) ...

I can install all other package. Any hint please?

---

### Post by fantab on 2014-09-15
Flash is proprietory, and it is offered from 'third-party' repositories.
Have you enabled 'Partner' repository?
If not:
Software Center -> edit -> software sources
Put a check on 'Partner'... reload.

Then install flash-plugin-installer via software center.

---

### Post by dietwo on 2014-09-15
I enabled Canonical Partner and updated the package repository but still I am getting the above error.

I am working behind a proxy server. Could that pose any problem? Though, the proxy settings are working well for all the packages.

---

### Post by fantab on 2014-09-16
How did you tried earlier to install flashplugin? Did you try to install it directly from your linked .tar.gz download?
If installing directly from package file the package must be .deb and not .tar.gz, unless you know how to build such package.

Try this:
```
sudo dpkg --purge *packagename*
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```

---

### Post by Bucky Ball on 2014-09-16
> **dietwo said:**
> 

I am working behind a proxy server. Could that pose any problem? Though, the proxy settings are working well for all the packages.

May have worked for other packages as proxy might consider the Ubuntu repos a trusted site. Other third-parties may be untrusted and therefore banished.

* Just looking at your first post and your code ends with:

```
Setting up flashplugin-installer (11.2.202.406ubuntu0.14.04.1) ...
```

What comes after that? It appears to be setting it up. Do you end at a cursor? If not, what is the final error message before the cursor reappears?

---

### Post by dietwo on 2014-09-17
> **fantab said:**
> How did you tried earlier to install flashplugin? Did you try to install it directly from your linked .tar.gz download?
If installing directly from package file the package must be .deb and not .tar.gz, unless you know how to build such package.

Try this:
```
sudo dpkg --purge *packagename*
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```

No, I never tried to install it manually from .tar.gz. It was always using apt-get.

---

### Post by dietwo on 2014-09-17
> **Bucky Ball said:**
> May have worked for other packages as proxy might consider the Ubuntu repos a trusted site. Other third-parties may be untrusted and therefore banished.

* Just looking at your first post and your code ends with:

```
Setting up flashplugin-installer (11.2.202.406ubuntu0.14.04.1) ...
```

What comes after that? It appears to be setting it up. Do you end at a cursor? If not, what is the final error message before the cursor reappears?

This is the complete output which I have posted. 

Yes. I am given cursor at the end. According to apt-get, it understand that flashplugin-installer installed successfully but I believe that it (APT) doesn't track whether the actual flash plugin file was downloaded and installed or not.

---

