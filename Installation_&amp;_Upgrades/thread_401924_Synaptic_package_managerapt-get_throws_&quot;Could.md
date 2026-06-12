---
title: "Synaptic package manager/apt-get throws &quot;Could not resolve &lt;hostname&gt;&quot; message"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by amitst on 2007-04-05
Hi,

I need to use a proxy to connect to outside word. I can access Internet properly through Firefox (by doing the proxy settings).

The important thing is my password contains special characters like @. I assume the following auth credentials,
username: foo
password: pass@ord

To use the proxy for apt-get or for synaptic package manager I tried out the following settings,

- Changed the global proxy setting in,
 System -> Preferences -> Network Proxy -> Manual proxy config (entered username/passwd in details)

- Changed the /etc/apt/apt.conf file to have
Acquire::http::Proxy "http://foo:pass@ord@<proxyhost>:<proxyport>"

- Entered proxy info under System -> Administration -> Synaptic Pkg manager -> Settings -> Preferences -> Network

The above settings gave me "could not resolve 'ord@<proxyhost>' (for the 'sudo apt-get update)

So I put the @ character encoded in the setting string inside /etc/apt/apt.conf as follows,
Acquire::http::Proxy "http://foo:pass%40ord@<proxyhost>:<proxyport>"

Still I got the same error.

Secondly I am not happy about entering the password in clear text in one of the files.

Any suggestions?

Thanks in advance,
Amit

---

### Post by amitst on 2007-04-20
I found a solution to the above issue.

I used the NTLM Auth proxy server from [https://sourceforge.net/projects/ntlmaps/](https://sourceforge.net/projects/ntlmaps/) and changed my global proxy settings to this server port. The server now takes care of logging on to the proxy server with my username/password.

Thanks,
Amit

---

