---
title: "what is sudoer file"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by asterix404 on 2005-10-19
I am a reacent arival to ubuntu and i was told that this is where all the funs tuff happens for root and su and stuff like that. I have looked online and basicly found nothing. I need to be able to use my regular user to sudo since... I want to. How do I do this? I also have a root user on my computer. I don't like this and I want it off. How do I do that? Thank you very much.

---

### Post by adwait on 2005-10-19
First, use (as root)
```
visudo
```
That will open the sudoers file, which is basically a file which contains the list of usernames that are allowed to use the sudo command. Now add the line
> 
<username>       ALL=(ALL) ALL


Now try using sudo.....you should be able to. 
Now for lokcing the root account, use
```
sudo passwd root -l
```

---

