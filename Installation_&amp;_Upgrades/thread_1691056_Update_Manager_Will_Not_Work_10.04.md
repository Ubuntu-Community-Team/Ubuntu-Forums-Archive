---
title: "Update Manager Will Not Work 10.04"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by TheBiggoronsword on 2011-02-19
Recently I have tried to run the update manager and got this message: Failed To Load Package List

E:Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list, E:The list of sources could not be read.

I tried to run sudo apt-get update in terminal, and got the same error message.

I think it could be fixed by reseting the respositories, but I do not know how to do so.  Any help would be appreciated.

---

### Post by dino99 on 2011-02-19
into a terminal:

sudo rm /var/cache/apt/archives/*

your akirad entry is weird, so remove it into synaptic repo tab (third parties), then check to add a repo and copy/paste:

ppa:akirad/akirad

then update, upgrade

explained here: [https://launchpad.net/~akirad/+archive/akirad](https://launchpad.net/~akirad/+archive/akirad)

---

### Post by TheBiggoronsword on 2011-02-20
I forgot to mention that synaptic says  "the list of sources could not be read" and then it auto-closes
also get message E:_cach->open() failed, please report.  
 
i ran in terminal the commands you posted, and it said file could not be found
 
I'm thinking of just doing a clean install of 10.10 if I can't get this fixed soon

---

### Post by sikander3786 on 2011-02-20
No big deal in correcting this simple error and it would be such a loss of time and energy to do a re-install for it.

From Terminal, please post the outputs of these commands.

```
sudo rm /etc/apt/sources.list.d/akirad.list
```

```
sudo apt-get update
```

If there are erros, please post the output of these one's as well.

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readibility purposes.

---

### Post by TheBiggoronsword on 2011-02-20
No need to post code; it worked! Thank you, even if this was a simple error. I am still getting used to terminal.

---

