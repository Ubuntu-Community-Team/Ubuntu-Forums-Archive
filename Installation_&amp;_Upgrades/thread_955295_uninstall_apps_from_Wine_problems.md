---
title: "uninstall apps from Wine problems"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by raedbenz on 2008-10-22
hi,,
i have just installed wine on Ubuntu8.04.
i install Windows applications ".exe" just by double clicking them. the installation completes fine, but most of the apps dont run (why!??) , moreover when i try to uninstall them, the uninstall wizard starts and completes succcesfully but the icon of the apps in the Applications Menu/wine remains?
any hints?

Thanx
Raed

---

### Post by brijith on 2008-10-22
Hai,

I don't have an answer about why Wine is not working. I can suggest a way to remove the icons from the menu.

Run

```
sudo nautilus /usr/share/applications/
```

A window will pop up. You can delete the unwanted Icons from it.In effect it will get removed from the Main Menu

---

### Post by raedbenz on 2008-10-22
> **brijith said:**
> Hai,

I don't have an answer about why Wine is not working. I can suggest a way to remove the icons from the menu.

Run

```
sudo nautilus /usr/share/applications/
```

A window will pop up. You can delete the unwanted Icons from it.In effect it will get removed from the Main Menu

i tried but i cant see the files i installed also the Wine Icon isnt there.
i used this tuutorila to install IE6 and wine : [http://www.howtoforge.com/ubuntu_internet_explorer](http://www.howtoforge.com/ubuntu_internet_explorer)

more over how can uninstall wine itself?
thanks

---

### Post by raedbenz on 2008-10-22
hi
i think i worked it out.
it seems the version of wine was old.
i used the guide from winehq website to install it now and works.
thanks

---

### Post by Mark Phelps on 2008-10-22
You said earlier that most of the apps didn't run.  Now that you've installed a more current version of Wine, do you get the same results? Or do most of the apps run now?  Am interested because I tried Wine months ago, and in my case, NONE of the apps worked.  If the situation is much better now, it would be worth trying Wine again.

Thanks for any info.

---

### Post by raedbenz on 2008-10-22
hi,
yes i have tried a couple of apps and they work with the new Wine.
follow this link    [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Raed

---

### Post by raedbenz on 2008-10-25
still cant remove the uninstalled apps from Applications/Wine/Programs list

hints????? even manualy they are not in 

/usr/share/applications/

---

### Post by brijith on 2008-10-27
> **raedbenz said:**
> still cant remove the uninstalled apps from Applications/Wine/Programs list

hints????? even manualy they are not in 

/usr/share/applications/

You can find the installation folder of wine application Under your home directory 

```
cd
cd .wine/
```

In this folder you may find windows like folder structure, that is you may see a folder named **program files** in that you can find all in that you may find folders for each application that you have installed using wine. 

Go through those folder deleting the unwanted application folder some time help you. See, I am not sure about it. I think it is better to wait for a good reply. I cannot check it since I my office every PC run Debian. 

Sorry...

---

### Post by marshalium on 2008-10-27
> **raedbenz said:**
> still cant remove the uninstalled apps from Applications/Wine/Programs list

hints????? even manualy they are not in 

/usr/share/applications/

Wine installs its menu items in ~/.local/share/applications/wine

---

### Post by brijith on 2008-10-27
> **marshalium said:**
> Wine installs its menu items in ~/.local/share/applications/wine

I think ~/.local/share/applications/wine contains .desktop files, right ?

---

### Post by raedbenz on 2008-10-27
yes it worked.
thanks

---

### Post by marshalium on 2008-10-27
> **brijith said:**
> I think ~/.local/share/applications/wine contains .desktop files, right ?

Yes. 

Wine also installs .directory files in ~/.local/share/desktop-directories/ and icon files in ~/.local/share/icons/

It sure would be nice if wine cleaned this stuff up when it uninstalled applications.

---

