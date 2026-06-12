---
title: "Results of &quot;apt-get update&quot; command different than update manager"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by bouriquet on 2011-03-24
Hi, I'm wondering about something. 
I've run the command "sudo apt-get update" from terminal, showing no update to do.
Then I've run the update manager (System-Administration-Update Manager) and it has shown an update (adobe flash).

I thought that "apt-get update" command and update manager were the same... 
Why do I have different results ? Is something missing in my "sources.list" file ?

Thanks in advance for your help.

---

### Post by wojox on 2011-03-24
Update just refreshes your sources.

```
sudo apt-get upgrade
```

Will show you what's available.

From the command line run

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by alexcckll on 2011-03-24
If you click on the "Check" button and supply your password - this is the same as apt-get update.  Clicking "Install" is the equiv of sudo apt-get upgrade.

---

### Post by bouriquet on 2011-03-24
Ok! Thanks a lot!

---

### Post by KegHead on 2011-03-24
Hi!

I always use  -f.

sudo apt-get update -f
sudo apt-get upgrade -f
sudo apt-get dist-upgrade -f

KegHead

---

