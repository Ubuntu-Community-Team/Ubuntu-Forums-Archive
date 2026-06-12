---
title: "HPLIP and 16.10"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2016-10-24
I don't find the HP print utility HPLIP in the software center.
Is it not available for the new Ubuntu 16.10?
Thanks in advance. Bob.

---

### Post by Geoffrey_Arndt on 2016-10-24
Use Synaptic . . you'll find it there.    The Software Center is limited.

---

### Post by Bucky Ball on 2016-10-25
As above. Use Synaptic. Software Centre has been problematic since 16.04 was released basically. Interesting to note the problem persists perhaps in 16.10.

---

### Post by bob brazie on 2016-10-26
Don't really want to install another utility or application.
Is there somewhere to download the package and then install it?
I have searched using Google and the results are confusing.

---

### Post by foxcbland on 2016-10-26
You can find the site here

[http://hplipopensource.com/](http://hplipopensource.com/)

---

### Post by Geoffrey_Arndt on 2016-10-26
Hmmmm . . . OK

---

### Post by howefield on 2016-10-26
If you are not afraid of the terminal...

```
apt-cache policy hplip
```

will show you the package version and status, then if required

```
sudo apt install hplip
```

will install it.

---

### Post by bob brazie on 2016-10-26
Thanks. I am not afraid of the terminal and ran the commands that you suggested. I copy and pasted to make sure it was correct. It ran through a install and unpack process and landed me back at the start promp.
But I find HPLIP no where. Type hplip in the dash, nothing. Look for it in the software center, nothing. Search my machine looking for HPLIP files/folders and find some in various locations.
Any ideas?

---

### Post by bob brazie on 2016-10-26
Ok I installed synaptic and it showed that the GUI was not installed. So I installed it and can now open it. However everytime I use it I get the error message in this screen shot.
Also when I click on the icon in the upper area it only shows a bland white list with nothing in it to open as with other versions.

---

### Post by Rex Bouwense on 2016-10-27
Just go here [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
and it will work you through the installation.  HP is really Linux friendly when it comes to printers.

---

### Post by bob brazie on 2016-10-30
After installing I also have no options in the drop down icon in the system tray.
It is literally a screen shot as when I tried to take it with in installed screen shot utility the example would not show.

Also there is nothing to click on in the system tray HPLIP icon.

---

### Post by bob brazie on 2016-11-05
I found a newer version that was just uploaded and it is working fine now.

---

