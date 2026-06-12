---
title: "problems with command-line install"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by Slipperyfish on 2008-11-16
ok, here's the scoop; I installed a command-line installation (8.10) to a SanDisk Mini flash drive. It installed just fine. It boots up great too, but whenever i try to edit or add or move a file, it kept telling me i needed administrative powers. If i use sudo then it works fine. It doesn't do that with regular ubuntu installs. How can i make it stop doing that. 

The other problem is that whenever i try to play a mp3 file with mplayer, it starts to play but there's no sound. But, if i use sudo, there is sound.

I have alsa-base installed to, but i can only run asla-mixer with sudo. 

any help is appreciated.

---

### Post by Partyboi2 on 2008-11-16
If you are trying to move, delete,copy etc.. files that are not in your /home folder then you will need to use sudo this applies to the "normal" ubuntu install. If you are doing work where you need admin rights alot you can use
```
sudo -s
```

---

### Post by Slipperyfish on 2008-11-17
Whenever I try to move or edit something in my home directory, it keeps telling me that i have insufficient privileges.

---

### Post by Partyboi2 on 2008-11-17
What is the permissions for your /home folder
```
ls -l  /home
```

---

