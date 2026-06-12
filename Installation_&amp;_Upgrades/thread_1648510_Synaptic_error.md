---
title: "Synaptic error?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by owkaye on 2010-12-18
> Failed to fetch [http://security.ubuntu.com/ ubuntu/dists/maverick-security/Release.gpg]("http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg")  

Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

Some index files failed to download, they have been ignored, or old ones used instead.Why am I getting this error when I click the Synaptic Reload button?  How can I resolve this problem?

---

### Post by sikander3786 on 2010-12-19
Is it happening with only one repository or all of them? In order to let us know, from Applications > Accessories > Terminal, post the _complete_ output of this command.

```
sudo apt-get update
```

While posting, click the # icon and paste your text in between the generated code tags. In other words, instead of using [quote] tags, use [code] tags ;-)

---

