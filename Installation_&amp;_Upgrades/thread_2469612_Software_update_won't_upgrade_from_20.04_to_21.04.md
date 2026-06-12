---
title: "Software update won't upgrade from 20.04 to 21.04"
date: 2021-12-03
forum: Installation &amp; Upgrades
---

### Post by jrcj38 on 2021-12-03
I've seen there's an issue with upgrading to 21.04. Software updater just immediately exits when I click upgrade. I'm assuming the problem still exist, yes? Is there any ETA on it being a safe thing to do? Tnx.

---

### Post by Dennis N on 2021-12-03
> **jrcj38 said:**
> I've seen there's an issue with upgrading to 21.04. Software updater just immediately exits when I click upgrade. I'm assuming the problem still exist, yes? Is there any ETA on it being a safe thing to do? Tnx.
I just checked on my own 20.04 - I don't see that problem. After the "Upgrade" button, the Software Updater window will close, but you should get another window with release notes. If that does not appear, you could try using the alternative "do-release-upgrade" command in the terminal and see if that gets the upgrade going. 
```

sudo do-release-upgrade
```

---

### Post by jrcj38 on 2021-12-06
Tried do-release-upgrade. Response was "Please install all available updates for your release before upgrading." Using apt-get I updated the list then ran the upgrade. Did both twice to make sure. Retried do-release-upgrade and am getting the same response from it. Something isn't right in the installed software database I think. Not sure what.

---

### Post by Impavidus on 2021-12-06
So, when you run sudo apt update, does it tell you that no more upgrades are available? If not, show the complete output of sudo apt upgrade.

---

### Post by rsteinmetz70112 on 2021-12-06
You might want to try "apt full-upgrade"

---

### Post by jrcj38 on 2021-12-06
This may be an issue. The reply to both impavidus and rsteinmetz70112 is as follows;

root@sr01:~# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libodbc1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Impavidus on 2021-12-07
So, one upgrade wasn't installed, either because a dependency is unavailable or it requires removal of a different package. It happens, most commonly because there may be unofficial software sources on your system. Maybe```
sudo apt full-upgrade
```will upgrade that package, but it may have undesired side effects. You can abort if you don't like it. Show us what it intends to do anyway.

If this doesn't fix the issue, can you show```
apt-cache policy libodbc1
```

---

### Post by yancek on 2021-12-07
I don't usually do upgrades but rather new install so I'm not sure about the methods suggested above.  20.04 is an LTS release, 21.4 is not.  You should be able to upgrade from one LTS (20.04) to the next LTS (22.04) but it hasn't been released yet so you need to go from release 20.04 to 20.10 to 21.04 as I understand it.

---

### Post by jrcj38 on 2021-12-07
Success! The item in question,  [COLOR=#000000]libodbc1, was a 32 bit generic database interface. I have a number of 32 bit libraries because I run something with helper apps that are still 32 bit. I couldn't see why the helpers would need a full blown database shim so I deleted it. The upgrade worked and does the program with the 32 bit helpers. In fact I got some functionality back with 21.04 Thank you all for your assistance.[/COLOR]

---

