---
title: "Update Manager unresolvable problem"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by harsh.kola on 2011-05-09
I am a new user to Ubuntu and recently once I updated the new Ubuntu 11.04 it was perfectly fine for the past two weeks until recently I am receiving the error when I try to update using update manager. Below I have attached error report or issue that I am facing:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened


Would appreciate any help in order to resolve this issue.

Thank You

---

### Post by cipherboy_loc on 2011-05-09
Try running the following from the command line (Applications -> Accessories -> Terminal):

```

sudo apt-get update

```

Post back with the results in <CODE> tags. If that works you should be able to update via update-manager  again.

Cipherboy

---

### Post by harsh.kola on 2011-05-10
I have tried that yet it errors out even then the error it shows looks like this:

< Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 232 kB in 3s (58.5 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened. >


I have also attached a screen shot of the error display on the terminal.

---

### Post by Frogs Hair on 2011-05-10
See this thread.[http://ubuntuforums.org/showthread.php?t=1752868&highlight=update+manager](http://ubuntuforums.org/showthread.php?t=1752868&highlight=update+manager)

---

### Post by harsh.kola on 2011-05-10
Thanks frogs hair tried the commands:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

It works!!!

---

