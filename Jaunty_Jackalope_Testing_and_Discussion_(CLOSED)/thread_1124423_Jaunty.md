---
title: "Jaunty"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-04-13
I purchased a new hard drive for my laptop and did a clean install of Jaunty beta (amd64, alternate installer). The install went fine -- better than any Ubuntu installation ever. 

After the install I was greeted by the proprietary driver notifier, and I told it to use the recommended nVidia properitary driver. After that installation succeeded, I restarted. 

Then I used update manager to install the available updates. However, that failed with the following message.

```
E: linux-image-2.6.28-11-generic: subprocess post-installation script returned error exit status 17
E: linux-restricted-modules-2.6.28-11-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
```What should I do?

---

### Post by cariboo on 2009-04-13
Using a more descriptive title would be helpful.

Open and Applcations-->Accessories-->Terminal and type:

```
sudo apt-get -f insall
```

then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The first command should install missing dependencies, then the second command gets for updates and installs them.

Even though it may not have any bearing on your problem, you should always do all the updates, before installing the restricted drivers.

Jim

---

### Post by MountainX on 2009-04-13
> **cariboo907 said:**
> 
Open and Applcations-->Accessories-->Terminal and type:
```
sudo apt-get -f install
```then
```
sudo apt-get update && sudo apt-get dist-upgrade
```The first command should install missing dependencies, then the second command gets the updates and installs them.

Jim

Thank you! I appreciate that tip. :)

> **cariboo907 said:**
> 
Even though it may not have any bearing on your problem, you should always do all the updates, before installing the restricted drivers.
Jim
This seems strange to me because updates will never stop coming. For example, there will be new ones next week, yet I will have already installed the restricted drivers by then even if I follow the above advice. 

> **cariboo907 said:**
> Using a more descriptive title would be helpful.
The title problem seems to be a limitation of vbulletin afaik. As you may see, the title on my OP was previously edited to "**Jaunty linux-image-2.6.28-11-generic post-installation error"**

---

