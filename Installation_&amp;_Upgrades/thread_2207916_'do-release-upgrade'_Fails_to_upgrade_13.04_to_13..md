---
title: "'do-release-upgrade' Fails to upgrade 13.04 to 13.10"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by moc10x on 2014-02-25
When attempting to run a "sudo do-release-upgrade -d" (though the behavior is the same when attempting the release upgrade from the GUI) in order to upgrade from 13.04 to 13.10, I receive quite a few errors similar to that below before the upgrade fails and reverts any changes:

```
Failed to fetch
http://archive.ubuntu.com/ubuntu/dists/saucy-security/universe/i18n/Translation-en
Cannot initiate the connection to *<xxxx>*:80 (0.0.8.219). - connect (22:Invalid argument)
```
Where *<xxxx>* is my proxy port (i.e., the port only--*not* the proxy address followed by the port like I would expect, which I suspect is the issue).

It's apparent when I attempt the same via update-manager that while it passes the 'Preparing to upgrade' portion, it fails during the 'Setting new software channels' piece.

My **/etc/apt/apt.conf** file looks as follows (with actual addresses omitted):

```
Acquire::http::Proxy "http://*<proxy FQDN>:<proxy port>*/";
```
My **/etc/environment** file looks as follows (with actual addresses omitted):

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"        
http_proxy=http://*<proxy FQDN>:<proxy port>*/                                                     
https_proxy=http://*<proxy FQDN>:<proxy port>*/                                                    
ftp_proxy=http://*<proxy FQDN>:<proxy port>*/                                                      
HTTP_PROXY=http://*<proxy FQDN>:<proxy port>*/                                                     
HTTPS_PROXY=http://*<proxy FQDN>:<proxy port>*/                                                    
FTP_PROXY=http://*<proxy FQDN>:<proxy port>*/
```
My **~/.bashrc** file contains no references to any proxy env variables.

I have no issues using apt-get for updating packages or kernel upgrades or the like.  Wget works fine for downloading, as does any type of internet browsing in a browser.  I've exhausted all sorts of web searches and while I've come across many similar issues, I've not seen one that applies to or resolves mine in particular.

Thanks very much in advance for any input you can provide!

-M

---

