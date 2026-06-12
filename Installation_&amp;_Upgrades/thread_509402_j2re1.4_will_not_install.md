---
title: "j2re1.4 will not install"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by gt2nv on 2007-07-25
for some reason my laptop with ubuntu version 7.04 and when i logged on last night the update notification came up and told me to run the update for j2re4.4.  when i tried to do this update it downloaded and then tried to install.   There was a screen that come up and asked me to accept the terms and agreements and as soon as i click the screen to do anything, it grays itself over and then says that it needs to force quit because it is not responding.  Is there any suggestions?

Please help!

Thanks,

Jeremy

---

### Post by Seisen on 2007-07-25
That is the blackdown version is thier a particular reason why you are using that. You can try uninstalling it by putting this in the terminal

```
sudo apt-get remove j2re1.4   
``` then you can install the Sun version by doing this

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by Gremlinzzz on 2007-07-25
When i use 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
it seems to get stuck at agree and no matter how many times i press enter nothing happens.
so what i do is install Sun Java(TM) Runtime Environment (JRE) 6 and its plugin from the synaptic package manager then i put the command to get extra stuff like fronts.
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
the java you use is also in the synaptic package manager.
:guitar:

---

