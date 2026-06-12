---
title: "selecting specific updates from terminal"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by raja.genupula on 2011-08-25
i know selecting updates from update manager , i am curious to know to do this from terminal . am i able to do this ? 


            thanks in advance .

---

### Post by bcschmerker on 2011-08-25
The standard procedure from GNOME Terminal, KDE Konsole, XTerm, KTerm, &c. goes through BASh or equivalent to call APT-Get.  From GMONE Terminal, for example:
```
gksudo -S apt-get update && apt-get upgrade
```

---

### Post by raja.genupula on 2011-08-26
> **bcschmerker said:**
> The standard procedure from GNOME Terminal, KDE Konsole, XTerm, KTerm, &c. goes through BASh or equivalent to call APT-Get.  From GMONE Terminal, for example:
```
gksudo -S apt-get update && apt-get upgrade
```
hey i got this 

```
Fetched 873 kB in 1min 20s (10.9 kB/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by oldos2er on 2011-08-26
You need to use sudo with both commands ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by raja.genupula on 2011-08-26
hi oldos2er
              do you remember , after opening update manager ,we can select what output we want and what we dont want .   
                 so i just wanna do this from terminal . selecting the required from the terminal . 

thanks in advance

---

### Post by raja.genupula on 2011-08-27
can any one give me support on this ?

---

### Post by saltmarshlamb on 2011-08-27
To update a specific package(s) reinstall it(them)

```
sudo apt-get install --reinstall *package1 package2 package3*
```

---

### Post by raja.genupula on 2011-08-30
thank you :S

---

