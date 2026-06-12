---
title: "Google Earth"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by ibates on 2010-06-03
Somebody - please remind me.

I have "installed" Google Earth from Synaptic and have a wonderful .deb package.

What do I have to do now to run it as an app?

Try as I might I cannot find any instructions anywhere and it is so long since I have done this, I simply can't remember how to go about it.

---

### Post by Rod J on 2010-06-03
So you have downloaded the installation file (.deb package) I take it? OK, now you have to install it. Easiest way is to run the GDebi package installer from System Tools in the main menu and open the GoogleEarth .deb file where you downloaded it. Or, in a terminal cd to the download location and type sudo dpkg --install <name of .deb file>.

---

### Post by ibates on 2010-06-03
Thanks for that Rod.

I have already tried the second option you suggest (dpkg) in the terminal.  Everything looks OK; there are no reported errors.

But that is the stone cold end of the process.  No executable file seems to have been created, and if there is, I cannot find it - by searching "File System".

I seem to recall last time I did this I simply ran the dpkg thing and an icon with the file name appeared in the Main Menu items.  But not this time.

I have probably forgotten some important step, although I can't imagine what that might be.

---

### Post by wojox on 2010-06-03
Did you add medibuntu [http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

---

### Post by realzippy on 2010-06-03
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install googleearth
```


does all you need (run in terminal)

---

### Post by John Bean on 2010-06-03
> **ibates said:**
> I have "installed" Google Earth from Synaptic and have a wonderful .deb package.

Not sure I understand this. If you install using Synaptic (or apt-get for that matter) there is no need to meddle with .deb files or anything else - it's all done for you, that's what APT is all about. In the case of Google Earth it also puts an entry in the main menu Applications->Internet->Google Earth, click on it and it runs :-)

---

### Post by wojox on 2010-06-03
There's also 

```

sudo apt-get install googleearth-package
make-googleearth-package --force
sudo dpkg -i googleearth*.deb

```

---

### Post by John Bean on 2010-06-03
> **wojox said:**
> There's also 

```

sudo apt-get install googleearth-package
make-googleearth-package --force
sudo dpkg -i googleearth*.deb

```

Sure, but googleearth-package is designed to make a Google Earth .deb not to *install* Google Earth.

I see why you point this out - and perhaps that's what the OP did - but if that's the case it's a lot simpler to just "sudo apt-get install googleearth" in the first place rather than make a .deb with googleearth-package then install it manually.

Waste of time and effort, and far too much typing ;-).

---

### Post by wojox on 2010-06-03
> **John Bean said:**
> Sure, but googleearth-package is designed to make a Google Earth .deb not to *install* Google Earth.

I see why you point this out - and perhaps that's what the OP did - but if that's the case it's a lot simpler to just "sudo apt-get install googleearth" in the first place rather than make a .deb with googleearth-package then install it manually.

Waste of time and effort, and far too much typing ;-).

It's not in the repo's

---

### Post by John Bean on 2010-06-03
> **wojox said:**
> It's not in the repo's

It's in medibuntu, as others (including you) have pointed out.

---

### Post by ibates on 2010-06-20
Thank you for all the above replies.  I finally got Google Earth "installed".

By that, I mean with many, many, errors during the installation process and with reports of broken packages during a subsequent update.

But now the REAL problem has returned.  At least one thing is established, and that is the reason for all the random system hangs in the past few months.

Sytem hangs have re-appeared.

Subsequent to installing GoogleEarth, I had a "clean" 10.04 installation.  No problems - no hangs.  But after installing Google Earth, the system hangs frequently.  Very frustrating indeed.  And the only way I can recover from the hang is to power down (hard power off) and start again.  It is a real hang.

Of course, there were plenty of warnings during the Google Earth installation process which said "I was on my own" and I am thus aware of that risk.  But now I want to get this cursed application out of the system.

I would be most appreciative for any advice as to how to uninstall Google Earth, and to clean up the system.

---

### Post by ibates on 2010-06-21
I seem to have removed Google Earth OK.  Problem seems to have disappeared - for the moment at least.

Thanks for assistance.

---

### Post by Rod J on 2010-06-21
If you want to reinstall it ... first install "Medibuntu". I think without that you can't install Google Earth (or if you manage to you might end up with the problems you've been having). There is another package (confusingly called "googleearth-package") which doesn't install Google Earth but creates a .deb file that can then be installed (I think?). Maybe that was what you did at first. Anyway, install Medibuntu first and you should then be able to install Google Earth via the Synaptic repository.

---

### Post by ibates on 2010-06-25
I have installed medibuntu as a software source as shown here, but despite successful downloading and installing of Google Earth via Synaptic, it simply will not run.

Clicking on the main menu icon (under Internet), I see the Google Earth opening screen (small) then simply get a white page.  Nothing I do will result in anything more.

If I quit (using the red x) I will then not be able to get any reaction from selecting Google Earth again.

I have executed a complete uninstall and even that left an unusual icon and Google Earth bar in the main menu, but one which yields nothing when clicked.  This weird menu item has also been deleted.

Is there any way I can specifically purge all or any  possible  Google Earth components which may be remaining in the system?  (When installing, the installation dialogue indicates 71.something Mb to be installed, and after uninstalling, it reports that 71.something Mb are being removed).

Assistance is requested.

---

### Post by oldos2er on 2010-06-25
> **ibates said:**
> Clicking on the main menu icon (under Internet), I see the Google Earth opening screen (small) then simply get a white page.  Nothing I do will result in anything more.

That sounds like a video driver problem. What video card do you have, and have you checked System, Administration, Hardware Drivers to see if proprietary drivers are available for it?

---

### Post by ibates on 2010-06-27
Graphics Card: ATI Radeon HD 5400 Series (Marketed as ASUS EAH5450 Silent

The following is Ubuntu System Information:

Hardware:
    BIOS
        Date                             01/19/2010 02:36
        Version                          012.019.000.002.035918
        Part Number                      113-AC59900-100
    Memory
        Type                             DDR2
        Clock                            400 MHz
        Size                             512 MB
        Bandwidth                        6.4 GBytes/s
    BUS
        Graphics Capability              PCI Express 2.0
        Maximum Setting                  x16
    Core Clock                           650 MHz
Software
    Driver Packaging Version             8.723.1-100408a-098580C-ATI
    2D Driver Version                    8.72.11
    Catalyst(TM) Control Center Version  2.12
    RandR Version                        1.3
Open GL
    Open GL Provider                     ATI Technologies Inc.
    OpenGL Renderer                      ATI Radeon HD 5400 Series
    OpenGL Version                       3.2.9756 Compatibility Profile Context

Hopefully this sheds some light on the problem.  Please let me know if you need more info.

---

### Post by mnsxpress on 2010-06-28
> **John Bean said:**
> Sure, but googleearth-package is designed to make a Google Earth .deb not to *install* Google Earth.

I see why you point this out - and perhaps that's what the OP did - but if that's the case it's a lot simpler to just "sudo apt-get install googleearth" in the first place rather than make a .deb with googleearth-package then install it manually.

Waste of time and effort, and far too much typing ;-).



















nazmus@nazmus-desktop ~ $ sudo dpkg -i googleearth*.deb
[sudo] password for nazmus: 
Sorry, try again.
[sudo] password for nazmus: 
Selecting previously deselected package googleearth.
(Reading database ... 114847 files and directories currently installed.)
Unpacking googleearth (from googleearth_5.2.1.1329+0.5.7-1_i386.deb) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on ttf-dejavu | ttf-bitstream-vera | msttcorefonts; however:
  Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package msttcorefonts is not installed.
dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 googleearth
nazmus@nazmus-desktop ~ $ 

WHAT I HAVE GOT IS THIS :     





NOW WHAT I HAVE TO DO ?

---

### Post by oldos2er on 2010-06-28
> **ibates said:**
> Graphics Card: ATI Radeon HD 5400 Series (Marketed as ASUS EAH5450 Silent

    2D Driver Version                    8.72.11
  

Googleearth requires 3D graphics. Check System, Administration, Hardware Drivers to see if there are any proprietary video drivers available for your video card.

---

### Post by ibates on 2010-06-28
Further to my reply above; yes I have downloaded the recommended drivers for this card and they are installed.

Subsequently I have once again "removed" Google Earth from the system and then run the sommand sudo apt-get install googleearth.

Everything installs perfectly, but no icon in the Applications->Internet main menu.

Selecting the application independently starts Google Earth (I get the "Google Earth" small screen, but then the display goes all white and that's all that happens.

If I click on the red x to close the program it asks if I want to execute a "force quit".  On answering "Force Quit", Google Earth disappears from the window.

BUT!  if i then attempt to run it again, nothing at all happens.

A check of the system monitor at this time reveals that the googlearth.bin process is still installed, but is sleeping.  It can only be removed by ending the process.

All this indicates that it is more than the graphics card (which I believe is working just fine).

Any further thoughts?

---

### Post by oldos2er on 2010-06-28
All I know is googleearth needs 3d drivers. If you already have the fglrx drivers installed, I don't really know what more to suggest (I've only used Nvidia cards on Linux). Maybe search for others running fglrx and googleearth? Sorry I couldn't help you.

---

### Post by ibates on 2010-06-28
I don't know why the information data included nothing about 3D specifically, but the hardware drive downloaded and installed is ATI/AMD proprietary FGLRX Graphics Drive which includes a "3D-accelerated proprietary graphics driver for ATI cards."

Further the notes on the driver state "This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards".

The notes further state that this driver has been tested by "The Ubuntu developers".

Further, the configuration for the card contains a whole section on configuring for 3D, all of which are set and active.

As I said above, I am still confused aboout the improper terminating of the app.  There seems to be something else going on here.

---

### Post by ibates on 2010-06-28
A bloody good try anyway, which I must say is a bit unusual for this forum.

Keep it coming - it is most appreciated.

---

### Post by Rod J on 2010-06-29
> **mnsxpress said:**
> nazmus@nazmus-desktop ~ $ sudo dpkg -i googleearth*.deb
[sudo] password for nazmus: 
Sorry, try again.
[sudo] password for nazmus: 
Selecting previously deselected package googleearth.
(Reading database ... 114847 files and directories currently installed.)
Unpacking googleearth (from googleearth_5.2.1.1329+0.5.7-1_i386.deb) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on ttf-dejavu | ttf-bitstream-vera | **msttcorefonts**; however:
  Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package **msttcorefonts** is not installed.
dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 googleearth
nazmus@nazmus-desktop ~ $ 

WHAT I HAVE GOT IS THIS :     





NOW WHAT I HAVE TO DO ?

It's pretty obvious what you need to do, isn't it? You need to install the **msttcorefonts** package from the repository :p

---

### Post by ibates on 2010-06-29
Slowly but surely all has been resolved.

It WAS the graphics card.

The brand new "high performance" ATI/Radeon video card referred to above was a total dog.  It couldn't even handle slowish graphics requirements.

I have subsequently got rid of it and installed a MSI GeForce GT240, 1 GB, DDR3 with fan, HDMI, DVI, D-Sub.  Problems have all disappeared.  Google Earth loads and runs at a zillion miles per hour with no other changes (after downloading and installing the nVidia drivers of course).

Thank you everyone for your attempts to fix a problem which was not really a problem other than a totally inadequate video card.  (Performance was checked on a Windows XP computer as well.  Snail's pace.  So remember that when next purchasing a video card).

---

### Post by Rod J on 2010-06-29
Great! Glad you got it sorted ... though I would have thought the ATI/Radeon card would have been up to it as it's a recent model.

---

