---
title: "Upgraded to 3.6.2pre"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by brvaland on 2010-03-07
Hi Experts

I have recently upgraded to Firefox 3.6.2pre, I would like to downgrade to a stable version Firefox 3.5.

Can someone guide me how can I achieve the above?

Kind Regards
Bhavesh

---

### Post by tom4everitt on 2010-03-07
It depends on how you installed it. If you added a repo to install it, you should do:

1. sudo apt-get remove firefox
2. Remove the repo you added to install firefox 3.6.2 (System->Administration->Software Sources)
3. sudo apt-get update
4. sudo apt-get install firefox

---

### Post by brvaland on 2010-03-07
Thanks for your email.

I have managed to remove Firefox 3.6.2pre and reverted to 3.5.8. Also, I would like to know if I can install a stable version of Firefox 3.6 and how?

As I am newbie to Linux, on Windows there is a option of under Help > check for updates.

This is not found on Linux, is this something dropped by firefox on linux version or I need to activate this option through changing some configuration setting.

Please advise?

Kind Regards
Bhavesh

---

### Post by tom4everitt on 2010-03-07
The reason for this is that its ubuntu (canonical) thats providing your firefox package (not mozilla directly). This enables ubuntu to have one central updater that checks every once in a while that everything is up to date.


The easiest way to get the latest firefox is to download it from firefox.com. You will get a compressed folder. Unpack it somewhere, and launch firefox by double clicking on a file named firefox in that folder. You can then create a link on your desktop or something to that file...



Also if you want a more "proper" way to install it, you can google for

install firefox 3.6 ubuntu

and you will find a lot of guides. Its a matter of taste which you prefer I guess. But the above one should work fine.

---

### Post by wojox on 2010-03-07
Look here: [http://wojox.homelinux.net/?p=67](http://wojox.homelinux.net/?p=67)

---

### Post by brvaland on 2010-03-07
Thanks 

I have managed to install firefox using the information found on the below link.

[http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/](http://digitizor.com/2010/01/22/how-to-install-firefox-3-6-in-ubuntu-9-10/)

Kind Regards
Bhavesh

---

### Post by brvaland on 2010-03-08
It did work for a while as I used "Manual Install".

This morning, when I click on check update it reverted to Firefox 3.5.8. I realised that it was available on repository.

I uninstall firefox through repository and found it was removed sucessfully as the shortcut is not available under application > Internet.

Then followed the manual install again but no luck it did not give me a shortcut to launch.

Please advise?

Kind Regards
Bhavesh

---

### Post by wojox on 2010-03-08
Just run this:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get install firefox-3.6
```

Then ```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by brvaland on 2010-03-09
Thanks for your response.

It works fine.

The only problem i have noticed is that adobe flash player is not working. I have tried to reinstall the software but no luck.

Any suggestions will be highly appreciated.

Kind Regards
Bhavesh

---

### Post by tom4everitt on 2010-03-11
Did you install it with:

```

sudo apt-get install flashplugin-nonfree

```

---

### Post by brvaland on 2010-03-12
Thanks for you reply.

Yes, I did try to install through that code but I receive message as it is already installed.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please advise?

Kind Regards
Bhavesh

---

### Post by brvaland on 2010-03-12
I have managed to resolve the adobe flash issue by following below link reference to removeing conflicting plugins.

[http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2)

Thanks for your help.

Kind Regards
Bhavesh

---

