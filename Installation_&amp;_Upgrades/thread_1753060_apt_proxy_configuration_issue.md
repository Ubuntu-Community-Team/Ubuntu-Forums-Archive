---
title: "apt proxy configuration issue"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by sunny5280 on 2011-05-08
I recently installed Ubuntu 9.04 and I'm having issues with apt-get and proxy configuration.
 
Upon initial install I attempted to set the proxy configuration through the GUI and opted for the "manual proxy" configuration. Part way through entering the proxy server name I decided to use the "automatic proxy" configuration option instead. I checked this radio box and entered the URL to automatically configure the proxy information.
 
At this point everything seeemed to work fine. I ran "apt-get update" and, partway through the update process, I decided to abort the update by pressing control-c. Now I am unable to use apt-get to perform any updates. It gives me several errors stating it is unable to resolve "www" (which is the partial name of the proxy server I began to enter before deciding to use the auto configuration option).
 
No problem I thought...I'll just go into "/etc/apt/apt.conf" and change the name. Except the name in the apt.conf file is correct. I brought up "synaptic" and changed the network configuration there (as it had the same issue) and now synaptic works fine. I am also able to use the GUI Update Manager to update my system. Still apt-get update fails. Here is one of the error lines it spits out:
 
```
 
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Could not resolve 'www'

```
 
This is repeated with a number of other different URLs. The problem being the "www". As I mentioned earlier it was the part of the proxy server name I initially entered before selecting the "Automatic configuration" option. My question is: Where else do I need to look to change this name? Here is the contents of my /etc/apt/apt.conf file (name changed to a generic name):
 
```
 
user@ubuntu9.04:/etc/apt$ more apt.conf
Acquire::http:proxy "[http://my-proxy.mycompany.com:80/](http://my-proxy.mycompany.com:80/)";
Acquire::ftp:proxy "[ftp://my-proxy.mycompany.com:80/](ftp://my-proxy.mycompany.com:80/)";
Acquire::https:proxy "[https://my-proxy.mycompany.com:80/](https://my-proxy.mycompany.com:80/)";

```
 
These were configured through the GUI with the "Apply system wide" setting. I used the Update Manager to ensure the system is up to date and still I receive the error.
 
Any help appreciated.

---

### Post by sunny5280 on 2011-05-09
Update for future reference. The issue appears to have resolved itself. I am now able to use apt-get without problem. As I did not change anything I can only assume there was a cache issue which expired.

---

