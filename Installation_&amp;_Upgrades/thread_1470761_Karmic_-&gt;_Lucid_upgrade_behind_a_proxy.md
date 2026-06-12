---
title: "Karmic -&gt; Lucid upgrade behind a proxy"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by jstammi on 2010-05-03
Hi,

the upgrade-manager shows me the new version 10.04 LTS but freezes after pressing the "Upgrade" button. "System Monitor" shows me in the "Waiting Channel" column "inet_wait_for_connect".

My machine is behind a proxy. Web access in general and normal system updates are working without any problems.

I tried to figure out the requested url that seems to block the upgrade manager. I with pressing the button I see a line 

7158	502.622360	<MY LOCAL IP>	141.30.13.21	TCP	51958 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=368970 TSER=0 WS=7

This looks to me as if the upgrade manager does not regard the proxy setting. Or am I wrong with this?

Anyone upgraded from behind a proxy already successfully?

---

### Post by lenanu on 2010-05-03
Hi,

I have a similar (if not identic) issue. I am behind a MS proxy with authentication. To bypass it, I use cntlm on my machine. For evey app that requires Internet access (including wget, apt ...) I use [http://127.0.0.1:3128](http://127.0.0.1:3128), that I have set in my environment variables. Everything works correctly except the ubuntu version upgrade.

update-manager shows the new version and freezes when trying to install it.
Trying to launch the command "do-release-upgrade" also freezes after displaying "Checking for a new ubuntu release"

When I cancel it (CTRL+C), it always shows the same things :
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 61, in <module>
    fetcher.run()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 235, in run
    if not self.fetchDistUpgrader():
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 203, in fetchDistUpgrader
    uri = self._expandUri(self.new_dist.upgradeToolSig)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in _expandUri
    new_uri = self.mirror_from_sources_list(uri, self.DEFAULT_MIRROR)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 164, in mirror_from_sources_list
    if url_downloadable(mirror_uri, self._debug):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/utils.py", line 105, in url_downloadable
    c.request("HEAD", path)
  File "/usr/lib/python2.6/httplib.py", line 898, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python2.6/httplib.py", line 935, in _send_request
    self.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 892, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 764, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 723, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 704, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 507, in create_connection
    sock.connect(sa)
  File "<string>", line 1, in connect

Would it be the perl libraries that do not get the correct proxy settings ?
Any idea how to solve this would be greatly appreciated.

Thanks,
 - emmanuel

---

### Post by Joshua1981 on 2010-05-03
Same problem for me!

netstat -tpn shows that some python script tries direct connection to some debian mirrors. The server addresses keep changeing, so I guess update-manager (is it python?) makes several attempts and times out every time.

I have set the system-wide http proxy in network proxy GUI wizard, the http_proxy variable and the apt configuration option. I wonder if there's a separate config option for python or any other workaraoud?:confused:

---

### Post by jstammi on 2010-05-03
Hi,

I just got asked (two hours later!!!) for my password for administrative tasks. I had kept the upgrade-manager running and now it seems to go on. So just leave the update-manager running and wait. Just at the moment it is now downloading the packages with using the proxy as one would expect.

Is this filed already as a bug? Else I would do now as it seems as if it is a problem in principle ...

---

### Post by jstammi on 2010-05-03
Filed bug: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/574439](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/574439)

---

### Post by lenanu on 2010-05-04
Hello,

I confirm the long-delay issue : I launched do-release-upgrade yesterday evening before leaving work and this morning it was waiting for my input with the usual
"Fetching and installing the upgrade can take several hours. Once the
download has finished, the process cannot be cancelled.

 Continue [yN]  Details [d]y"

 - emmanuel

---

