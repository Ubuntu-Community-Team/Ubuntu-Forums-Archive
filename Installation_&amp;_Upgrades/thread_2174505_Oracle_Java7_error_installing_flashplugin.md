---
title: "Oracle Java7 error installing flashplugin"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by Vijendra_Singh_Aswal on 2013-09-14
I have been having problems with Oracle Java latetly on my Ubuntu 13.04. Somehow my Flash Player plugin does not work anymore. And when i try to re-install it get the following error. Please help. Thanks.

I have OpenJDK 7 installed.

vijendra@vijendra-Rev-1-0:~$ sudo apt-get install flashplugin-installer
[sudo] password for vijendra: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/6,990 B of archives.
After this operation, 139 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-installer
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 410563 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.310ubuntu0.13.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.310.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.310.orig.tar.gz)
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
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
  File "/usr/lib/python2.7/urllib.py", line 674, in http_error_307
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 635, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 661, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 437, in open_https
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 969, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 829, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 791, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 1176, in connect
    self.sock = ssl.wrap_socket(sock, self.key_file, self.cert_file)
  File "/usr/lib/python2.7/ssl.py", line 440, in wrap_socket
    ciphers=ciphers)
  File "/usr/lib/python2.7/ssl.py", line 200, in __init__
    self.do_handshake()
  File "/usr/lib/python2.7/ssl.py", line 362, in do_handshake
    self._sslobj.do_handshake()
IOError: [Errno socket error] [Errno 8] _ssl.c:504: EOF occurred in violation of protocol
Setting up oracle-java7-installer (7u40-0~webupd8~0) ...
Downloading Oracle Java 7...
Error parsing proxy URL [http://iit2011151:mojo77##@172.31.1.4:8080/:](http://iit2011151:mojo77##@172.31.1.4:8080/:) Bad port number.
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.

dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up flashplugin-installer (11.2.202.310ubuntu0.13.04.1) ...
Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

