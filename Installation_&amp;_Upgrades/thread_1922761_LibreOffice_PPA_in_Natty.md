---
title: "LibreOffice PPA in Natty"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by dstark on 2012-02-09
Greetings, all.

I'm still fairly new to Ubuntu (Natty), so this question may have a fairly simple answer, but I haven't been able to find it yet. Is it possible to install a later distribution's (e.g., Oneiric) current version of LibreOffice on an earlier one (e.g., Natty) via the LibreOffice PPA? If so, how?

I'd rather not receive backport updates for everything on the system, but I would like to have the most current version LibreOffice, especially once the current version for Precise becomes a stable release of LibreOffice 3.5.

Thanks so much for the thoughts and assistance.

---

### Post by Dennis N on 2012-02-09
Add this PPA:

ppa:libreoffice/ppa

with 

sudo add-apt-repository ppa:libreoffice/ppa

Then update your package lists, and the newer version should show up for upgrade in a package manager.

---

### Post by dstark on 2012-02-09
Thanks so much for the feedback, Dennis N. At present, things only update to the most current version of LibreOffice listed for [Natty]("https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=natty"), which is 3.4.3. The most current stable version, at this time, is [3.4.5]("http://www.libreoffice.org/download/"). If I'm reading things correctly, this version is in the pipe for [Oneiric]("https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=oneiric") (as is 3.5rc1?). But, on

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Natty doesn't pick up any updates past 3.4.3. Any thoughts on how I might get it to do so without enabling backports for system updates overall?

---

### Post by dstark on 2012-02-09
In case it's relevant, I should probably add that I've also tried
```
sudo apt-get update --fix-missing
sudo apt-get dist-upgrade
```
and still not seen any LibreOffice updates past 3.4.3.

---

### Post by Dennis N on 2012-02-09
> **dstark said:**
> 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Natty doesn't pick up any updates past 3.4.3. Any thoughts on how I might get it to do so without enabling backports for system updates overall?

Second command is incorrect:

You want [B]sudo apt-get upgrade
[/B]
Or run update-manager, click on check, and it will pick up the upgrade.

---

### Post by Dennis N on 2012-02-09
Looks like 3.4.3 is the latest for Natty in there. Original distro version was 3.3.2, and two upgrades since from PPA, if I am not mistaken.

Can't really advise on newer versions. I stick to the PPA and what it offers for my version of Ubuntu.

You can check out the Libre Office Downloads page for more information.

[http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)

---

### Post by viperdvman on 2012-02-09
I run version 3.4.3 for Natty as well. However, the **lo-menubar** does not work with the newest version. So I no longer have the app menu when I run LibreOffice like I used to.

Any way to get it back?

---

### Post by dstark on 2012-02-10
@Dennis N.,
```
sudo apt-get update
sudo apt-get upgrade
```
still does not upgrade LibreOffice past 3.4.3 in Natty. (Still learning: Is ["smart" conflict resolution]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands") something I didn't want to invoke here to begin with?)

Just for kicks, I added
```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu oneiric main
```
as an additional repository. When I open the Update Manager and check for updates, I can now see what look like updates for LibreOffice from 3.4.3 to 3.4.5. But, I cannot "check" these updates to select them for installation. When I do
```
sudo apt-get update
sudo apt-get upgrade
```
I get a message that says "The following packages have been kept back:" with a list of the LibreOffice package updates that I see in Update Manager.

Natty now seems at least to see the updates. Any thoughts about how *actually* to install these updates that Natty now apparently sees? ;)

@viperdvman,

I'm using the Ubuntu Classic interface, but have you tried [uninstalling the lo-menubar]("http://www.howtogeek.com/93212/add-global-menu-support-to-libreoffice-in-ubuntu-11-04-unity/") package via Synaptic? Does that at least give you the menu bar back inside the LibreOffice window?

---

### Post by viperdvman on 2012-02-17
> **dstark said:**
> 

@viperdvman,

I'm using the Ubuntu Classic interface, but have you tried [uninstalling the lo-menubar]("http://www.howtogeek.com/93212/add-global-menu-support-to-libreoffice-in-ubuntu-11-04-unity/") package via Synaptic? Does that at least give you the menu bar back inside the LibreOffice window?

Yes, I already uninstalled it. Why have it if Natty's lo-menubar doesn't support LibreOffice 3.4.3? It was the sacrifice I had to make to get a newer LibreOffice in Natty.

---

### Post by mastablasta on 2012-02-17
you can download the .deb file on libre office site. for example latest stable or previous stable....
 
install instrucitons for the deb file instalation are found in the readme file inside the package. make sure you do desktop integration.
 
i am using 3.4.3 (cause it works best with word 2003) on Kubutnu 10.10 as well as Debian 6 stable (chrunchbang statler but the first version with xfce). works well. not sure how well it works in Gnome...

---

### Post by viperdvman on 2012-02-18
I found one method that is getting the global menu to work in Natty. It required me going to launchpad and grabbing an older version of the lo-menubar (**0.1.0-0ubuntu1**) and installing it ([link here]("https://launchpad.net/ubuntu/+source/lo-menubar/0.1.0-0ubuntu1/+build/2302331")) It works well, and I have my LibreOffice global menu back. However, my package manager/update manager is constantly nagging me to upgrade to the newest version of lo-menubar (**0.1.1~pre1-0ubuntu2**), the one that doesn't work with LibreOffice 3.4.3 in Natty. Unless there's a way I can disable that particular update, or if there's a newer version of lo-menubar out there than the one my Natty has, I'll just have to give up using the lo-menubar.

---

