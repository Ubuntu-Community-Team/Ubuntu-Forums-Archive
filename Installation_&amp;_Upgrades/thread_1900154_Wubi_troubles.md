---
title: "Wubi troubles"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by Unkn0wn1 on 2011-12-25
I have recently got a netbook (Well, today) and wanted to run linux on it. After finding out it had to small a screen for Ubuntu 11.x, I found out about the netboook version in earlier ones. I have downloaded Wubi and the image of the netbook version, namely 
ubuntu-10.04-netbook-i386.iso, opened up Wubi, and started to install (I DID select netbook, before you ask), and instead of using the image, like expected, it stated downloading another one. With the torrent taking predicted 23 hours, even though the actual image took me about 20mins to download, I don't think this is really practical. Help me!

---

### Post by darkod on 2011-12-25
If you are sure you have the wubi.exe for the same version (image), because it will work only with the same one, you need to put wubi.exe and the ISO in a same folder and execute the .exe. That way it will use the ISO and not start downloading. Only if they are in the same folder, as far as I know.

Wubi installs ubuntu inside windows, is this what you want? It always works better as proper dual boot, or you can replace windows with ubuntu if that's what you want.

Also, the desktop image works just fine on 10" netbook, I have it on mine (not the netbook version).

---

### Post by Unkn0wn1 on 2011-12-25
It has the wonderfully awkward resolution of 1024x600, so well, desktop needs 768 height :(
Edit: Would it need to be in a sub of my download folder, or is it ok to have 'em outside. Just had a failed Xubuntu-Wubi install :(

---

### Post by darkod on 2011-12-25
I don't use wubi but as far as I know, where ever you want.
The only requirement is that wubi.exe and ubuntu-blahblah.iso files are in the same folder. And that the wubi.exe is for that exact ISO file, because if it's for different it will start downloading it even if they are in the same folder.

Another way to go, if you have any software that can look inside ISOs and extract files, the wubi.exe is also in the ISO. You can extract just that one file, put them together in the same folder as already said, and fire away. This way you are sure that the wubi.exe is for that exact ISO.

---

### Post by Unkn0wn1 on 2011-12-25
Glad to tell ya that I've just successfully Wubi'd 10.10 Netbook onto my N130. Gonna boot into it tomorrow, as I remember something about those RealTek drivers...
Thanks,

Unkn0wn1

BTW, I am using Wubi as I am just trying out Ubuntu, and want the option to uninstall it easily

---

