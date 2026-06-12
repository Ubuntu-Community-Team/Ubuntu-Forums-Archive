---
title: "Having trouble adding pcsx2 PPA"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by murderd2death on 2012-04-22
Whenever i try to add th pcxs2 ppa from terminal i get this.

```
wintermute32@wintermute32-Lenovo-B570:~$ sudo add-apt-repository ppa:gregory-hainut/pcsx2.official.ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 83, in get_ppa_info_from_lp
    return json.loads(lp_page)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded

```

any suggestions on what to do or other packages i need to get for this to work?

[Here]("https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa") is where the PPA is located on launchpad.

---

### Post by dino99 on 2012-04-22
you need to be a little bit more curious to find a workaround:

Technical details about this PPA
This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.

Display sources.list entries for: 
deb [http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu](http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu](http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
Signing key:
1024R/7A617FF4 (What is this?)
Fingerprint:
A36D8D60D79F0F65D2B81421508A982D7A617FF4

---

