---
title: "Lost Upgrade to 12.04.01 prompt in Upgrade Manager"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by AbNormCler on 2012-12-01
Hello,

  I have a laptop, and have been using 64-bit Ubuntu, version 10.04.01 LTS for a bit over a year. Some months ago, I began seeing on my Update Manager that I could upgrade to 12.04.01 LTS, and provided me with a button to push to do so. (My setting in the Upgrade Manager is configured to display LTS upgrades.)

  I did not upgrade, and, after several months, this prompt disappeared from the Upgrade Manager. Does anyone know why? I would now like to upgrade. How can I restore the prompt?

Norm

---

### Post by ranger1021994 on 2012-12-01
Open terminal and type :
```
update-manager -d
```

---

### Post by AbNormCler on 2012-12-01
Thanks for your help.

Norm

---

### Post by zvacet on 2012-12-02
You can also use synaptic for updating system.Igf you don´t have it installed 

```
sudo apt-get install synaptic
```

Open synaptic and click on** reload** and after that **mark all updates**.Quick and easy way! ;)

---

### Post by AbNormCler on 2012-12-02
Many thanks to both of you. I'm up and running 12.04. Looks good.

Norm

---

