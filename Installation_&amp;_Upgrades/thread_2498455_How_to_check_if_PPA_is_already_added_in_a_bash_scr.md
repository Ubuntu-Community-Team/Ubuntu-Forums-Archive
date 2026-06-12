---
title: "How to check if PPA is already added in a bash script"
date: 2024-06-14
forum: Installation &amp; Upgrades
---

### Post by alfredino on 2024-06-14
Hi,
I found a solution on [how to check if PPA is already added to apt sources list in a bash script]("https://askubuntu.com/questions/381152/how-to-check-if-ppa-is-already-added-to-apt-sources-list-in-a-bash-script")[FONT=inherit].[/FONT]
The code worked fine until the previous version of ubuntu 22.04. Now I noticed that the file /etc/apt/sources.list has been moved to /etc/apt/sources.list.d/ubuntu.sources.
Moreover, the "format" of the file has been changed (it no longer contains the deb prefix for some PPAs).
"Old"
```
deb [arch=amd64 signed-by=file.gpg] URL stable main

```
"New"
```
Types: deb
URIs: URL
Suites: noble
Components: main
Signed-By:

```

I then modified the code accordingly by removing ^.deb and it works fine. Is this correct? Or is there a better way to achieve this?
```

myPPA=
if ! grep -q ".*$myPPA" /etc/apt/sources.list.d/*; then
     add-apt-repository ppa:$myPPA -y
fi

```

Thank you

---

