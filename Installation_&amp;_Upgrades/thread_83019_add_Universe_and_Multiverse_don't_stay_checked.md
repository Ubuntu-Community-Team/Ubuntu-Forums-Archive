---
title: "add Universe and Multiverse don't stay checked"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-10-27
[B][U]I follow the instructions below but Community maintained (Universe) and Non-free (Multiverse) don't stay checked.
[/U][/B]:confused: 
How do I add Universe and Multiverse?

By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

   1.

      Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.

      In Synaptic choose Settings-> Repositories.
   3.

      Click the Settings button.
   4.

      Tick Show disabled software sources, then click Close.
   5.

      On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.
   6.

      You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked.

---

### Post by denkedran on 2005-10-27
try to set it manually in /etc/apt/sources.list
simply uncomment the lines with Universe and Multiverse

---

### Post by super on 2005-10-27
try manually editing the /etc/apt/sources.list

[FONT="Courier New"]sudo gedit /etc/apt/sources.list[/FONT]

remove the pound signs (#) from before the url of the repositories that you want to add

---

### Post by denkedran on 2005-10-27
@super
take a look at our first lines
this is spooky

---

### Post by AllanP on 2005-10-27
OK thanks; tried that. There were no ## signs before the lines, just a space, so I deleted one space bringing the line home. Here is one exampe:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Still these items remain unchecked.

---

### Post by rjwood on 2005-10-27
Here is mine--make it look like this.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

make sure you don't include the lines in my signature

---

### Post by AllanP on 2005-10-27
Still the same; I'll try logging off and back on.

---

### Post by super on 2005-10-28
> @super
take a look at our first lines
this is spooky

spooky theme from the x-files
doo, doo, doo, da! doo, doo, doo, da!

---

### Post by aysiu on 2005-10-28
One last try: follow the instructions here... [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Don't forget to type the command ```
sudo apt-get update
```

---

