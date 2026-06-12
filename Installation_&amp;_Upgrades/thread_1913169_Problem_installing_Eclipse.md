---
title: "Problem installing Eclipse"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by Danieb309 on 2012-01-22
I installed Eclipse by Ubuntu Software Center and by Synaptic Package Manager. Both times the icon in Applications->Programming->Eclipse is in place but when I click it absolutly nothing happens. I tried several times installing and uninstalling but it´s always the same. I run Ubuntu from VirtualBox.

---

### Post by poolet on 2012-01-22
You can try and used QDevelop.. Also is better download eclipse from official web site.... At the end you must install libraries for your compiler.... 

```
sudo apt-get update
```
```
sudo aptitude install build-essential
```

good luck!!!

---

### Post by Danieb309 on 2012-01-22
I´m going to download the files directly from eclipse site. Where in the file system should I install it (new to Ubuntu/Linux/Unix), is there a usual directory where it should go?

Thanks!

---

### Post by poolet on 2012-01-23
> **Danieb309 said:**
> I´m going to download the files directly from eclipse site. Where in the file system should I install it (new to Ubuntu/Linux/Unix), is there a usual directory where it should go?

Thanks!

Just download from eclpise.org the isn't necessary to install the file you can run the application as you download...

---

### Post by raja.genupula on 2012-01-23
ok try to call eclipse from terminal , and tell us what you got .

---

### Post by Andrew_nuts on 2012-02-21
Me too facing the same problem. thanks for the solution.

**Mark the thread closed**

---

### Post by fballem on 2012-02-21
I have used the following process to install Eclipse from eclipse.org (the eclipse site).

[https://wiki.ubuntu.com/fballem/Software/external/eclipse](https://wiki.ubuntu.com/fballem/Software/external/eclipse)

Please let me know if any of the instructions are not clear. Please note that if you are running ubuntu 11.10, you will need to install gnome-system-tools in order to be able to administer groups in ubuntu. The following command may be used from a terminal:
```

sudo apt-get install gnome-system-tools
```

I hope this helps,

---

