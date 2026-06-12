---
title: "[Solved] ROS (robot operationg system)"
date: 2021-04-02
forum: Installation &amp; Upgrades
---

### Post by bengao51 on 2021-04-02
Hello 
I am trying to install ros, 
but I have had errors that I cannot resolve for several days.
 
Sorry, it's in French but the translation is simple.

Can you help me?

Thanks a lot

Ben

```

sudo apt install ros-noetic-desktop-full

```

```

Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 python3-catkin-pkg : Dépend: python3-catkin-pkg-modules (>= 0.4.23) mais ne sera pas installé
 python3-rospkg : Dépend: python3-rospkg-modules (>= 1.2.10) mais ne sera pas installé
 ros-noetic-desktop-full : Dépend: ros-noetic-desktop mais ne sera pas installé
                           Dépend: ros-noetic-perception mais ne sera pas installé
                           Dépend: ros-noetic-simulators mais ne sera pas installé
                           Dépend: ros-noetic-urdf-sim-tutorial mais ne sera pas installé
E: Dépendances non satisfaites. Essayez « apt --fix-broken install » sans paquet
   (ou indiquez une solution).



```

---

### Post by mikewhatever on 2021-04-02
Looks like you've added a wrong repository to a wrong distro. There is no info about both, so no way to tell if it is right.
Anyway, what can we do for you?

---

### Post by bengao51 on 2021-04-02
I don't know how to solve this problem

So I need help

---

### Post by yetimon_64 on 2021-04-02
Note the line: > Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Or in English:
>  You can run "apt --fix-broken install" to correct these problems.
Have you tried running the next command (copy the line from your output in your language but with "sudo", I'll use English for this site) ...
```
sudo apt --fix-broken install
``` ... yet as suggested in the output ? After running the rest of your output through Google translate I would tend to follow such a suggestion as a first step. Post back here if any further problems/issues show up.

Regards, yeti.

---

### Post by grahammechanical on 2021-04-02
Please open Software & Updates and confirm that the Universe, Restricted & Multiverse repositories are enabled.

[http://wiki.ros.org/Installation/Ubuntu](http://wiki.ros.org/Installation/Ubuntu)

Regards

---

### Post by bengao51 on 2021-04-02
thanks a lot, it's ok.

"apt --fix-broken install" resolt it

---

