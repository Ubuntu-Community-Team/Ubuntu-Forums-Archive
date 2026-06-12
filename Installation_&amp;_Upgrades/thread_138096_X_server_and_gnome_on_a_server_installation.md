---
title: "X server and gnome on a server installation"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by peppermint on 2006-03-01
Ive recently setup an old computer to serve web pages. Now I want to install samba so I can put files onto the computer without being sat in front of it. Looking at [this guide](https://wiki.ubuntu.com/SettingUpSamba), I will need a GUI for setting up samba. So how do I install Xserver and gnome, and still have the computer boot to the command line?

---

### Post by ranf on 2006-03-01
I just looked at this guide and only saw one picture that shows the network card. Does that make you believe you need a GUI? I don't think so.

If you need your IP type:
ifconfig

---

### Post by peppermint on 2006-03-01
I dont need to know my IP address, all I need is a place to enter these details
```

    Windows Networking
      Tick Enable windows networking
      Description:       <whateveryouwant>
      Domain/Workgroup:  <yourdomainorworkgroup>

```

---

### Post by ranf on 2006-03-01
C&p from this guide:

You may also edit the file "/etc/samba/smb.conf" manually, and then use "/etc/init.d/samba" to stop and start the service again.

It really isn't complicated.

---

### Post by peppermint on 2006-03-01
Eye, I saw that after I posted. Thanks anyway.

---

