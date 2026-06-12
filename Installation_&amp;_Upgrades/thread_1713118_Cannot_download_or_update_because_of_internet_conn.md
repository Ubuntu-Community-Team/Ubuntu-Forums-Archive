---
title: "Cannot download or update because of internet connection?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by brainmurphy1 on 2011-03-23
I tried to download some software from the Ubuntu software center, and it does not download. It does not give me an error message, it just stays at 0 bytes.
It eventually tells me to check my internet connection. (this does not make sense because I am using it to write this thread) I checked synaptic package manager for correct proxy settings and it was ok. I ran  ```
sudo apt-get update
``` but to no avail. I am using wireless, and recently dissembled the computer to disconnect the CMOS battery, but I *think* that it was put back together properly.

---

### Post by ajgreeny on 2011-03-23
What error messages did you get from that command?  Can you use a cable ethernet connection to update?

---

### Post by tommcd on 2011-03-23
> **brainmurphy1 said:**
>  I checked synaptic package manager for correct proxy settings and it was ok. 
If you are behind a proxy, this is likely the source of the problem. Do you have to use a proxy? If not, then do not use a proxy and you will probably be ok. Otherwise, there is likely something wrong with your proxy settings.

Also post the output of: ```
sudo apt-get-update
``` from the terminal.
And welcome to the Ubuntu forums!

---

### Post by agarner98 on 2011-03-24
Check your proxy, use a neighbor's connection, or just reset your router/connection. simple as that. i get these issues, too.

---

