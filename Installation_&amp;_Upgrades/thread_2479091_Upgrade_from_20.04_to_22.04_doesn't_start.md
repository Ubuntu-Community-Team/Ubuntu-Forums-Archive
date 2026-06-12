---
title: "Upgrade from 20.04 to 22.04 doesn't start"
date: 2022-09-14
forum: Installation &amp; Upgrades
---

### Post by luca-dgh on 2022-09-14
HI!
I have a 20.04 installed on my laptop, no unofficial repos, everything is updated, ubuntu-desktop package is installed.
When I use graphic method it doesn't say anything, just doesn't start, so I used terminal command "sudo do-release-upgrade".
As you can see it stucks on the "check for a new version". How can I fix it?

---

### Post by mikewhatever on 2022-09-14
Who said we can see anything? You've posted screenshots of terminal windows, presumably with some text output. 
Why not copy/paste the output itself?
Do you want answers as text in a screenshot too?

---

### Post by #&amp;thj^% on 2022-09-14
> **luca-dgh said:**
>  it stucks on the "check for a new version". How can I fix it?

Try keyboard combo  <Ctrl + z>

---

### Post by grahammechanical on 2022-09-14
To copy text from the terminal, first select it then press Shift+Ctrl+c. To paste into the terminal, press Shift+Ctrl+v. 

Click the icon of the three parallel lines. Then select Properties>Shortcuts to see all the key combinations that are effective in the terminal in Ubuntu 20.04.

Regards

---

### Post by luca-dgh on 2022-09-16
sorry for that, I didn't paste the terminal output just because there is no errors, as I said before it only stay there without do nothing. I posted the desktop screenshot just to let see that the cpus are quiet (0%) and internet as well (no traffic UP or DOWN).
Anyway, after a while I hit CTRL+C and the output is
```
luca@laptop-luca:~$ sudo do-release-upgrade 
[sudo] contraseña para luca: 
Comprobar si hay una nueva versión de Ubuntu
^CTraceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 251, in <module>
    fetcher.run()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 239, in run
    if not self.fetchDistUpgrader():
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 196, in fetchDistUpgrader
    uri = self._expandUri(self.new_dist.upgradeToolSig)
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 166, in _expandUri
    new_uri = self.mirror_from_sources_list(uri, self.DEFAULT_MIRROR)
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 152, in mirror_from_sources_list
    if url_downloadable(mirror_uri, self._debug):
  File "/usr/lib/python3/dist-packages/DistUpgrade/utils.py", line 263, in url_downloadable
    http_file = urlopen(HeadRequest(uri))
  File "/usr/lib/python3.8/urllib/request.py", line 222, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.8/urllib/request.py", line 525, in open
    response = self._open(req, data)
  File "/usr/lib/python3.8/urllib/request.py", line 542, in _open
    result = self._call_chain(self.handle_open, protocol, protocol +
  File "/usr/lib/python3.8/urllib/request.py", line 502, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.8/urllib/request.py", line 1383, in http_open
    return self.do_open(http.client.HTTPConnection, req)
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
  File "/usr/lib/python3.8/http/client.py", line 922, in connect
    self.sock = self._create_connection(
  File "/usr/lib/python3.8/socket.py", line 796, in create_connection
    sock.connect(sa)
KeyboardInterrupt

```

---

### Post by luca-dgh on 2022-09-16
> **1fallen said:**
> Try keyboard combo  <Ctrl + z>

Yes thanks, but this doesn't solve the problem, it just ends the execution of the script. I wish to upgrade.

---

### Post by #&amp;thj^% on 2022-09-16
> **luca-dgh said:**
> Yes thanks, but this doesn't solve the problem, it just ends the execution of the script. I wish to upgrade.

Yep, wasn't meant to solve the upgrade problem, just get you unstuck on a hung command.
Show us this:
```
apt policy update-manager-core
```
if nothing shows as installed then use:
```
sudo apt install update-manager-core
```
EDIT:I left this out but do "update and upgrade" before "do-release" and be sure to disable any PPA's you have installed.
so use:
```
sudo apt update
sudo apt-get dist-upgrade
sudo apt autoremove
```
then run again:
```
sudo do-release-upgrade 
```

---

### Post by luca-dgh on 2022-10-15
Sorry for delay, life sometimes drive us in a direction very far from our desires.
here the output required:
```
luca@laptop-luca:~$ sudo apt policy update-manager-core
update-manager-core:
  Instalados: 1:20.04.10.10
  Candidato:  1:20.04.10.10
  Tabla de versión:
 *** 1:20.04.10.10 500
        500 http://pe.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://pe.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:20.04.9 500
        500 http://pe.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://pe.archive.ubuntu.com/ubuntu focal/main i386 Packages

```

I go ahead with the other commands.

---

### Post by luca-dgh on 2022-10-15
@1fallen
very thanks, now it is upgrading to 22.04.
Excelent

---

### Post by TheFu on 2022-10-15
> **luca-dgh said:**
> Yes thanks, but this doesn't solve the problem, it just ends the execution of the script. I wish to upgrade.

Actually, cntl-z stops the job, it doesn't terminate it.  To terminate it, cntl-c is necessary, perhaps a few times.
cntl-z is normal "job control" for any Unix.  There are fg, bg, jobs and kill commands which are part of Unix job control.

---

