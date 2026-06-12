---
title: "How to Uninstall application which are not directly installed from UBUNTU SOFTWARE?"
date: 2021-06-06
forum: Installation &amp; Upgrades
---

### Post by joydipto on 2021-06-06
I have installed **Opera** by downloading an installation package from **Firefox** from the official website of Opera. Now I want to uninstall it. I am not getting **Opera** listed under the **INSTALLED** tab in Ubuntu Software. So how do I uninstall **Opera **now?

---

### Post by grahammechanical on 2021-06-06
It should still be possible to find the Opera application in Ubuntu Software and click the Remove/Uninstall button. If not try

```
sudo apt remove package_name
```

To remove configuration files as well

```
sudo apt purge package_name
```

Regards

---

### Post by ActionParsnip on 2021-06-06
If you run
```

dpkg -l | grep -i opera

```
You can see the opera package name. As long as you install packages using deb files then it will be able to uninstall using the usual commands. It doesn't matter if its from the software center or otherwise. A deb is a deb

---

### Post by grahammechanical on 2021-06-06
> As long as you install packages using deb files

Now, there is a thought. What if it is a snap packaged version of Opera?

[https://snapcraft.io/opera](https://snapcraft.io/opera)

That page has an Install button. I wonder if it gives a Remove button if Opera snap is installed. To find out which snaps are installed 

```
snap list
```

to remove a snap

```
snap remove appname
```

[https://www.omgubuntu.co.uk/2016/12/simple-guide-snapd-commands](https://www.omgubuntu.co.uk/2016/12/simple-guide-snapd-commands)

Regards

---

### Post by joydipto on 2021-06-07
Thnx mission successful

---

