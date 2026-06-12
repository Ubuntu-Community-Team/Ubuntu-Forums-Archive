---
title: "Not able to install pip"
date: 2017-06-29
forum: Installation &amp; Upgrades
---

### Post by plopmon on 2017-06-29
for installing google assistant on ubuntu i need to install pip. i followed this tutorial [https://stackoverflow.com/questions/33023599/usr-local-bin-python-no-module-named-pip](https://stackoverflow.com/questions/33023599/usr-local-bin-python-no-module-named-pip) . on executing this command sudo pip install requests, this happens-

The directory '/home/jayant/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/jayant/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting requests
Downloading requests-2.18.1-py2.py3-none-any.whl (88kB)
100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 92kB 185kB/s 
Collecting idna<2.6,>=2.5 (from requests)
Downloading idna-2.5-py2.py3-none-any.whl (55kB)
100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 61kB 1.2MB/s 
Collecting urllib3<1.22,>=1.21.1 (from requests)
Downloading urllib3-1.21.1-py2.py3-none-any.whl (131kB)
100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 133kB 412kB/s 
Collecting chardet<3.1.0,>=3.0.2 (from requests)
Downloading chardet-3.0.4-py2.py3-none-any.whl (133kB)
100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 143kB 1.1MB/s 
Collecting certifi>=2017.4.17 (from requests)
Downloading certifi-2017.4.17-py2.py3-none-any.whl (375kB)
100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 378kB 702kB/s 
Installing collected packages: idna, urllib3, chardet, certifi, requests
Found existing installation: chardet 2.3.0
Uninstalling chardet-2.3.0:
Successfully uninstalled chardet-2.3.0
Successfully installed certifi-2017.4.17 chardet-3.0.4 idna-2.5 requests-2.18.1 urllib3-1.21.1

what does the text in yellow means? because the same color was there in terminal also. because then also pip is not installed. this error shows up, no module named pip

---

### Post by deadflowr on 2017-06-29
> what does the text in yellow means? because the same color was there in terminal also. because then also pip is not installed. this error shows up, no module named pip
I reset that for you, so others can actually read it.
that said, it's telling you that if you need to run pip with sudo, then use the -H flag.
That sets it to preserve the user's home environment settings. Basically.

---

### Post by plopmon on 2017-06-29
Thanks

---

