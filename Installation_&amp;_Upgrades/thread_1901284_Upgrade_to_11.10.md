---
title: "Upgrade to 11.10"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by Khalil Ibrahim on 2011-12-28
Hello there,

I am trying to upgrade to the new 11.10 ubuntu. I am on 11.04. I already updated all my software, but the upgrade is too big to be downloaded by day. Since we have a limited connection. But I can do this by night. This is my first issue. The second one is that I would like to download the upgrade and install it later. So I am searching for a complete guide on how to do this using command line (since I would be sleeping not watching over). I know it could be done with cronetab, but I can't really apply what I know to my case. Please step by step I am an artist no computer guy.
Thanks in advance.
K.I.

---

### Post by Paddy Landau on 2011-12-28
[LIST]
[*]Go to Update Manager and select *Check*.
[*] Then close Update Manager without updating.
[/LIST]
Then:
 
[LIST]
[*] Open Synaptic Package Manager (if you don't have it, open Ubuntu Software Centre and install *synaptic*).
[*] Press *Mark All Upgrades*.
[*] Press *Apply*.
[*] Select the check-box *Download package files only*.
[*] Press *Apply*.
[/LIST]
 
That will download the files but not install them.
Later, you can open either Update Manager or Synaptic Package Manager and apply the updates.

---

### Post by Khalil Ibrahim on 2011-12-28
> **Paddy Landau said:**
> [LIST]
[*]Go to Update Manager and select *Check*.
[*] Then close Update Manager without updating.
[/LIST]
Then:
 
[LIST]
[*] Open Synaptic Package Manager (if you don't have it, open Ubuntu Software Centre and install *synaptic*).
[*] Press *Mark All Upgrades*.
[*] Press *Apply*.
[*] Select the check-box *Download package files only*.
[*] Press *Apply*.
[/LIST]
 
That will download the files but not install them.
Later, you can open either Update Manager or Synaptic Package Manager and apply the updates.
I am grateful, but then I think I have to be there to do this manually, when I need it to be synchronized after midnight (when I have an open free download possibility). Could you still help me out with this?
Regards,
K.I.

---

### Post by Paddy Landau on 2011-12-28
You would have to run the commands in a way that doesn't require you to be there to enter your password.

Warning: The following will complete the upgrade; it will not merely download the files.

**First:**

[LIST=1]
[*]First, run Update Manager and ensure that your system is fully up-to-date. Restart if required.
[*]Back up your data!
[/LIST]
**Second:**

[LIST=1]
[*]Create a script file (using Text Editor) with the following contents. To make it easier, let's agree on a name -- let's say you put it in your home folder and call it [FONT=Fixedsys]midnight[/FONT] (copy-and-paste to ensure you get the commands correct):
```
#!/bin/bash

apt-get update && apt-get install update-manager-core && do-release-upgrade

echo '*** FINISHED ***'
```
[*]Now right-click the file > *Properties* > *Permissions* > *Execute* > check *Allow executing file as a program*.
[*]Test the file as follows:
[LIST=a]
[*]Open a terminal by pressing Ctrl-Alt-T.
[*]Enter the following command, changing "khalil" to your user name:```
/home/khalil/midnight
```The command should fail with a few error messages starting with something like "Could not open lock file". However, if it says, "No such file or directory", then you have placed the file in the wrong place.
[/LIST]
 
[*]Schedule your script to run as root for five minutes after midnight as follows.
[LIST=a]
[*]Open a terminal by pressing Ctrl-Alt-T.
[*]Enter the command:```
sudo VISUAL=gedit crontab -e
```
[*]At the end of the file, add the following line, changing "khalil" to your user name  (copy-and-paste to ensure you get the command correct):
```
5 0 * * * /home/khalil/midnight &>/home/khalil/midnight.list
```
[*]Save the file.
[/LIST]
 
[/LIST]
At five minutes past midnight, the script should run. The results of the script will be in your home directory in a file named [FONT=Fixedsys]midnight.list[/FONT]. Check for any errors. It should have the line "*** FINISHED ***" at the end (otherwise it hasn't finished running).

You will have to restart the computer.

If there are no errors, you need to prevent the script from running again: Repeat step 4, but this time delete the line you had added.

Good luck! Unattended distribution upgrades can be tricky!

---

### Post by Khalil Ibrahim on 2011-12-28
Thanks indeed! 
So,  if I understand you well, there is no way to just download unattended and then install later? If this is the case, I should prefer to stay awake till midnight and use the first option. But could it be possible there should be no way around?
K.I.

---

### Post by Paddy Landau on 2011-12-28
> **Khalil Ibrahim said:**
> there is no way to just download unattended and then install later?
I'll bet there is, but I don't know how.

Upgrades sometimes can be tricky, so, yes, I would suggest you attend the upgrade. Choose a day when you aren't working the next day, and get some sleep beforehand!

Please back up first.

---

### Post by grahammechanical on 2011-12-28
I do all my updates and upgrades and downloads after midnight as it does not count towards my download usage. There is a limit to how much I can download during a month.

This is not much of a problem unless you are on a dial-up modem. It can take hours not minutes.

Regards.

---

### Post by Khalil Ibrahim on 2011-12-28
> **grahammechanical said:**
> I do all my updates and upgrades and downloads after midnight as it does not count towards my download usage. There is a limit to how much I can download during a month.

This is not much of a problem unless you are on a dial-up modem. It can take hours not minutes.

Regards.
Hi,

Downloading the upgrade with my internet connection could take me up to three nights. This is why I need that crontab script.

Thanks.
K.I.

---

### Post by Paddy Landau on 2011-12-28
> **Khalil Ibrahim said:**
> Downloading the upgrade with my internet connection could take me up to three nights.
Three nights! As distribution upgrades can be problematic, may I suggest a different course?

Wait until 12.04 (a Long-Term Release) is available; order its CD; and install 12.04. Otherwise, you may find you've wasted three nights on upgrading to 11.10 only to find that the upgrade doesn't work.

Then stick with 12.04 until the next LTS, which is supposed to be 14.04.

---

### Post by Khalil Ibrahim on 2011-12-28
Dear me!! Well, I might do that! But if you say I could upgrade from a live cd, without doing a full install and erasing all my previous installation, then I could as well just schedule 11.10 as torrent and use it to upgrade whenever it downloads. Am I right?

Regards,
K.I.

---

### Post by Paddy Landau on 2011-12-28
> **Khalil Ibrahim said:**
> But if you say I could upgrade from a live cd...
I was suggesting a fresh installation rather than an upgrade; it would be more likely to work well.

> **Khalil Ibrahim said:**
> ... I could as well just schedule 11.10 as torrent and use it to upgrade whenever it downloads.
A torrent sounds like a great idea, because you can schedule it to run during your "free" hours. But, as I say, in your place I wouldn't be in a hurry to upgrade in case the upgrade doesn't work, but instead do a fresh installation of 12.04 in May. It will be supported for a full five years, although you'd probably want to upgrade again when 14.04 comes out.

---

