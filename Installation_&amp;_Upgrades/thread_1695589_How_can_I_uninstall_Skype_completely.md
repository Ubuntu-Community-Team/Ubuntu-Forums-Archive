---
title: "How can I uninstall Skype completely?"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by JosephWheatley on 2011-02-26
I have uninstalled and reinstalled ***Skype 2.1 Beta 2 for Linux[SIZE=1][COLOR=#000000][FONT=Times New Roman][FONT=Helvetica][/FONT][/FONT][/COLOR][/SIZE]*** several times using the Ubuntu Software Centre and the Synaptics Package Manager for a complete removal.

My problem is that *** Skype*** still knows my log-in details when I start the newly reinstalled ***Skype*** so I know it has not been a complete uninstallation.

I want all these details to be deleted. I have had issues with ***Skype*** not ringing on calls and the instant messaging being disorderly so I want it all **CLEANLY** installed.

---

### Post by sffvba[e0rt on 2011-02-26
Hi,

Most application will store info in hidden files in your home folder ~/ ... Enable hidden files to be viewable and look for a folder like .Skype or something similar after you have removed the software... delete this folder and try again...

Please note that I don't know if this will work and I don't use Skype... but it is worth a shot ):P



404

---

### Post by squenson on 2011-02-26
Here is a [link]("https://support.skype.com/en-us/faq/FA142/How-do-I-delete-my-profile-or-Skype-Name?frompage=search&q=delete+account&fromSearchFirstPage=false") from Skype web site that explains how to proceed.

---

### Post by runeh76 on 2011-02-26
```
sudo apt-get autoremove --purge skype
```

---

### Post by ajgreeny on 2011-02-26
You still need to remove or rename the hidden ~/.Skype folder in your home as that is where everything related to your skype subscription is stored locally on your computer.
```
mv .Skype .Skype.bak
``` will do it for you but leave all the old data available if you should need it in .Skype.bak.

---

