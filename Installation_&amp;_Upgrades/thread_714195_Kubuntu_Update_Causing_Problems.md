---
title: "Kubuntu Update Causing Problems"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by ballysallagh on 2008-03-03
Hi,
I have had Ubuntu installed on an old computer of mine for the nine months or so, and I have never had any major problems with it but I was not particularly keen on the GNOME interface so I decided to try Kubuntu. I ran the Live CD and found that I quite liked it so I decided to install it. The install went fine and I rebooted the system to quit the Live CD and to boot from the hard drive. When I logged in a icon appeared telling me that I had new updates available so I opened the update manager and tried to install them. All the packages were successfully downloaded, but half-way through the install process I receive an error message that says:

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

So I clicked OK. I was then told that there was a new distribution available (version 7.10) was available which I knew there wasn't as that is the version that is on my disc, but I let it try to download and install it as I thought that maybe some files had been corrupted or something and it was trying to fix itself but after a few seconds another error message came up telling me the install could not start.

Next I tried to open the "Add/Remove Programs" to install Firefox as I am not overly pleased with the default browser and I was given the follwing error message:

"Another program is using the packaging system database (probably some other Adept application or apt-get or aptitude)."

Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself."

If I click Yes I get The KDE Crash Handler.
If I click Cancel the installer closes.
AND
If I  click No the installer opens and I can attempt to install programs but when the install starts I get the same message that I got when I tried to install the updates.
I have reinstalled Kubuntu on the chance that it was just a freak but the exact same thing happened.
I have a fair bit of experience on Windows but I am relitively new to Linux so please keep it simple. Any help would be appreciated.
Thanks in advance.

---

### Post by cmfarley19 on 2008-03-25
Same problem here.

Any thoughts?

---

### Post by zvacet on 2008-03-26
Do you have all repositories open?I don´t use Kubuntu,so I think it is good idea to read [this.](https://help.ubuntu.com/community/Repositories/Kubuntu) Did you closed Adept before you start with add/remove.Be sure that is the case.And you can try this

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ballysallagh on 2008-03-26
Thanks for your help, but I have since decided to switch to PCLinuxOS and this is working fine for me at the moment.

---

### Post by zvacet on 2008-03-28
Take distro which make you feel comfortable and enjoy it.

---

### Post by nadrach on 2008-03-29
This is caused by a problem committing part of the Qt3 upgrade, which is what KDE uses for its display, and the main upgrade procedure fails at that point, especially if you click on "OK" to acknowledge the error message, where "dpkg" shuts down because there are too many errors. Attempting to install any other programs after this will run into many problems. The solution is to finish the upgrade from a terminal window using:

sudo apt-get update

(you will need to enter your password to allow the "sudo") which will download the update list and then may give you an error message to run "dpkg" manually using the "--configure -a" option. What it omits to tell you is to also run this under "sudo". If you get this error, run the "dpkg" command. When you do this, the missing commit may ask if you want to replace the suspect file. Say "Y" and let "dpkg" run to complete the update.

If you don't get the error message about "dpkg", then run the command:

sudo apt-get install --fix-broken

which will run the missing bit (or bits) of "dpkg".

Then reboot (just for the clean-up) and you should be able to install other programs.

There is one side-effect, which I am about to raise as a separate post. If you use a display scheme other than the default KDE (I use "Point Reyes Green"), you will find after the upgrade that "Adept" no longer follows your chosen scheme and always uses the KDE default colors within the utility. I suspect that the upgrade problem with Qt3 may be the cause of this.

Andrew Morris
[www.amsor.org](www.amsor.org)

---

