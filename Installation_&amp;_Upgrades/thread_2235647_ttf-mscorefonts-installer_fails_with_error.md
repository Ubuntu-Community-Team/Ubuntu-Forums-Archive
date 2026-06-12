---
title: "ttf-mscorefonts-installer fails with error"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by mdarr on 2014-07-22
I am trying to install the MS core fonts on Ubuntu 14.04 64bit.
sudo apt-get purge ttf-mscorefonts-installer ------- to make sure old installs don't interfere
sudo apt-get install ttf-mscorefonts-installer 
Everything goes smoothly until I get to the 
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
where the install dies with an error
 File "/usr/lib/update-notifier/package-data-downloader", line 239, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
........
IOError: [Errno socket error] [Errno -2] Name or service not known
Of course the trace has a lot in .....

Anyone else getting this error and know what to do about it?

---

### Post by slickymaster on 2014-07-22
Hi mdarr, welcome to the forums?

Does **/var/log/apt/term.log** offer any more explanation for why the download has failed? Is there an apt proxy setting on your system pointed to a proxy that doesn't allow arbitrary file downloads?

---

### Post by kc1di on 2014-07-22
if you down load the file you've listed in the link georgi32.exe it will install manually without problems. 
At least it did on my xubuntu install here.

---

### Post by mdarr on 2014-07-23
How can I download individual files? What I need are the arial and New Times Roman fonts. If there is a way to bypass then I will use that.

Not really. Just what I already posted.
Of course I got the entire stack trace here it is:
```
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 239, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 94, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 240, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 359, in open_http
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 372, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 665, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 635, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 661, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 359, in open_http
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 372, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 635, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 661, in redirect_internal
    return self.open(newurl)
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
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
```

Do you know if there is a way to bypass the problem file and install the rest of the fonts? For instance is [COLOR=#000000] ttf-mscorefonts-installer on disk somewhere that can be modified after the install fails?[/COLOR]

Actually there is one more piece of information. I live in Cambodia and my internet ip address says Vietnam. Now only one of the fonts are failing, but is it possible this has something to do with the failure.

Actually, I found out how to download arial and the font that died before. They are .exe files and of course Ubuntu does not know what to do with them. I assume that [COLOR=#000000]ttf-mscorefonts-installer contains the code necessary to read the exe and extract. How can I get to that code without WINE?[/COLOR]

Solved!
Thank you for the observations. 
When I tried to download the font files directly it worked.
Since one of you had observed it might be a problem with a proxy I realized it might have simply been an internet connection problem.
I tried to install again and it worked perfectly.
Solution, patience!

---

### Post by kc1di on 2014-07-23
Glad it worked for you :)

---

### Post by howefield on 2014-07-26
> **BarryM said:**
> ...until I got to a Microsoft EULA dialog that had an <OK> at the bottom. There it all stuck. I can's click on the OK nor does [Enter] or [Esc] do anything. Any suggestions where I go from here?

Try pressing the tab key to highlight the OK, you should then be able to press enter.

---

