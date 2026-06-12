---
title: "Installing ubuntu / Kubuntu from iso without cd"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Fintan on 2008-03-02
Hi there,
just out of curiousity is there a way of installing *ubuntu directly from the downloaded .iso instead of buring a cd?

Lets say from the grub boot or a live cd?

Thank you for any ideas:)

---

### Post by roaldz on 2008-03-02
Maybe Wubi, but I must warn you: It´s going to be slow, becouse Wubi installs ubuntu from the ¨alternative iso¨, and it creates a virtual hard disk in a file to install it to. Then grub will tell ubuntu that that file is its root partition. Be sure to defrag your disk when you´re going to use wubi.

Roald

---

### Post by Fintan on 2008-03-02
Thankx roaldz,
Wubi is not an option unless I can use it from a vm guest xp. Besides I didn't here to many good things about installing from wubi, updates/-grades etc.

---

