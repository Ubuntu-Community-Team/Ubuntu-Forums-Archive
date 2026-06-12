---
title: "Libre crashes after installing Ubuntu 11.4"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Dada Maheshvarananda on 2011-05-02
After 11.4 update, Libre 3.3 crashes upon opening every time.

---

### Post by rejinarudo on 2011-05-02
You may try removing it and try reinstalling again.
I'm not sure, but I think it is some sort of conflict between the "libreoffice" package of the previous version and the "libreoffice" of 11.04.

---

### Post by Dada Maheshvarananda on 2011-05-02
> **rejinarudo said:**
> You may try removing it and try reinstalling again.
I'm not sure, but I think it is some sort of conflict between the "libreoffice" package of the previous version and the "libreoffice" of 11.04.

Yes, I was using Open Office previously. Can you please explain how to remove and reinstall Libre Office?

---

### Post by Dada Maheshvarananda on 2011-05-02
Using Ubuntu Software Center, I removed and reinstalled Libre Office Suite. Same problem persists. When I open a Word or open office document, the system closes after 1 second.

I wonder if the System Log Viewer has anything that would show the problem? (I don't know which System log would be appropriate.)

---

### Post by rejinarudo on 2011-05-02
> **Dada Maheshvarananda said:**
> Yes, I was using Open Office previously. Can you please explain how to remove and reinstall Libre Office?

Thanks for asking.

Try doing this.

Remove Libreoffice through terminal:
```
sudo apt-get purge libreoffice libreoffice-gnome
```

Or try it removing through synaptic package manager.

Installing Libreoffice:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && apt-get install libreoffice libreoffice-gnome
```

---

### Post by Dada Maheshvarananda on 2011-05-02
> **rejinarudo said:**
> Thanks for asking.

Try doing this.

Remove Libreoffice through terminal:
```
sudo apt-get purge libreoffice libreoffice-gnome
```

Or try it removing through synaptic package manager.

Installing Libreoffice:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update && apt-get install libreoffice libreoffice-gnome
```

Did remove and reinstall commands through terminal. At end, got this:

Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

?

---

### Post by rejinarudo on 2011-05-02
> **Dada Maheshvarananda said:**
> 
```
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```


I think you are not root. Try ```
sudo su
```
You might want to run ```
apt-get update
```

---

### Post by Dada Maheshvarananda on 2011-05-02
Thanks. Followed all instructions and repeated the process. Only LibreOffice Writer closes each time. If I have LibreOffice Calc open, for example, the moment I open a Writer doc, the entire suite will close. Any other suggestions?

---

### Post by Dada Maheshvarananda on 2011-05-03
> **Dada Maheshvarananda said:**
> Thanks. Followed all instructions and repeated the process. Only LibreOffice Writer closes each time. If I have LibreOffice Calc open, for example, the moment I open a Writer doc, the entire suite will close. Any other suggestions?

I wonder if something in my Log File Viewer would indicate what the problem could be that causes LibreOffice to fail?

---

### Post by Dada Maheshvarananda on 2011-05-03
> **Dada Maheshvarananda said:**
> I wonder if something in my Log File Viewer would indicate what the problem could be that causes LibreOffice to fail?

Help! Please! I'm a writer and I need LibreOffice Writer to function!

---

### Post by Dada Maheshvarananda on 2011-05-05
> **Dada Maheshvarananda said:**
> Help! Please! I'm a writer and I need LibreOffice Writer to function!

Finally solved by doing a clean install and formatting my hard drive.:popcorn:

---

