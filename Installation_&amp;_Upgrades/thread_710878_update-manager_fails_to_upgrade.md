---
title: "update-manager fails to upgrade"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by ligxn on 2008-02-28
I typed sudo update-manager -d to upgrade from 7.10 to 8.04. When the manager gets all new packages and begins to install, it tells me that /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb is in not working state, so the update-manager cannot be installed. when i typed sudo apt-get dist-upgrade in the terminal, the following messages comes out:

The following packages will be upgraded:
  update-manager
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/895kB of archives.
After this operation, 57.3kB of additional disk space will be used.
(Reading database ... 123458 files and directories currently installed.)
Preparing to replace update-manager 1:0.81.2 (using .../update-manager_1%3a0.87.9_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1674, in <module>
    main()
  File "/usr/bin/pycentral", line 1668, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1169, in run
    pkg.prepare(used_runtimes, old_used_runtimes, old_pkg)
  File "/usr/bin/pycentral", line 803, in prepare
    rt.remove_byte_code(removed_fs)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot keep updating, neither can I install any deb.

---

### Post by zvacet on 2008-02-29
```
sudo dpkg --configure -a
```

or 

```
sudo apt-get -f install
```

---

### Post by keykero on 2008-02-29
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

or 

```
sudo apt-get -f install
```

This just repeats the error.

---

### Post by keykero on 2008-02-29
This one worked for me:

[http://ubuntuforums.org/showthread.php?t=710271&highlight=pycentral](http://ubuntuforums.org/showthread.php?t=710271&highlight=pycentral)

Didn't work from the command line but worked that way.

---

### Post by ligxn on 2008-02-29
I have found a resolution.
First, I type
```
 sudo dpkg --configure -a
```
After that, in the Synaptic, I find that the version of update-manage-core is 0.81 or so and it is marked red, which means that it is broken. I click it and choose *mark for complete removal*. Restart. When the login interface comes out, I press ctrl+alt+F2, so I go into tty2. I change to ~/Public, where I downloaded an update-manager-core_0.87.9_i386.deb. I type sudo dpkg -i update*. There comes no error. Then I return to login interface, type my username and password. Then I enter the GUI. I try to install some packages. It is alright now!

---

### Post by allquixotic on 2008-02-29
Simpler still:

```

 sudo dpkg --configure -a
 sudo dpkg -P --force-all update-manager update-manager-core
 sudo aptitude update
 sudo aptitude install update-manager update-manager-core

```

works for me. no reboot required.

Thanks,

Sean

---

### Post by cdsboy on 2008-02-29
> **allquixotic said:**
> Simpler still:

```

 sudo dpkg --configure -a
 sudo dpkg -P --force-all update-manager update-manager-core
 sudo aptitude update
 sudo aptitude install update-manager update-manager-core

```

works for me. no reboot required.

Thanks,

Sean

Thanks worked for me!

---

### Post by TheIdiot on 2008-02-29
> **allquixotic said:**
> Simpler still:

```

 sudo dpkg --configure -a
 sudo dpkg -P --force-all update-manager update-manager-core
 sudo aptitude update
 sudo aptitude install update-manager update-manager-core

```

works for me. no reboot required.

Thanks,

Sean

Thanks. This also worked for me

---

### Post by Game_boy on 2008-03-01
Worked for me. Thanks.

---

