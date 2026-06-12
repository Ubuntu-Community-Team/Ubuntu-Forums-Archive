---
title: "&quot;Recent&quot; folder under My Computer"
date: 2022-06-13
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-06-13
Ubuntu 22.04 has started putting a "Recent" folder under My Computer.  How do I get rid of it.  How do I keep it from reappearing once I get rid of it?

Thank you,

John

---

### Post by web-user on 2022-06-18
It should be a feature of the file manager not the system itself. Look through the settings of Nautilus / whatever FM you use

---

### Post by mIk3_08 on 2022-06-18
> **cigtoxdoc said:**
> Ubuntu 22.04 has started putting a "Recent" folder under My Computer.  How do I get rid of it.  How do I keep it from reappearing once I get rid of it?
Thank you,
John
Please run the command below in your terminal and paste the result here in thread wrap with code. To run the terminal in your system just press the ctrl and alt + t inside to your desktop or just find it to your installed applications in your Linux Ubuntu System. Regards and cheers.
```
hostnamectl status
```

---

### Post by cigtoxdoc on 2022-06-18
Reply to web-user: there is nothing in Nemo properties that would indicate choice of displaying "Recent" or not.

Reply to mik3_08: the output you requested is shown below.

hostnamectl status
 Static hostname: john-Vostro-3500
       Icon name: computer-laptop
         Chassis: laptop
      Machine ID: c6433a6ade3741a7a9bfab0150d88303
         Boot ID: 0a42cf8356bf43cfa39aece65d81a149
Operating System: Ubuntu 22.04 LTS                
          Kernel: Linux 5.15.0-39-generic
    Architecture: x86-64
 Hardware Vendor: Dell Inc.
  Hardware Model: Vostro 3500

Thank you both for replying to my post.

---

### Post by #&amp;thj^% on 2022-06-18
> **cigtoxdoc said:**
> Ubuntu 22.04 has started putting a "Recent" folder under My Computer.  How do I get rid of it.  How do I keep it from reappearing once I get rid of it?

Thank you,

John

Are you sure it was not something that was recently downloaded?
To disable what I've mentioned go to>>>Settings > Security & Privacy > Files & Applications and check to "off"
Or just use:
```
gsettings set org.gnome.desktop.privacy remember-recent-files false
```

---

### Post by deadflowr on 2022-06-18
> **1fallen said:**
> Are you sure it was not something that was recently downloaded?
To disable what I've mentioned go to>>>Settings > Security & Privacy > Files & Applications and check to "off"
Or just use:
```
gsettings set org.gnome.desktop.privacy remember-recent-files false
```

If nemo you need to change it from org.gnome.blahblah to org.cinnamon.blahblah
```
gsettings set org.cinnamon.desktop.privacy remember-recent-files false
```

---

### Post by cigtoxdoc on 2022-06-18
Thank you very much for your suggestions. "gsettings set org.cinnamon.desktop.privacy remember-recent-files false" did the job.

---

### Post by #&amp;thj^% on 2022-06-18
> **deadflowr said:**
> If nemo you need to change it from org.gnome.blahblah to org.cinnamon.blahblah
```
gsettings set org.cinnamon.desktop.privacy remember-recent-files false
```

Good catch deadflowr, I missed the comment>>"Reply to web-user: there is nothing in **_Nemo _**properties that would indicate choice of displaying "Recent" or not."
Thought OP was on Gnome and not cinnamon flavored....:D

---

