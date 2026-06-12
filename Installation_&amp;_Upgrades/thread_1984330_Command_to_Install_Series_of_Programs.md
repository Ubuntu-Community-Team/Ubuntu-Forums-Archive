---
title: "Command to Install Series of Programs"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Altin on 2012-05-21
After using Ubuntu Netbook Remix 10.04 for the last 2 years I recently upgraded to Ubuntu 12.04 & what a difference! After using it for some time Ive decided Unity's not for me & have reinstalled Xubuntu on my netbook. I now have to reinstall the programs I had used previously & rather than installing them one by one I was wondering what command would work to line them up & download & install them in series overnight for me. Should I use 'sudo apt-get install -y program1; sudo apt-get -y install program2; ...' or 'sudo apt-get install -y program1 && sudo apt-get install -y program2 && ...'?

---

### Post by cortman on 2012-05-21
If you know the names of the programs it's as simple as

```
sudo apt-get install -y gimp xchat emacs agave firefox
```

for example.

---

