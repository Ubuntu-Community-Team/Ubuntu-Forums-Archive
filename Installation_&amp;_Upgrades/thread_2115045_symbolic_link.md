---
title: "symbolic link"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by findingthebalance on 2013-02-11
I am a new Ubuntu user.

I just installed Komodo edit via Terminal and it says Komodo Edit 7 has been successfully installed to: /root/Komodo-Edit-7. It then tells me I should create a symbolic link to 'komodo', e.g.:

 ln -s "/root/Komodo-Edit-7/bin/komodo" /usr/local/bin/komodo

I do not know how to do this and cannot fine clear instructions on how to proceed. Is there step by step instructions to assist me. Also, if I wanted to uninstall this program from the root folder how would one go about such a task? I cannot access the root folder.

---

### Post by tgalati4 on 2013-02-11
Open a terminal:  (cut and paste)

```
sudo ln -s "/root/Komodo-Edit-7/bin/komodo" /usr/local/bin/komodo
```

To remove, there may be a removal script in /root/Komodo, or just remove it using the sudo rm command.

---

### Post by The Cog on 2013-02-11
Just enter the command into the terminal and press enter.

The command has to be run as root, but I guess you know how to run commands as root since you just installed a program into root's home directory.

---

