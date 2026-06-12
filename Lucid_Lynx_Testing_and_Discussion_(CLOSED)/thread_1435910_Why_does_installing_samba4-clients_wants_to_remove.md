---
title: "Why does installing samba4-clients wants to remove ubuntu-desktop?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-22
i want to install samba4 in order to try and check some problems in my home network like why i can't i print from remote computer in my printer despite the fact that it shared and i managed to add it to xp and it said port open and also why i can't connect to my computer remotly despite the fact that i enabled it but ** samba4-clients** wants me to remove smbclient and ubuntu-desktop does any body know why?

thanks in advance.

---

### Post by dino99 on 2010-03-22
why not let it doing so then reinstall desktop

---

### Post by cgroza on 2010-03-22
Its ok to remove ubuntu-desktop because ubuntu-desktop is just an empty package that points to other packages.

---

### Post by Eclipse. on 2010-03-22
ubuntu-desktop is a meta package that just says install everything that comes by default. So removing anything that is installed by default removes the package.

---

### Post by aviramof on 2010-03-22
ok thanks for the information.

---

### Post by aviramof on 2010-03-22
> **dino99 said:**
> why not let it doing so then reinstall desktop

i can't reinstall it without uninstall samba4-clients

---

### Post by emarkay on 2010-03-22
> **cgroza said:**
> Its ok to remove ubuntu-desktop because ubuntu-desktop is just an empty package that points to other packages.

In this case, I suggest that that package"Ubuntu-Desktop" be renamed so  it doesn't appear as if removing it (I have seen this a few times in the  past few years) may trash the system to the uninformed.

---

