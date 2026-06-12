---
title: "Update Manager fails"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-12-06
I have 41 updates. Only some of them are failing.

When it does fail, here's the actual error...

```
Failed to download package files
Check your internet connection.
Details
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
```

---

### Post by fantab on 2011-12-06
> **kakashi_12 said:**
> I have 41 updates. Only some of them are failing.

When it does fail, here's the actual error...

```
Failed to download package files
Check your internet connection.
Details
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.0-8ubuntu4_i386.deb 404  Not Found [IP: 91.189.92.177 80]
```

Try another Server for your downloads from Synaptic- Settings- Repositories.

---

### Post by kakashi_12 on 2011-12-14
From there I chose the "Select Best Server" option.
Now it's telling me I have 142 new updates available.
Seems to be going through okay so far though.

---

### Post by bluexrider on 2011-12-14
> **kakashi_12 said:**
> From there I chose the "Select Best Server" option.
Now it's telling me I have 142 new updates available.
Seems to be going through okay so far though.

seems like, once in a while anyway, just changing the server becomes faster too

---

### Post by kakashi_12 on 2011-12-14
Okay. They all installed except for one.
Thanks for your help.
 
The one is a Grub Customizer update and it says it is from an untrusted source or something. It does not give the option to go ahead and do it anyway. It only has a cancel button.

---

### Post by oldos2er on 2011-12-14
Sounds as though you don't have the gpg key for the grub customizer PPA installed. It's here: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA8AA1FAA3F055C03](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA8AA1FAA3F055C03)

Save the text including the begin and end bits to a file in your home folder, give it a name (I used grub.customizer.ppa.gpg.key), run ```
sudo apt-key add grub.customizer.ppa.gpg.key
``` then ```
sudo apt-get update
```

---

### Post by kakashi_12 on 2011-12-18
Thanks. I am up to date.

---

