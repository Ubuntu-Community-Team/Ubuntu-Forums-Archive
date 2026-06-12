---
title: "I want to put Linux Mint 13 on a pendrive using Unetbootin"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by Jon Anderson on 2013-04-05
I'll try this again, I haven't been clear. The only unibooten you can get in Ubuntu12.10 software center is a older Unetbootin 575 and it doesn't suport upgrades past that  575. But to ubgrade to the latest mint13 To put on my thumbdrive  I need Unetbooten 583 , I can't get it through software center or through terminal. Conical doesn't support Unebooten upgrades past just the old 575 But I have downloaded it to downloads but in downloads it is not a executable file. So what do I have to do to make unetbooten 583 that is in my download file executible.

---

### Post by nerdtron on 2013-04-05
I'm sorry, I'm a bit little confused on your situation. If you want the latest unetbootin installer, download it from the website [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Click the Linux installer and it will give you the 583 version of Unetbootin.

After download open the terminal and go to your download folder using the command:
```
cd ~/Downloads
```

Then make the installer executable:
```
chmod +x unetbootin-linux-583 
```

Now you can double click the Unetbootin installer and it will run.

---

