---
title: "Package refuses to uninstall"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Bob Morane on 2007-02-06
Hello everyone, i have an issue that recently got worse then it was before. I have a rebellious package in my system. The package is k3d, a 3d modeling software for kde i installed one day and never used much.

When i upgraded to edgy, k3d didn't upgrade well, synaptic returned me an error in the post installation script. Since i didn't needed it, i tried uninstalling it. This time synaptic returned me an error in the pre-removal script. I posted in the french forum but nobody was able to help me, then i simply stop worrying about it.

But today, after made an update, k3d appears once again in the update list. What's worse is that if i try to uninstall ANY package, synaptic stops because of the error in k3d's pre-removal script, even thought i don't select k3d itself for uninstall

So, i now have a package i can neither uninstall nor reinstall and it prevents me from uninstalling ANY other package. I hope there is something to do apart from a clean system install.

Oh, i tryed  a " sudo dpkg -P k3d " and got an error too. It's in french so i'll try to translate
"error treating k3d --purge
package is in an incoherent state, you should try to reinstall before trying to remove it
Errors were encountered during the execution : k3d"

The reinstall is not even available because the package is not up-to-date, i can only select uninstall (does not work) or update (does not work either).

Please, help :confused:

---

### Post by Rui Pais on 2007-02-06
hi,
have you tried:
```
sudo aptitude purge k3d
```

aptitude is usually very good dealing with broken packages.

hth.

---

### Post by Bob Morane on 2007-02-06
I get an error too
```
dpkg : erreur de traitement de k3d (--purge) :
 Le paquet est dans un état incohérent - vous devriez
 le réinstaller avant d'essayer de le supprimer.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Des erreurs ont été rencontrées pendant l'exécution :
 k3d
Abandon (core dumped)

```

The french messages are the same i get with dpkg -P.

---

### Post by Rui Pais on 2007-02-06
sorry to hear that...

another two suggestions:
Synaptic sometimes seems to solve some issues with broken packages that apt/aptitude wont.

open synaptic on the buttons on the bottom left choose 'Custom Filters' (don't know how they are named in french...) and in the up section you got a 'Broken' Section. k3d should be there listed... double click on it (or choose complete remove)

Another option is trying the very general 
sudo apt-get install -f
(and cross fingers) to try to fix all...

hope some of this work.

---

### Post by Bob Morane on 2007-02-06
k3d is NOT listed as broken.

I tryed the "fix-all" method, here is the output (*translated from french*)

sudo apt-get install -f
*Reading package list ... done*
*Building dependecy tree*
*Reading state information ... done*
*0 updated, 0 newly installed, 0 to remove and 1 non updated*
*1 partially installed or removed*
*It is necessary to download 0o/10.4Mo in the archives*
*After unpacking, 0o of additional disk space will be used*
*Selecting k3d package that was deselected*
*(reading databse ... 176530 files and directories already installed*
*Preparing to replace k3d 0.5.12.0-1ubuntu2 (with .../k3d_0.5.12.0-1ubuntu2_i386.deb)*
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
*dpkg : warning - old pre-removal script returned an output error code 1*
*dpkg - trying to execute new package script in place*
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
*dpkg : error of treatment of /var/cache/apt/archives/k3d_0.5.12.0-1ubuntu2_i386.deb (--unpack) :*
*the sub-process new pre-removal script returned a state output error code 1*
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
*dpkg error while cleaning*
*the sub-process post-installation script returned a state output error code 1*
*Errors were encountered during execution*
 /var/cache/apt/archives/k3d_0.5.12.0-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

:confused:  ](*,)

---

### Post by Rui Pais on 2007-02-06
uhmm... thats hard. 
i'm afraid it's a little beyond my knoledge :(

maybe try to search around or google for something related (not with k3d but with stale packages)

mean while since it seems that it's not entirely removed nor installed maybe a reinstall of the old package followed by a new retry of remove/update.

you can find old package (assuming it came from dapper) [here]("http://packages.ubuntu.com/dapper/graphics/k3d").

Apart from that, i'm without more ideas...

---

### Post by vikingdocerrado on 2007-02-25
Hi there,

I had the same problem, and after googling around I found the solution/workaround in [http://forums.pcpitstop.com/lofiversion/index.php/t131935.html]("http://forums.pcpitstop.com/lofiversion/index.php/t131935.html").

It goes like this:
```

 sudo kate /var/lib/dpkg/status

```
Find (Ctrl+F) k3d and keep "finding next" (F3) until you find the k3d package.
The last line of package (i.e. after the "Depends", "Suggests", and "Description" fields) is:
```

Python-Versions: current

```
Remove the "s".
Save the file.

Done.

---

### Post by DarkN00b on 2007-03-13
> **vikingdocerrado said:**
> Hi there,

I had the same problem, and after googling around I found the solution/workaround in [http://forums.pcpitstop.com/lofiversion/index.php/t131935.html]("http://forums.pcpitstop.com/lofiversion/index.php/t131935.html").

It goes like this:
```

 sudo kate /var/lib/dpkg/status

```
Find (Ctrl+F) k3d and keep "finding next" (F3) until you find the k3d package.
The last line of package (i.e. after the "Depends", "Suggests", and "Description" fields) is:
```

Python-Versions: current

```
Remove the "s".
Save the file.

Done.

And this is why we should search the forums first before asking kiddies. This fixed my problem perfectly. Thank you vikingdocerrado!

---

