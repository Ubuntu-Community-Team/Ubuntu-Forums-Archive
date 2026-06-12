---
title: "Network settings -- Windows configuration missing"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by agiledata on 2005-05-21
I've just installed Ubuntu Hoary, and I'm trying to set up samba, to allow me to share files and a printer on a Windows XP machine. I'm following instructions at:

    [http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)

samba has been successfully installed, with
    sudo apt-get update 
    sudo apt-get install samba

Then the instructions take me to System --> Administration --> Networking --> General, to fill in settings.

Host Settings
      Hostname:       <yourcomputer>
      Domain name:    <yourdomain>

Windows Networking
      Tick Enable windows networking
      Description:       <whateveryouwant>
      Domain/Workgroup:  <yourdomainorworkgroup>

But my "network settings" window, "general" tab has a big space under Host Settings with nothing about Windows in it. I'm stuck. Please tell me what step I have missed out.

Rob

---

### Post by stevenyu on 2005-05-21
System -> Administration -> Shared Folders :razz:

---

