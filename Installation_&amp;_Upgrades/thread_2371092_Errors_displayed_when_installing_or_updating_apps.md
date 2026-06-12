---
title: "Errors displayed when installing or updating apps"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2017-09-10
When I install an application (through [FONT=lucida console]apt[/FONT] [FONT=lucida console]install[/FONT] or [FONT=lucida console]dpkg[/FONT] [FONT=lucida console]--install[/FONT]) or run an update ([FONT=lucida console]apt[/FONT] [FONT=lucida console]update[/FONT]), I see the following error in the terminal.
```
I/O warning : failed to load external entity "/usr/share/mime/packages/virtualbox.xml"
Failed to parse '/usr/share/mime/packages/virtualbox.xml'
```
This doesn't seem to cause any problem, and my VirtualBox (installed using the [official VirtualBox PPA]("https://www.virtualbox.org/wiki/Linux_Downloads")) works correctly.

Do you have any idea what this error means, and what, if anything, I should do about it?

I'm running Lubuntu 16.04 64-bit.

---

### Post by SeijiSensei on 2017-09-10
I have a "/usr/share/mime/packages/virtualbox-5.1.xml" on my machine.  Since "virtualbox-5.1" matches the name of the package in the Oracle repos, I'm guessing that file was installed along with VirtualBox.  The Ubuntu version uses the name "virtualbox" for the package.

Now, I've never seen the error you describe, but if you have the same virtualbox-5.1.xml file as I do,  this should get rid of the error:

```

cd /usr/share/mime/packages
sudo ln -s virtualbox-5.1.xml virtualbox.xml

```

---

### Post by Paddy Landau on 2017-09-10
Interesting, thank you, SeijiSensei. In that folder, I have (among other files) the following.
```
-rw-r--r-- 1 root root    2148 2016-08-22 08:00:21 virtualbox-5.1.xml
lrwxrwxrwx 1 root root      30 2017-07-24 13:41:29 virtualbox.xml -> /opt/VirtualBox/virtualbox.xml
```
The folder in [FONT=lucida console]/opt[/FONT] doesn't exist.

So, I removed the invalid link and replaced it using your suggestion, and it seems to have done the trick!

Thank you.

---

