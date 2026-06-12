---
title: "Attention!!! Jaunty Jackalope Alpha 3 - Known Issues !!"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Gourgi on 2009-01-16
> **Known Issues**

As is to be expected at this stage of the release process, there are several known bugs that users are likely to run into with Jaunty Alpha 3. We have documented them here for your convenience along with any known workarounds, so that you don't need to spend time reporting these bugs again:
[LIST]
    [*] A new XServer, version 1.6, is included in Alpha 3. The binary proprietary drivers -fglrx and -nvidia are not yet supported for this server and will exhibit various serious issues if run against it. Users of these drivers are encouraged to wait or to switch to the corresponding open source drivers 4(-ati and -nv respectively) in the meantime. Bug : [[COLOR="Red"]308410[/COLOR]]("https://bugs.launchpad.net/bugs/308410")
    [*] While the user-space component of the EXPERIMENTAL nouveau X driver is available in Alpha 2 universe, the kernel modules this driver requires to work are not yet available. The kernel modules should be uploaded soon after Alpha 2.
    [*] Users of Intel i845 or i865 video chipsets are unable to load X, getting an error message of "Fatal server error: Couldn't bind memory for BO front buffer". Users on these systems are advised to wait for a resolution to this bug before upgrading. Bug : [[COLOR="Red"]304871[/COLOR]]("https://bugs.launchpad.net/bugs/304871")
    [*] The OEM mode on Kubuntu images fails after reboot in Jaunty Alpha 3. Investigation of this issue is ongoing. Bug : [[COLOR="Red"]309482[/COLOR]]("https://bugs.launchpad.net/bugs/309482")
    
    [*] Choosing the "use a password to log in and decrypt my home directory" option on the desktop CD will result in an installation failure. As a workaround, avoid using this option for the time being. Bug : [[COLOR="Red"]317068[/COLOR]]("https://bugs.launchpad.net/bugs/317068")
    
    [*] The amarok package has been updated to Amarok 2 for Alpha 3. Amarok 2 uses the mysql 5.1 embedded database for collection storage. These packages are not included on any Alpha 3 CD, but may be installed from the Ubuntu repository. For users of Kmail/Kontact, parts of the mysql 5.1 package conflict with parts of mysql 5.0 used by Akonadi, the Kmail/Kontact mail store. Amarok and Akonadi cannot be installed at the same time, so it is not currently possible to use both Kmail/Kontact and Amarok at the same time. Improvements in the packaging are in progress and this will be resolved in a later Alpha release.
    
    [*] Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it via the [[COLOR="Red"]DontZap[/COLOR]]("https://wiki.ubuntu.com/DontZap") option in xorg.conf. A GUI tool to simplify setting xorg.conf options is under development and will be available in a later Alpha release.
[/LIST]


i though it worth posting this here.
maybe sticking it would be better, it could save people's time.

Get Jaunty Alpha 3 while it's hot !!!
[http://www.ubuntu.com/testing/jaunty/alpha3](http://www.ubuntu.com/testing/jaunty/alpha3)

---

### Post by Starks on 2009-01-16
Xorg.conf is getting a gui? Is that the fabled xkit?

---

### Post by WelshDragon on 2009-01-16
> **Starks said:**
> Xorg.conf is getting a gui? Is that the fabled xkit?

Blueprint: [https://blueprints.launchpad.net/ubuntu/+spec/xorg-options-editor](https://blueprints.launchpad.net/ubuntu/+spec/xorg-options-editor)
Wiki: [http://wiki.ubuntu.com/X/OptionsEditor](http://wiki.ubuntu.com/X/OptionsEditor)

:)

---

