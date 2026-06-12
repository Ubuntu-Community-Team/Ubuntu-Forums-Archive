---
title: "update manager wont work?"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by Def215 on 2011-12-14
ok, so i have an issue with my ubuntu partition. after my laptop went crazy and had to do a boot repair, my update manager stopped working. when i run my update manager, i get a pop up that says this:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.'

that popup comes up with that text in it after the update manager fails to finish the upload.

i tried to do it manually through the terminal by putting in sudo apt-get update, but i get the same message 

i also got this message too:

SystemError: installArchives() failed

thanks for looking. if its any help to troubleshoot my problem, im on ubuntu 10.10

---

### Post by Def215 on 2011-12-15
bump. 

can anyone help me. i think i solved the problem with the /var/lib/dpkg/status because i dont get that code any more but im still getting the SystemError: installArchives() failed message when i try to get apps from the software center.

---

### Post by BC59 on 2011-12-15
What is happening after running those commands?

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by PTOPedro on 2011-12-15
Having same problem here. Come back in terminal as:


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by BC59 on 2011-12-15
> **PTOPedro said:**
> Having same problem here. Come back in terminal as:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Open a terminal with CTRL+ALT+T and run:

```
gksudo nautilus
``` put your password

Then from the root nautilus opened go to file system--var--lib--dpkg and rename the file status to status1 and available to available1. Then rename the file status-old to status and available-old to available.

Close nautilus and run to the termminal

```
sudo apt-get update
```

---

### Post by PTOPedro on 2011-12-15
That did it, Thanks a bunch!

---

### Post by Def215 on 2011-12-15
i tried both things and it still gives me the same error message. it still says installArchives() failed.

---

