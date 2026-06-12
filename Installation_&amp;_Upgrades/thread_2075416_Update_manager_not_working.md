---
title: "Update manager not working"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by 5prasad on 2012-10-23
hello all,


I have updated Ubuntu 12.04 to 12.10. During installation Question was that if you keep keep the packages which are not needed but mistakenly I kept the 12.04 packages. So now update manager is showing following error.

The installation or removal of a software package failed.


installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 213466 files and directories currently installed.)
Preparing to replace libdrm2:amd64 2.4.39-0ubuntu1 (using .../libdrm2_2.4.39-0ubuntu1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
dpkg: error processing /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm2/changelog.Debian.gz', which is different from other instances of package libdrm2:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb
Error in function: 



This is causing many error. Such as speaker and dropxbox not working. I am in real mess.

Please help.
Any help is appreciated.
thanks in advance.

---

### Post by nisith on 2012-10-23
I had the same problem. Try this command in the terminal (Ctrl + Alt + T):

```
sudo rm /usr/share/doc/libdrm2/changelog.Debian.gz
```

After that, run the Update Manager again.It should be able to complete any pending operations. Your loss of audio may not be related to this though...
[[COLOR="Blue"]Related bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1068165")

---

### Post by Raptor354 on 2012-10-24
I had the same problem as described in the OP regarding libdrm2.  However, audio and Dropbox worked and works fine for me before and after the dist upgrade.

nisith's solution worked for me.  Thanks, nisith.  If I was wearing a hat, I would have tipped my hat at you.

---

### Post by 5prasad on 2012-10-24
Thanks a lot nisith . Update manager is working now. But dropbox and speakers are still not working.  Can you suggest something for that.

---

### Post by OKK@oR7rb§yWcvIM£ on 2012-11-10
Thanks  nisith

---

### Post by Erufailon on 2012-11-16
Thank you nisith for your help. It solved the same problem I had with libdrm2 package.

@5prasad
Maybe you should change the status of the  thread to [Solved] and I suggest to add the package name to the title because I was searching for the problem with the package name and I suppose many others do the same as it is a "package specific" problem/bug and not a problem/bug of the update manager, thank you.

---

### Post by Frogster on 2012-11-21
Thanks nisith

---

### Post by softwareregisterac on 2012-12-13
Thanks nisith !!! Your solution worked for me !!!

---

### Post by spensk8 on 2012-12-30
Thanks a lot! It worked for me :)

---

### Post by GMeister on 2013-03-17
Thanks - worked!

---

