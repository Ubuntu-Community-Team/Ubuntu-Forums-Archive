---
title: "Upgrade to OpenOffice.org 3.0"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Hydrohs on 2008-12-01
2.4 came installed with Intrepid Ibex, but I want to update it to 3.0. I haven't had any luck downloading it from the website and following the instructions, my terminal just says that it cannot open the package. And since there isn't an option to upgrade in the version I already have I don't know what to do, any help would be appreciated.

---

### Post by anuban on 2008-12-01
Just add
[I]deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
*to the Software source -> Third party *Software

As soon as you add the above key, it should show you an update.  That update will install all OpenOffice 3.0 updates.

Hope that helps.
[/I]

---

### Post by Cerny on 2008-12-02
I found this rather useful. Thanks

---

### Post by Skripka on 2008-12-02
> **anuban said:**
> Just add
[I]deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
*to the Software source -> Third party *Software

As soon as you add the above key, it should show you an update.  That update will install all OpenOffice 3.0 updates.

Hope that helps.
[/I]

The problem being, the PPA repos are still down, and _*have been for a week*_ (people keep posting the links to them though)...and there is rumour that there will not be any OOo3 rerelease for *buntu until Jaunty (9.04).


Currently the only way to get OOo3 is to REMOVE ALL of OOo2 from your system, and then download the BIG .deb archive from the OOorg website.


Once you have the big .deb archive, exxtract the contents....open a terminal and navigate to the folder containing all the debs and:

```

sudo dpkg -i *.deb

```

After that, there is still on more deb hiding in a subfolder you need to install.  And BAM-you have OOo3.  This is the ONLY way to get OOo3 on your *buntu system as of 11/25/2008 through the present.

---

### Post by barksten on 2008-12-03
Thanks for that information. I was going crazy. I knew I updated my 8.10 beta but I have not been able to update my current installation of ubuntu to OO 3.0. 
I have found a detailed guide in [this thread]("http://ubuntuforums.org/showthread.php?p=6300667#post6300667") that I will try.

---

### Post by Hydrohs on 2008-12-03
> **Skripka said:**
> The problem being, the PPA repos are still down, and _*have been for a week*_ (people keep posting the links to them though)...and there is rumour that there will not be any OOo3 rerelease for *buntu until Jaunty (9.04).


Currently the only way to get OOo3 is to REMOVE ALL of OOo2 from your system, and then download the BIG .deb archive from the OOorg website.


Once you have the big .deb archive, exxtract the contents....open a terminal and navigate to the folder containing all the debs and:

```

sudo dpkg -i *.deb

```

After that, there is still on more deb hiding in a subfolder you need to install.  And BAM-you have OOo3.  This is the ONLY way to get OOo3 on your *buntu system as of 11/25/2008 through the present.

What do you mean by navigate to the folder? O_o

I need detailed instructions, I'm coming from Windows, where everything is easier.

---

### Post by MeURi on 2008-12-03
The Windows command prompt works more or less like the terminal in Ubuntu.

Open up gnome-terminal, konsole, or the terminal emulator you use and do a ```
 cd <dir where you saved your files>
```

Note that the terminal is case-sensitive under linux. So, if you saved the archive on your desktop, and extracted the files in a dir called "debs_for_openoffice", you will have to do

[list]
[*] open the terminal from the menu
[*] issue a "cd Desktop/debs_for_openoffice" without the quotes
[*] issue a "sudo dpkg -i *.deb", always without the quotes
[/list]

And you're done

EDIT: as a side note, if you have software packaged for your distribution available through software repositories, Ubuntu is way easier than Windows; here the situation sounds tricky because you have to manually download the files and install them by hand; note that you can achieve the same exact result by double clicking on each deb package that comes out from the archive, and choosing to install it (in a very Windows-like way); issuing commands from the console is just quicker ;-)

---

### Post by mamous on 2008-12-04
Hi
you can go to this thread....
[http://ubuntuforums.org/showthread.php?t=1000861]("http://ubuntuforums.org/showthread.php?t=1000861")

---

### Post by mamous on 2008-12-04
Hi
you can go to this thread....
[http://ubuntuforums.org/showthread.php?t=1000861]("http://ubuntuforums.org/showthread.php?t=1000861")

---

