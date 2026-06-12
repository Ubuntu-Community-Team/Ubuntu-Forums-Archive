---
title: "Error while deleting iso file"
date: 2017-02-06
forum: Installation &amp; Upgrades
---

### Post by andy159 on 2017-02-06
Hi all. I'm running Ubuntu 16.04 and had downloaded Linux mint 18.1 to take a look at but for some reason grub could not find the iso file so I gave up and decided to delete it (I was following the instructions to boot from HDD from here [https://community.linuxmint.com/tutorial/view/1849](https://community.linuxmint.com/tutorial/view/1849)). However when I try to delete the file I get an error saying "Error removing file: Permission denied". I don't have a whole lot of free memory on my system so any help getting rid of the 1.8GB iso would be greatly appreciated!

Many thanks,

Andy

---

### Post by howefield on 2017-02-06
According to the tutorial you would have moved the iso file to the /boot folder, That would have required elevated privileges, ie, the use of sudo, you'll need elevated privileges to remove it.

Preceding your command with sudo should do it.

---

### Post by andy159 on 2017-02-06
I'm new to Linux so could you tell me what the command would be? Thanks

---

### Post by howefield on 2017-02-06
> **andy159 said:**
> I'm new to Linux so could you tell me what the command would be? Thanks

Well, according to the tutorial you would use ..

```
sudo mv ~/Downloads/linuxmint-17-mate-dvd-32bit.iso /boot/
```

to move the file to /boot, so you would use

```
sudo mv /boot/linuxmint-17-mate-dvd-32bit.iso ~/Downloads/
```

to move it back to the /home/$USER/Downloads folder.

Of course, you need to substitute "*linuxmint-17-mate-dvd-32bit.iso*" with the actual name of the file you used.

---

### Post by andy159 on 2017-02-06
Embarrassingly simple, many thanks!

---

### Post by howefield on 2017-02-06
Cool, it always is when you know how I guess, feel free to mark the thread as solved. :)

---

