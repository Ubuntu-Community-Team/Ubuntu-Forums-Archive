---
title: "Add/Remove Applications Error"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by daxm on 2007-10-21
Starting yesterday I have been receiving this error after the add/remove applications program is done downloading and installing my newly requested programs.

<snip>
E: timidity: subprocess post-installation script returned error exit status 1
E: exult: dependency problems - leaving unconfigured
</snip>

Any ideas on what this is and how to solve it?  :confused:

---

### Post by Takuhari on 2008-01-11
I second this... i want to get rid of it^^*
I am running the 7.10 version.
Any suggestions?:confused:

It happens when i install

---

### Post by zvacet on 2008-01-11
system<administration>software sources>chek all under Ubuntu software and under update tab.Reload.Now,when you have all repos open you should be able to install whatever you want from repos.If you want to remove program

```
sudo apt-get --purge remove >program name>
```

---

