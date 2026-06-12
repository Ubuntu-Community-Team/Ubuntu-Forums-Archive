---
title: "I made a big mistake, now not network! Should I Re install Ubuntu or what???"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by donfisico on 2010-02-18
Hello guys,

I am a newbie to Ubuntu and Linux in general and today i have messed things up big time. 
Remember my post about installing [Thunderbird ]("http://ubuntuforums.org/showthread.php?t=1410041")(today`s one), well... I wanted to install Thunderbird 3.0 because I wanted to install an addon to minimize it on the tray (only avaible for thunderbird 3.0). Because I was so obsses with that idea I thought in installing instead mail-notify . Because I have problem with dependencies Ihad to build then I thought in removing the expat package. Well, huge mistake, I did type "apt-get autoremove expat". That make uninstall a lot of packages.  Terrified at the point of freezing face, I patiently install all the packages that seemed to be uninstalled. Then I reboot,  ubuntu worked but the network and the Gstreamer (and the the volume control) doesn`t . I do not what to do, I have no network (I am writing this from another computer)
I thought in [re-instaling]("http://ubuntuforums.org/showthread.php?t=125339") ubuntu but I am a little afraid after this and I do not want any of the instaled apps to be removed and didn`t want to touch the home directory. What shall I do????

---

### Post by darkod on 2010-02-18
As far as I know, apt-get autoremove just removes packages downloaded which are no more needed. It doesn't uninstall anything.
So maybe forcing installs messed it up actually.
If network manager is messed up, you could actually download the .deb file, transfer it on a usb stick and install on the broken computer. But first try a reboot just to see if something will change.
And this might not be related directly to networkmanager.

---

### Post by donfisico on 2010-02-18
Well, darkod, when *apt-get autoremove* was working I saw with my own eyes sentences like "uninstalling gnome-session" and many others. Imagine my surprise and my panic! As far as I know, when I try to install an already installed package with (example) *apt-get install gnome-session*, if really the package is already installed the answer will be "0 packages instaled, 0 packages updated..." or something like that (I saw this phrase lots of times in the past before this problem when I have tried to install a package that I thought it was not installed). But the sittuation is that only a few "0 packages instlaed..." messages I saw each time I tried to re-install the packages un-installed by  *apt-get autoremove. *So my conclusion is that *apt-get autoremove ***really** had uninstalled a lot of packages.
 Anyway, that is only a detail, wich .deb files should I download and then install to make my network work again? Network-admin is installed, but perhaps the package "network-manager" (or something like that) is lost and also they may be lost the drivers to my network card. I mean, I am not pretty sure where is the problem.....

---

### Post by darkod on 2010-02-18
For Karmic, I think it's this one:
[http://packages.ubuntu.com/karmic/net/network-manager-gnome](http://packages.ubuntu.com/karmic/net/network-manager-gnome)

If you have another version of ubuntu, at the top, right under the ubuntu logo you can go back in the links to find your version. Then in Network, then search for network-manager-gnome.

Otherwise for Karmic, open the above link and the 32bit and 64bit version are at the bottom of the page for download. Lets hope you have all dependancy packages otherwise it won't install I guess.

---

### Post by donfisico on 2010-02-18
Ok, thanks for the name of the packages. I have 9.04 (Jaunty) 64 bits, but with yours instructions I guess I can get to download the right ones. About depencies I saw that the package manager reports what dependencies is missing when you try to install a package. And I have just saw that also the depencies are in the web page. So it will be a question of patience. Stay tunned for the results, but keep in mind that it might be a slow process (depending on how many dependencies I have to download and put in the usb, then take them to computer with ubuntu).

---

### Post by donfisico on 2010-02-19
My USB driver is not mounted into Ubuntu. I guess I am lost and I have to make an re-installation....

---

