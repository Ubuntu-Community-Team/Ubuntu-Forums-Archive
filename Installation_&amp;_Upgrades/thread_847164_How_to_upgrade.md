---
title: "How to upgrade?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-07-02
I've installed Filezilla an FTP client via add/remove applications. Currently there's an upgrade available and it says to use package manager to upgrade, however, when I go to Synaptic Package manager and right click on Filezilla's line the option for Upgrade is grayed out. 

Am I doing something wrong? Do I need to uninstall and re-install it?

Thanks.

---

### Post by Pumalite on 2008-07-02
You have to remove all third parties from your /etc/apt/sources.list
Including the Medibuntu folder if you have it. Lastly, make sure your OS is fully updated before upgrade. I'd prefer a clean install.

---

### Post by damis648 on 2008-07-02
> **Pumalite said:**
> You have to remove all third parties from your /etc/apt/sources.list
Including the Medibuntu folder if you have it. Lastly, make sure your OS is fully updated before upgrade. I'd prefer a clean install.

No, he is referring to updating FileZilla.

To do this, click the update icon in the notification bar. This is in the upper right hand corner.

---

### Post by avtolle on 2008-07-02
If it is grayed out, then there is a reason that the update cannot be safely installed at the moment. Usually, this happens when there are updated dependencies needed, but the dependencies are not yet ready. Wait for a while, then check again.

---

