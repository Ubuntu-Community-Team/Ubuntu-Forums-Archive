---
title: "updating errors"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Speakerspushair on 2008-10-02
Every time I try to upgrade I get the following error:

An error occurred:
W: Failed to fetch [http://www.bashterritory.com/pytube/releases/Release.gpg](http://www.bashterritory.com/pytube/releases/Release.gpg)  Could not resolve 'www.bashterritory.com'

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/en_US.bz2](http://www.bashterritory.com/pytube/releases/en_US.bz2)  Could not resolve 'www.bashterritory.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2008-10-02
Apparently, there is a third party repository unrelated to Ubuntu that gives you errors. Check if that repository is valid or disable it.

---

### Post by Speakerspushair on 2008-12-04
How do you check your repositories?

---

### Post by taurus on 2008-12-04
> 
The domain bashterritory.com has expired. If you owned this domain, please contact your domain registration service provider for further assistance. If you need help identifying your service provider, visit     [http://domainhelp.tucows.com](http://domainhelp.tucows.com).


So, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove that repo, bashterritory.com, from it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

