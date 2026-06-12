---
title: "How to disable Ubuntu CD as a repository?"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by ChantCd_com on 2006-08-22
Can't seem to find out how to do that. Thanks!

Matthew

---

### Post by cstudent on 2006-08-22
Open a terminal window (Applications Menu>>Accessories>>Terminal)

and edit your sources list by entering at the prompt:
```

gksudo gedit /etc/apt/sources.list

```

An editor will open up with your repo source list. Put a # in front of the line for the CD. You'll see other examples of this in the file to go by. Close and save the file. Then run at the prompt.
```

sudo apt-get update

```

---

### Post by aysiu on 2006-08-22
Alternatively, if you're using Ubuntu, go to System > Administration > Synaptic Package Manager > Settings > Repositories and uncheck the box next to the CD repository.

---

### Post by m83 on 2006-08-22
Another way (I would say even simpler than Synaptic) is go to System->Administration->Software Preferences and disable the CD channels.

---

