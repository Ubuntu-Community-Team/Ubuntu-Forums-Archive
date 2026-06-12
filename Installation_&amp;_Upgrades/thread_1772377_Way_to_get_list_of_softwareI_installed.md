---
title: "Way to get list of softwareI installed?"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by cheetos316 on 2011-05-31
I'm considering rebuilding my system.  Is there any way to get the list of software that I added?  I know I can see the list of installed software in Ubuntu Software Center, but that list includes items that were included.  Rather than going through that long list to see what was included and what I added, is there a way to see only the items I added?

Thanks!

---

### Post by matt_symes on 2011-05-31
Hi

```
dpkg --get-selections > ~/installed_software
```

This will get a list of the installed packages on your system and put them in a file called installed_software in your home directory.

Make a backup of this file. Reinstall the os, put the file in your home directory, then open a terminal and type.

```
sudo dkpg --set-selections < ~/installed_software
```

Enter your password. It will not be echoed to the screen. This will update dpkg with your packages you have installed.

Next type

```
sudo apt-get install dselect
```

to install dselect on your system. Start dselect with

```
sudo dselect
```

Select the i (lower case I) option to reinstall your old packages on the new system.

Kind regards

---

### Post by cheetos316 on 2011-05-31
Wow that is really handy.  Now, just for personal curiosity, is there a way to manually select which packages I want vs the packages I don't want?  I can probably uninstall the ones I don't want right now prior to running the first line of code but I was just wondering if it could be done.

Thanks again!

---

### Post by matt_symes on 2011-05-31
Hi

> **cheetos316 said:**
> Wow that is really handy.  Now, just for personal curiosity, is there a way to manually select which packages I want vs the packages I don't want?  I can probably uninstall the ones I don't want right now prior to running the first line of code but I was just wondering if it could be done.

Thanks again!

To be honest, i am not sure as i have always just installed the lot. Maybe check out the options in dselect. There is a 'select' option as well as an 'install' option.

From man dselect

> 
select
       View or manage package selections and dependencies.

       This  is  the  main function of dselect. In the select screen, the user
       can review a list of all available and  installed  packages.  When  run
       with  administrator  privileges,  it  is also possible to interactively
       change packages selection state. dselect  tracks  the  implications  of
       these changes to other depending or conflicting packages.

       When  a conflict or failed depends is detected, a dependency resolution
       subscreen is prompted to the user. In this screen, a list of  conflict&#8208;
       ing  or  depending  packages is shown, and for each package listed, the
       reason for its listing is shown. The user  may  apply  the  suggestions
       proposed  by  dselect,  override  them,  or  back  out all the changes,
       including the ones that created the unresolved depends or conflicts.

       The use of the interactive  package  selections  management  screen  is
       explained in more detail below.

   install
       Installs selected packages.

       The configured access method will fetch installable or upgradable pack&#8208;
       ages from the relevant  repositories  and  install  these  using  dpkg.
       Depending  on the implementation of the access method, all packages can
       be prefetched before installation, or fetched when needed.  Some access
       methods may also remove packages that were marked for removal.
<snip>


Maybe select is your best bet. Read up on dselect and dpkg to verify the options i have given you as they were from memory, but i am pretty sure the are correct.

Kind regards

---

