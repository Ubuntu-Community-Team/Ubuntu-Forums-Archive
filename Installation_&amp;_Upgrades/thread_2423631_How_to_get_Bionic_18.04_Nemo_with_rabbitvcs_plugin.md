---
title: "How to get Bionic 18.04 Nemo with rabbitvcs plugin working?"
date: 2019-07-26
forum: Installation &amp; Upgrades
---

### Post by catman2 on 2019-07-26
I had used Xubnuntu 16.04 with the nemo3 PPA from webupd8team. It was the only way I found to get the rabbitvcs plugin for nemo working. With that tool I have a 1:1 look and feel of SVN between Windows (Tortoise) and Linux.

     Now I found that the PPA webupd8team did not supply a Bionic version. Although 18.04 repos already have Nemo3 and even a few plugins such as nemo-fileroller it does not provide the rabbitvcs plugin.  I found another PPA  "embrosyn/cinnamon" that had all of the plugins. It installed fine except the "nemo-rabbitvcs". This showed an unresolvable unment dependeny with another package in the same PPA named "rabbitvcs-nemo".  I tried the usual steps with purging, removing held packages with aptitude. Even aptitude could not resolve the error. I could install the rabbitvcs-nemo from that PPA, but it would not acutally do anything nor add any plugin that I could find.      

Did someone else find a way (maybe different PPA)  to get the rabbitvcs plugin for nemo running in Ubuntu ?

---

### Post by Frogs Hair on 2019-07-27
The plugin may require dependencies from the Cinnamon desktop environment. Nemo is now default on U-Budgie 19.04 + though the plugin is not included in the repository.

---

### Post by catman2 on 2019-07-27
> **Frogs Hair said:**
> The plugin may require dependencies from the  Cinnamon desktop environment. 
The PPA  "embrosyn/cinnamon" does have some cinnamon stuff as well. Do you think I have to install the full cinnamon desktop to get this plugin installable for xfce?

> **Frogs Hair said:**
> Nemo is now default on U-Budgie 19.04 +  though the plugin is not included in the repository.
In the 18.04 bionic repository the additional plugins have been added compared to 16.04. Unfortunately not the nemo-rabbitvcs.


**Edit**: I tried to install the cinnamon desktop to resolve the problem. I still could not add the nemo-rabbitvcs. 
I get the same error

  ```
sudo apt install nemo-rabbitvcs
  ... 
  The following packages have unment dependencies: 
  nemo-rabbitvcs: Depends: rabbitvcs-nemo but it is not going to be installed
```

---

### Post by Frogs Hair on 2019-07-27
> **catman2 said:**
> The PPA  "embrosyn/cinnamon" does have some cinnamon stuff as well. Do you think I have to install the full cinnamon desktop to get this plugin installable for xfce?


In the 18.04 bionic repository the additional plugins have been added compared to 16.04. Unfortunately not the nemo-rabbitvcs.

I find instructions for enabling the plugin in distributions that use Cinnamon as the default desktop. Linked is a Nautilus instruction.

[https://askubuntu.com/questions/1062947/rabbit-vcs-on-ubuntu-18-04-not-showing-menu-in-nautilus](https://askubuntu.com/questions/1062947/rabbit-vcs-on-ubuntu-18-04-not-showing-menu-in-nautilus)

---

### Post by catman2 on 2019-07-27
> **Frogs Hair said:**
> I find instructions for enabling the plugin in distributions that use Cinnamon as the default desktop. Linked is a Nautilus instruction.
[https://askubuntu.com/questions/1062947/rabbit-vcs-on-ubuntu-18-04-not-showing-menu-in-nautilus](https://askubuntu.com/questions/1062947/rabbit-vcs-on-ubuntu-18-04-not-showing-menu-in-nautilus)

Thanks for finding that for me. However, I think the version between nautilus and nemo are not the same. However I did find a solution. 

The thing is a bit tricky because there is Python involved which is incompatibe betweeen Python3 and Python2.7. Nemo switched to Pyhon3 in Version 4. So all extensions and all dependencies require Pyhon3 support. The installation for Python3 is very different and at the time of writing there is no PPA that includes all required parts. This is transisiton time. Expect confusion for a couple of month a few years..

Ubuntu pulls their files from a mint repro. Due to the transition they dropped the rabbitvcs extension. The rabbitvcs nemo extension is actually coded by the rabbitvcs people. The extension itself is a single python file and its easy to install (just copy to a sytem directory). The problem is getting the dependencies installed. For Nemo4 with python3 dependencies see the description here: [https://github.com/rabbitvcs/rabbitvcs/issues/251](https://github.com/rabbitvcs/rabbitvcs/issues/251)  (at the end)

Here is a way to get things running with Python2.7. We only use standard Ubuntu repository stuff, except the Extension python file. This will install nemo 3.65

Then the steps are
```

 run sudo apt update
 sudo apt install nemo nemo-data nemo-python.
 sudo apt install rabbitvcs-core

```
Download the from the github project rabbitvcs/rabbitvcs under Releases the whole zip file for 16.01 (see here [https://github.com/rabbitvcs/rabbitvcs/releases](https://github.com/rabbitvcs/rabbitvcs/releases) )
We only need the file "RabbitVCS.py" from the folder clients/nemo/. Copy this to /usr/share/nemo-python/extensions and set file permissions the chmod 644.
If the file is in you home directory the code is```

[CODE]
sudo cp RabbitVCS.py/usr/share/nemo-python/extensions
sudo chmod 644 /usr/share/nemo-python/extensions/RabbitVCS.py

```
Finally register this with nemo. 
```

nemo -q
pgrep -f services.py | xargs kill
nohup nemo > /dev/null &

```
If you get an error with the 'nemo- q' command close all nemo windows and try again. If you get an error on the 'kill' line ignore it but be sure re-logon after the last command.

You shoud re-logon. Then it should work. Open the preferences and see the RabbitVCS plugin listed. On the context menu you should see an SVN or Git or Mercurial entry. And on checked out code you should see (tiny) overlay icons.

If someone knows how to get the icons larger, please post this here.


EDIT: Updated procedure

---

