---
title: "installing samba"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Advait on 2010-02-25
Hi All,

From what I can see it looks like I need to install Samba before I can share files between my Ubuntu 9.10 and Win7. I went to samba.org and they report the latest version of Samba as 3.4.6. When I searched for Samba in the Ubuntu software center, they report the Samba version as Version: 1.2.63-0ubuntu4 (system-config-samba).

Version 1.2.63 seems really old. Am I missing something? How can I install the latest version of Samba?

Thanks,

Tom the Uber Newbie

---

### Post by johnson.d on 2010-03-04
System-config-samba is a front-end GUI tool for managing Samba server.You can try installing Samba server using synaptic package manager. You can follow this procedure to install the latest Samba version supported by Ubuntu.

1) Goto System->Administration->Synaptic Package Manager
2) At the search box type 'samba'
3) It will list all the softwares that contain the name 'samba'
4) Select 'Samba'and Mark for installation
5) Click apply.

If you want to install the latest source version of Samba you can download it and install manually by downloading it manually from [http://samba.org](http://samba.org)

---

### Post by madmax.santana on 2010-03-04
Or, if you like to go hardcore with Linux, play around with console!

Applications -> Accessories -> Terminal

Then type

```
sudo apt-get update
```

Requires your password and then it will retrieve lists of packages from repositories.

Then

```
sudo apt-get install samba samba4
```

Howsoever, method provided by johnson.d is fully functional and easiest!

---

### Post by Advait on 2010-03-04
Hi,

Thanks very much for the info. It turns out I had a misunderstanding of Samba. I thought I needed it in order to look at the files on my Windows 7 partition. I have Ubuntu 9.10 and Win7 installed in two separate partitions on my laptop. Much to my surprise, I discovered I was able to look at my Windows files directly from the file navigator in Ubuntu.

I'm not connected to any kind of network. I'm only connected to the internet.

Thanks

---

