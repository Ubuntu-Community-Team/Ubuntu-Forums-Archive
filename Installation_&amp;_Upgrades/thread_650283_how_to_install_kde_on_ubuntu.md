---
title: "how to install kde on ubuntu"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by d0tn3t on 2007-12-26
[SIZE="3"]i installed Ubuntu  7.04 and i want to install the kde from the cd of kubuntu coz i have a very slow internet connection and every time i trying to use synaptic it make the download from the internet not from the cd 
[/SIZE]

---

### Post by LaRoza on 2007-12-26
Can you install Kubuntu?

I don't think you can do that, however, you can buy the 6 DVD set of Ubuntu and the Universe and Multiverse Repositories from [http://thelinuxstore.ca](http://thelinuxstore.ca)

---

### Post by ironstorm on 2007-12-26
> **d0tn3t said:**
> [SIZE="3"]i installed Ubuntu  7.04 and i want to install the kde from the cd of kubuntu coz i have a very slow internet connection and every time i trying to use synaptic it make the download from the internet not from the cd 
[/SIZE]

The Ubuntu CD doesn't contain the KDE packages...  So you'll have to either get a Kubuntu CD like d0tn3t said ([https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)) or download them using aptitude install KDE (but that will be pretty big, probably 100+ MB of downloads)

Cheers,
-G

---

### Post by LaRoza on 2007-12-26
> **ironstorm said:**
> The Ubuntu CD doesn't contain the KDE packages...  So you'll have to either get a Kubuntu CD like d0tn3t said ([https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)) or download them using aptitude install KDE (but that will be pretty big, probably 100+ MB of downloads)

Cheers,
-G

```

sudo aptitude install kde-core

```

Is smaller doesn't crowd your menus.

---

### Post by adityakavoor on 2007-12-26
```
sudo apt-get install kubuntu-desktop
```

---

### Post by d0tn3t on 2007-12-26
i have the kubuntu cd and i want to install the kde but it keep connecting to the internet to download and install i just want it to load it from the cd i have

---

### Post by LaRoza on 2007-12-26
> **adityakavoor said:**
> ```
sudo apt-get install kubuntu-desktop
```

That is a much larger package.

@OP I don't think you can use the Kubuntu install disk as a repository disk.

---

### Post by d0tn3t on 2007-12-26
so there is no possibility to install kde without internet connection ?????

thanx guys for help

---

### Post by KOld Iron on 2007-12-26
Okay, I haven't really tried this myself, but when I look at the Synaptic Package Manager, you should be able to do the following:

1. Start Synaptic Package Manager
2. From the menu select "Settings/Repositories"
3. On the first register card "Ubuntu Software" DE-select all sources from internet
4. On the second register card "Third Party Software" DE-select all sources you may have there
5. On the same register card use "Add CD-ROM" (having your Kubuntu CD in the drive)
6. That last step should add the Kubuntu CD to your list of Third Party Software OR to the list CDs on the first register card (apparently it depends). Select it
7. Close and push the "Reload" button in the menu
8. Now push the "Selections" button on the lower left side of the window. It will generate a list above it. One of the entries reads "KDE Desktop Environment"
9. If you select this entry, the main window will list all the KDE components
10. Select them all for installation

The installation should now take place from the CD. Again, I could not test that on my system, because it is my productive system. But give it try and see whether it does the trick.

[EDIT]: Item 6 was corrected, sorry about that.

---

