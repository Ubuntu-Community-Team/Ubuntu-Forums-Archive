---
title: "Upgrade from 12.04 to 14.04"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by andysummerskill on 2015-11-14
Been running 12.04(LTS) for 3 years with no problems but decided it's about time to upgrade. However, Update Manager only gives me the option to upgrade to 12.10 (which is unsupported) not to the current LTS version, 14.04.

I thought it should always be possible to upgrade from one supported LTS version to the next?

Is there anyway I can do the upgrade from 12.04 to 14.04 or is the choice for me either to do a fresh install of 14.04 or stick with 12.04?

Thanks,
Andy

---

### Post by deadflowr on 2015-11-14
Your software sources settings is set for any version.
That needs to be changed to long-term-release only.
To do so, you need to click on the settings button in the update manager.
Then go to the section updates.
Then toggle the line that should read something like 'notify of new version"
Select the long term release option.
(It'll ask for a password)
The click on the close button, and if it doesn't ask to reload, when you get to the main update manager window, click on check.
The check will reload the option and when that is done the option of release-upgrade will be for 14.04.

Hope it helps

---

### Post by andysummerskill on 2015-11-14
Thanks for the reply. 

I should have said that if I choose "Long-term Support versions only" in Update Manager, then there is no version shown to upgrade to.

Thanks,
Andy

---

### Post by deadflowr on 2015-11-14
Do you have (normal) updates ready to install?

And if so, is one of them marked as something like update-manager-core?

---

### Post by andysummerskill on 2015-11-14
I did an update immediately before investigating upgrading. Didn't note whether one of the packages was [COLOR=#000000]update-manager-core. However, just now Update Manager shows "There are no updates to install".

Thanks,
Andy[/COLOR]

---

### Post by Bashing-om on 2015-11-14
andysummerskill; Hello;

I think command line rather then GUI, I would want to look directly and see what is set for the upgrade path.
```

cat /etc/update-manager/release-upgrades

```
Make sure the system is fully updated, any proprietary graphics driver ( and other PPAs) are reverted to standard, and screensaver is disabled.
Then:
Release Upgrade from terminal .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than 1 way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andysummerskill on 2015-11-15
cat /etc/update-manager/release-upgradesreturns 
prompt=LTS
Also, just to confirm, 'system setting -> details -> overview' shows that the OS is, indeed, ubuntu 12.04 LTS.
Can anyone confirm that, because I am running a currently supported LTS version, I should expect Update Manager to give me the option to upgrade to the next LTS version?

Thanks,
Andy

---

### Post by tokyobadger on 2015-11-15
[Ubuntu wiki notes on upgrading to 14.04 from 12.04 or 13.10](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Upgrading_from_Ubuntu_12.04_LTS_or_Ubuntu_13.10)
```
[h=2]Upgrading from Ubuntu 12.04 LTS or Ubuntu 13.10[/h][COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]To upgrade on a desktop system: [/FONT][/COLOR]

[LIST]
[*]Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
[*]Update Manager should open up and tell you: New distribution release '14.04 LTS' is available. 
[*]Click Upgrade and follow the on-screen instructions.
```
[/LIST]
14.04 will be supported until 2019. The next LTS 16.04 is released April 2016.

---

### Post by andysummerskill on 2015-11-15
Yes, that is what I would expect to happen but it isn't happening on my machine. Hence my query.

---

### Post by tokyobadger on 2015-11-15
Are you running update-manager from command line?

---

### Post by andysummerskill on 2015-11-15
Running upgrade from CL gives
andy@andy-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
andy@andy-laptop:~$

---

### Post by deadflowr on 2015-11-15
Please post the full output for 
```
sudo apt-get update
```
Use code tags in your reply.

---

### Post by flocculant on 2015-11-15
apt-get dist-upgrade is nothing to do with updating to a new version of the OS

Try

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

---

