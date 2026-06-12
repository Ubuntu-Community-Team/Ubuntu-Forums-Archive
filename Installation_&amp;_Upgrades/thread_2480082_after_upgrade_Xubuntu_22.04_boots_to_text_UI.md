---
title: "after upgrade Xubuntu 22.04 boots to text UI"
date: 2022-10-18
forum: Installation &amp; Upgrades
---

### Post by Sonador on 2022-10-18
Hello,

- after upgrade from Xubuntu 20.04 LTS to **22.04 LTS** the system **boots to text user interface**/terminal
- in the text UI i login and then type **startx **to run GUI
- then I can use Xubuntu without problems

```
lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35)
```

I searched the internet, somebody had same issue, but he gave up and made fresh install.

---

### Post by &amp;KyT$0P# on 2022-10-18
Please post the output from running the following commands in Terminal -
```
systemctl status lightdm
systemctl status graphical.target
```

---

### Post by Sonador on 2022-10-18
So the outputs are (and it is the same both before and after running startx):

systemctl status lightdm
```
&#9675; lightdm.service - Light Display Manager
     Loaded: loaded (/lib/systemd/system/lightdm.service; static)
     Active: inactive (dead)
       Docs: man:lightdm(1)
```

systemctl status graphical.target
```
&#9679; graphical.target - Graphical Interface
     Loaded: loaded (/lib/systemd/system/graphical.target; static)
     Active: active since Tue 2022-10-18 18:26:25 CEST; 54s ago
       Docs: man:systemd.special(7)

&#345;íj 18 18:26:25 computer_name systemd[1]: Reached target Graphical Interface.
```

---

### Post by &amp;KyT$0P# on 2022-10-18
Any difference if you run
```
sudo dpkg-reconfigure lightdm
```

---

### Post by Sonador on 2022-10-18
> **halogen2 said:**
> Any difference if you run
```
sudo dpkg-reconfigure lightdm
```

A big difference ):P Now it boots into GUI as it should, thank You a lot!

EDIT: Probably as a consequence, a login screen after suspend didn't work. I found out that removing **light-locker** package, which is probably a relict from previous LTS versions, will correct it.

---

