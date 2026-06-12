---
title: "postinstall disconnect monitor, ect"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2013-09-08
I dont have internet so after I install ubuntu I will go to place that charges by minute and download all the extra stuff I need. Once I start downloads, can I disconnect monitor? Can I also disconnect mouse and keyboard. I will be doing this on two computers so want to get one started downloading, then use monitor to get second computer downloading. Same for mouse and keyboard if possible. Dont want to bring two monitors, mice and keyboards unless I have to.

---

### Post by varunendra on 2013-09-09
> **acefromspace said:**
> I dont have internet so after I install ubuntu I will go to place that charges by minute and download all the extra stuff I need.  Once I start downloads, can I disconnect monitor? Can I also disconnect mouse and keyboard.
Short answer, yes you can do it with monitor, but you 'should not' do it with kb/mouse (and you Can Not do it with kb/mouse if they are not USB type). However...

Instead of downloading the same stuff multiple times, just install an extra program - AptOnCD, and to fully support its GUI functions (basically - restore button), also install a package - hal :
```
sudo apt-get install aptoncd hal
```

AptOnCD is a GUI application that can create a CD/DVD iso image of all the packages that you download with apt-get, Ubuntu Software Center or Synaptim Package Manager.

You can then burn this ISO (can be one or multiple depending upon the quantity of packages) to CD/DVDs and use them as offline packge repositories for your Ubuntu installation. The system(s) on which you will be using these packages must be same version of Ubuntu from which you created the CD/DVD.

So.. assuming you are using the exactly same version of Ubuntu on both machines, you will update one system > create AptOnCD ISO(s) > burn CD/DVDs from the ISO(s) > Insert the CD/DVD in the other system (which will automatically recognise it as a software source and will prompt you to add it as repository) > Install the same packages from the CD/DVD instead of internet.

If you don't want to burn CD/DVDs, I can give you instructions to install the packages from a folder. Let me know if you need more help with this. :)

---

### Post by acefromspace on 2013-09-12
Varun, thank you for the tip. It sounds perfect, and it would also be great if I ever have to redo the original computer again. If I understand correctly, the cd will include all downloaded software, dependencies and updates. Waiting for response... both computers are ready to go.

---

### Post by varunendra on 2013-09-12
> **acefromspace said:**
> If I understand correctly, the cd will include all downloaded software, dependencies and updates.

Yes. Since all of this comes in form of .deb packages, everything is covered by it.

*[Info part, you can skip it if it confuses you]*
However, AptOnCD has a 'smart selection logic' that makes it select only those packages by default that are newer if more than one version of the same package is available. While doing this, it takes full care of dependencies among the selected packages, but sometimes a fresh install can not jump to a much higher version of a package if some of the "in-betweens" are missing. This sometimes causes certain packages fail to install on a fresh installation.

Although you will be creating the ISOs from a fresh installation itself, this shouldn't happen, but is something you should know.
*[End of Info part]*

So.. when you are done with updates, installations and are going to create the ISOs with AptOnCD, just **make sure** it selects **ALL** the packages that have been downloaded (AptOnCD indicates at the bottom of its GUI how many packages found/how many selected).

You can verify that by looking at **/var/cache/apt/archives** directory and see if the number of .deb files in the directory is same as the number of packages selected by AptOnCD. If some packages are not selected, you can manually add them to the ISO (AptOnCD gives you the option to manually add packages).

To be extra safe, you can simply copy the whole **/var/cache/apt/** directory. :)

---

