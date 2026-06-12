---
title: "Disabled software sources"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2012-10-24
Hi, how can I re-enable software sources disabled by the system as a result of upgrading from 12.04 to 12.10?

---

### Post by dino99 on 2012-10-24
> **Tornikee said:**
> Hi, how can I re-enable software sources disabled by the system as a result of upgrading from 12.04 to 12.10?

sudo apt-get install software-center

---

### Post by Tornikee on 2012-10-24
> **dino99 said:**
> sudo apt-get install software-center
Ran that, but they still show up as disabled: [http://bit.ly/XUkpod](http://bit.ly/XUkpod)

---

### Post by deadflowr on 2012-10-24
Open up the software center go to the menu and find software sources, other software. 
Or update manager and open up settings (same thing).
Or synaptic, or the dash and type software sources, then proceed to re enable those that can be enabled.
Some sources might need to be purged in favor of newer ones for the latest Ubuntu you're running.
then open a terminal and run sudo apt-get update, to simply make sure their aren't any errors and to reload the package info.

---

### Post by Tornikee on 2012-10-24
> **deadflowr said:**
> Open up the software center go to the menu and find software sources, other software. 
Or update manager and open up settings (same thing).
Or synaptic, or the dash and type software sources, then proceed to re enable those that can be enabled.
Some sources might need to be purged in favor of newer ones for the latest Ubuntu you're running.
then open a terminal and run sudo apt-get update, to simply make sure their aren't any errors and to reload the package info.
If by 'enabling' you mean unchecking and re-checking the boxes shown in my screenshot, and then running the update script, it doesn't change anything.

---

### Post by plucky on 2012-10-24
Do you know for certain that there exists **Quantal** repositories for those PPAs?

Not all PPAs have Quantal repositories in place.You have to go through them individually and make sure the Quantal repository exists.

Post output for ```
cat /etc/apt/sources.list.d/*.list
```


Good Luck

---

### Post by Tornikee on 2012-10-24
No I don't know if there are 12.10 repositories for these sources, and probably there aren't. But how should I enable these when there are repositories? Will just the ```
sudo apt-get update
``` do it?

The update for the source list script is:

```
tornike@TornikeLinux:~$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/alanbell/unity/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/alanbell/unity/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/atareao/atareao/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/diesch/testing/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/diesch/testing/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/fossfreedom/rhythmbox-plugins/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/fossfreedom/rhythmbox-plugins/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/ikarosdev/unity-revamped/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/shimmerproject/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/shimmerproject/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/synapse-core/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/synapse-core/ppa/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/webupd8team/gthumb/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/webupd8team/gthumb/ubuntu quantal main # disabled on upgrade to quantal
deb http://ppa.launchpad.net/webupd8team/puddletag/ubuntu quantal main # disabled on upgrade to quantal
deb-src http://ppa.launchpad.net/webupd8team/puddletag/ubuntu quantal main # disabled on upgrade to quantal

```

---

### Post by plucky on 2012-10-24
None of the lines have a # in front of them.

If you run ```
sudo apt-get update
``` any line that gives a '404 not found' error are the ones that do not have a quantal repository.

Good Luck

---

### Post by Tornikee on 2012-10-24
Thank you.

---

### Post by Papex on 2012-10-24
I think I am facing the same issue here. After upgrade I'm unable to check the boxes for other software that was disbled before upgrade.

When I click on a checkbox I get prompted for authentification. After authentification nothing happens when I click the checkboxes.

I googled it and then found this:
[http://askubuntu.com/questions/203142/other-software-checkboxes-in-software-sources-are-not-working-after-update-to-12](http://askubuntu.com/questions/203142/other-software-checkboxes-in-software-sources-are-not-working-after-update-to-12)

However it didn't fix it. 

Also tried the things mentioned above. Still no luck. What should I do?

---

### Post by DustofDust on 2012-10-24
there is also a thread about it

[http://ubuntuforums.org/showpost.php?p=12310585&postcount=6](http://ubuntuforums.org/showpost.php?p=12310585&postcount=6)
> add [https://launchpad.net/~webupd8team/+.../y-ppa-manager](https://launchpad.net/~webupd8team/+.../y-ppa-manager) to your lists of repos with synaptics... if you dont have synaptics installed do it as its easier to change things like repos

[http://www.webupd8.org/2012/10/y-ppa...-with-new.html](http://www.webupd8.org/2012/10/y-ppa...-with-new.html)
you can also follow this way to install

Quote:
- Re-enable working PPAs after Ubuntu upgrade: when you upgrade to a newer Ubuntu release, the PPAs are disabled so using this feature, the PPAs that work with the new Ubuntu version you're using are re-enabled, leaving the others disabled
it does a lot more too, like to find a repo for a program on launchpad and install it

---

