---
title: "Install from downloaded package -- how?"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by TheAJKMan on 2008-07-21
Okat folks, hope you'll bear with me on this one. Want to have a look at the Flock browser and have downloaded the tar.gz package to my desktop. For the life of me I cannot remember how to install the package for use on the system. Could someone help the newb out please. Thanks :)

---

### Post by iaculallad on 2008-07-21
> **TheAJKMan said:**
> Okat folks, hope you'll bear with me on this one. Want to have a look at the Flock browser and have downloaded the tar.gz package to my desktop. For the life of me I cannot remember how to install the package for use on the system. Could someone help the newb out please. Thanks :)

Assuming you downloaded the latest file below:

> flock-1.2.4.en-US.linux-i686.tar.gz

On your terminal:

For the Dependency library:

```
sudo apt-get install libstdc++5
```

Change Directory to the location of the downloaded Flock archive:

Say: (It's in the Desktop)

```
cd ~/Desktop
```

Extract the archive:

```
tar xzvf flock-1.2.4.en-US.linux-i686.tar.gz
```

Change Directory to Flock folder:

```
cd flock
```

Execute it:

```
./flock
```

---

### Post by ibutho on 2008-07-21
You need to simply unzip the tarball using File Roller or the command "tar zxvf somefile.tar.gz". You can then navigate into the exxtracted directory and click on the icon labelled flock or from the cli, cd into the extracted directory and run "./flock".

---

### Post by michaeltobin on 2008-07-24
hey im pretty new to ubuntu so dont really know what im doing that much!
i followed the above instructions and flock worked fine until i closed the terminal and it disapeared with no way to reopen except to re follow the above installation instructions, again when i close the terminal flock closed down and there was no icon in the menu to reopen it!
i need flock as the extension for the online game i play (uwars) is not compatible with firefox3.
any ideas

thanks in advance 
mike

---

