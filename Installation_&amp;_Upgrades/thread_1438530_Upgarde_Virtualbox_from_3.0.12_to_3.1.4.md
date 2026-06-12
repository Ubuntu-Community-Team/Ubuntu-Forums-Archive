---
title: "Upgarde Virtualbox from 3.0.12 to 3.1.4"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by motorcity909 on 2010-03-25
Hi all

I'm currently using the PUEL version of Virtualbox 3.0.12 and whenever I open it, it prompts me to update - see screengrab.

Clicking that link and choosing to open it via the package installer (see screengrab) results in the error screen below - another screengrab.

I then realised the deb file was named Jaunty, so went to the [Vbox website]("http://www.virtualbox.org/wiki/Linux_Downloads") to download the Karmic file.

Running that via package installer produces the same error - **Error: Conflicts with the installed package 'virtualbox-3.0'**

Do I need to remove the old version first?  If so, how do I do that (given that this is the PUEL version not the open-source version) and will my existing virtual machines (I've got WinXP and ChromeOS) be safe and still work afterwards?

My reason for wanting to upgrade is to virtually try Ubuntu 10.4 which I just cannot get to run or install in Vbox (either from a CD or from the iso image) so I figured upgrading to the latest Vbox might help.

Any help much appreciated
Dave

---

### Post by s.fox on 2010-03-25
Hello,

I just found [this]("http://ubuntuforums.org/showthread.php?t=1346197") thread which describes the same error as you are having.   I would try the advice given in that thread :)

-Silver Fox

---

### Post by new_tolinux on 2010-03-25
Uninstall the current version by using this from a terminal ```
sudo apt-get remove VirtualBox
```
I do not have it installed atm, so the package-name will be different.
Don't let the program delete old configs and machines, just uninstall.

Then install the new version as normal.

---

### Post by motorcity909 on 2010-03-26
Thanks all.

I managed to install 10.4 in Vbox by first disabling ACPI in the options so am happy with that for now.

I will get round to installing the new Vbox using the methods advised.

Many thanks
Dave

---

### Post by motorcity909 on 2010-03-28
I followed the other thread and Vbox 3.1.6 installed beautifully, no loss of virtual machines and Ubuntu 10.04 runs much better in it, inc. full screen.

Cheers
Dave

---

### Post by mbelos on 2010-05-31
> **motorcity909 said:**
> Thanks all.

I managed to install 10.4 in Vbox by first disabling ACPI in the options so am happy with that for now.

I will get round to installing the new Vbox using the methods advised.

Many thanks
Dave

Thanks for posting back, this just saved me an hour or so of research!

---

