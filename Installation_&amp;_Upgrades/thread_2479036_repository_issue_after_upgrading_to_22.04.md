---
title: "repository issue after upgrading to 22.04"
date: 2022-09-12
forum: Installation &amp; Upgrades
---

### Post by bigmrbill on 2022-09-12
I have a Lenovo Thinkpad P17 Gen 1 that I upgraded recently from 20.04 to 22.04. I am now getting the following feed back when I execute a ' apt update '. I appreciate any suggestions to resolve this. Thank you very much.

```
[COLOR=#000000]Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease[/COLOR]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease        
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease   [COLOR=#B26818] [/COLOR][COLOR=#000000] [/COLOR]
Hit:5 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease[COLOR=#B26818]         [/COLOR][COLOR=#000000] [/COLOR]
Hit:6 [http://lenovo.archive.canonical.com](http://lenovo.archive.canonical.com) jammy InRelease
Reading package lists... Done[COLOR=#B26818]                  [/COLOR][COLOR=#000000] [/COLOR]
Building dependency tree... Done
Reading state information... Done
33 packages can be upgraded. Run 'apt list --upgradable' to see them.
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/binary-amd64/Packages' as repository 'http://lenovo.archive.canonical.com jammy In[/COLOR]
Release' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/binary-i386/Packages' as repository 'http://lenovo.archive.canonical.com jammy InR[/COLOR]
elease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/i18n/Translation-en_US' as repository 'http://lenovo.archive.canonical.com jammy I[/COLOR]
nRelease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/i18n/Translation-en' as repository 'http://lenovo.archive.canonical.com jammy InRe[/COLOR]
lease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/dep11/Components-amd64.yml' as repository 'http://lenovo.archive.canonical.com jam[/COLOR]
my InRelease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/dep11/icons-48x48.tar' as repository 'http://lenovo.archive.canonical.com jammy In[/COLOR]
Release' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/dep11/icons-64x64.tar' as repository 'http://lenovo.archive.canonical.com jammy In[/COLOR]
Release' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/dep11/icons-64x64@2.tar' as repository 'http://lenovo.archive.canonical.com jammy [/COLOR]
InRelease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/dep11/icons-128x128.tar' as repository 'http://lenovo.archive.canonical.com jammy [/COLOR]
InRelease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)
[COLOR=#FFFF54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'sutton.simon/cnf/Commands-amd64' as repository 'http://lenovo.archive.canonical.com jammy InRel[/COLOR]
ease' doesn't have the component 'sutton.simon' (component misspelt in sources.list?)


```

---

### Post by deadflowr on 2022-09-12
Might help: [https://askubuntu.com/questions/1426833/lenovo-repository-for-ubuntu-22-04]("https://askubuntu.com/questions/1426833/lenovo-repository-for-ubuntu-22-04")

---

