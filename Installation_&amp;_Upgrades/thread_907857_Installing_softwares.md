---
title: "Installing softwares"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by ranjithnair on 2008-09-01
When I download the packages for ubuntu how would i know the dependencies for that software....for example if i am installing "kubuntu-desktop",how would i know its dependencies....here i am not using synaptic package manager...

---

### Post by Pumalite on 2008-09-01
Stick to Synaptic

---

### Post by iaculallad on 2008-09-01
> **ranjithnair said:**
> When I download the packages for ubuntu how would i know the dependencies for that software....for example if i am installing "kubuntu-desktop",how would i know its dependencies....here i am not using synaptic package manager...

Try this on your terminal if it work:

```
sudo apt-get install apt-rdepends
```

then

```
sudo apt-rdepends kubuntu-desktop
```

---

### Post by aysiu on 2008-09-02
You can find the dependencies here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

It'd take a long time to individual download them all, though.

What's wrong with using Synaptic or *apt-get*?

Do you not have a working internet connection in Ubuntu?

---

### Post by ranjithnair on 2008-09-02
I have a working connection,but my friend doesnt..so i want to give him a few softwares with synaptic it is pretty difficult to give him the packages....

---

### Post by manishtech on 2008-09-02
No need to do all these. First get a software called **Aptoncd** on the computer which has a net connection.

Now goto synaptic and select the software which your friend wants. Now click on "**Apply**", then there a screen comes which confirms the software download and installation. There you would find a check box which says "**Download Package files only**". Select it and then click on **Apply**.

Now after this only the packages are downloaded and not installed. They are downloaded it** /var/apt/cache/archives** .

Now goto **System> Administration> AptOnCD**. Click on Create, it will scan all the packages and create an ISO for it. Burn this ISO in a CD and then take it to his computer and insert it. The CD will be detected to contain an offline repo. Add it to the package manager and then it can be installed from there.

_**Additional Method**_
Or in the other way, just take the ISO which you created to your friend's comp, and the .deb file of AptonCD. Install AptonCD from the deb file, then open this and select Restore, choose the ISO to be restored to /var/apt/cache/archives.
After restoration is complete, goto Synaptic and click on Reload. The packages will be reloaded and you can install from the entry which appears in the list.

---

