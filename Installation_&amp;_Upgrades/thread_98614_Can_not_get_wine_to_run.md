---
title: "Can not get wine to run"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by ok67 on 2005-12-03
I have installed wine, but can not get it to run.
Running wine gives me the following:
oddgeir@papsi:/$ wine
wine: creating configuration directory '/home/oddgeir/.wine'...
/usr/bin/wineprefixcreate: line 173:  3878 Segmentation fault      "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
wine: wineprefixcreate failed while creating '/home/oddgeir/.wine'.
oddgeir@papsi:/$ wineserver: could not save registry branch to /home/oddgeir/.wine-5QoVua/system.reg : No such file or directory
wineserver: could not save registry branch to /home/oddgeir/.wine-5QoVua/user.reg : No such file or directory

winecfg gives much the same:
oddgeir@papsi:/$ winecfg
wine: creating configuration directory '/home/oddgeir/.wine'...
/usr/bin/wineprefixcreate: line 173:  3952 Segmentation fault      "${WINELOADER :-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.in f
wine: wineprefixcreate failed while creating '/home/oddgeir/.wine'.
oddgeir@papsi:/$ wineserver: could not save registry branch to /home/oddgeir/.wi ne-G5CubQ/system.reg : No such file or directory
wineserver: could not save registry branch to /home/oddgeir/.wine-G5CubQ/user.re g : No such file or directory


ny sugestions of how to get wine running
I have even downloaded the source and compiled it, with the similar results.

Do I need windows on my computer to use wine ?

---

### Post by dcstar on 2005-12-03
[QUOTE=ok67]I have installed wine, but can not get it to run.
......
ny sugestions of how to get wine running
I have even downloaded the source and compiled it, with the similar results.

Do I need windows on my computer to use wine ?[/QUOTE]
Rename the hidden .wine directory in your home directory, and try again.

Also, open a user terminal and run "winecfg"

---

### Post by ok67 on 2005-12-03
The problem is that neither wine nor winecfg generate any .wine directory in my home directory. And yes I have write acces to my home folder.

---

### Post by aysiu on 2005-12-03
How did you install Wine--via Synaptic or from source?
If you run the Wine command the way you appeared to have, this is what should have happened: ```
wine
Wine 0.9.1
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
``` And, no, you don't need Windows installed, but Wine doesn't run independently of a .exe file. It's a helper application that helps you launch a Windows executable file.

For example, to run Filezilla, I don't run the command ```
wine
``` I run the command ```
wine "z:\home\username\.wine\drive_c\Program Files\Filezilla\Filezilla.exe"
``` If you didn't install Wine with apt-get or Synaptic, I'd advise doing so--it's far easier. See both links in my sig for more details.

---

### Post by ok67 on 2005-12-03
I installed it using synaptic. I have tried both the version from ubuntu, and also from winehq. Same results.

---

### Post by aysiu on 2005-12-03
Do you get those same errors if you use a different user to run Wine? What about if you run Wine as root (or sudo)?

---

### Post by ok67 on 2005-12-04
I have the same errors with a different user, and also with root.

I am using my own compiled kernel 2.6.14.3 optimised for Athlon, can that cause this problem?
I am also using the nvidia display drivers.

---

### Post by ok67 on 2005-12-04
[QUOTE=ok67]I have the same errors with a different user, and also with root.

I am using my own compiled kernel 2.6.14.3 optimised for Athlon, can that cause this problem?
I am also using the nvidia display drivers.[/QUOTE]

To rule out this posibility I booted to a standard 386 kernel supplied with Ubuntu and used the nv driver instead of the nvidia driver. But with the same results as before.

My installation is new, just a few days old, since I replaced a shaky harddrive where I have been running Slackware for manny years. Installed Ubuntu this time (with no problems). But I have never tried to run Wine before.

---

### Post by ok67 on 2005-12-05
I also tried to install version 0.9.1 from sources, but stil the same error. Segmentation fault when trying to generate the .wine directory.

---

### Post by ok67 on 2005-12-05
Stil testing some more.

By running winetools O get the following message:

Gtk-WARNING **: Unable to locate loadable module in module_path: "libredmond95.so",

How do I add: /usr/lib/gtk-2.0/2.4.0/engines
to module_path, since this is where the requested library is located.

Making ld.so.conf and add it there did not do it.

---

### Post by dcstar on 2005-12-05
[QUOTE=ok67]Stil testing some more.

By running winetools O get the following message:

Gtk-WARNING **: Unable to locate loadable module in module_path: "libredmond95.so",
.......[/QUOTE]
Set your desktop Theme back to the Ubuntu default one, then the winetools stuff runs without complaining.

---

### Post by CPUFreak91 on 2005-12-05
[QUOTE=ok67]Do I need windows on my computer to use wine ?[/QUOTE]

Sorry, can't be much help, but, no wine will never need windows to be installed.

---

### Post by ok67 on 2005-12-06
[QUOTE=dcstar]Set your desktop Theme back to the Ubuntu default one, then the winetools stuff runs without complaining.[/QUOTE]

I made a separate user and logged in. This user is using the default Theme. The GTK Warning message is gone, but the other problems are stil there. I beleive I am about to give upp on Wine:(

---

### Post by ok67 on 2005-12-07
I have installe an old version of Wine "wine_0.0.20050310-1.1_i386.deb" Including wine lib of the same version etc. This version is able to generate the .wine director. But every Windows program I try to run crashes with:

Wine failed with return code 139
Segmentation fault

---

### Post by linbetwin on 2005-12-07
I installed wine through Automatix and it works. You just have to run **winecfg** in a terminal after you install wine.

---

### Post by ok67 on 2005-12-07
Must be some other packages & librarys that I have installed that are causing me problem......... But my installation of Ubuntu is only a few days old.....

---

### Post by YokoZar on 2005-12-08
[QUOTE=ok67]Must be some other packages & librarys that I have installed that are causing me problem......... But my installation of Ubuntu is only a few days old.....[/QUOTE]
From the errors you're getting, it sounds like you're missing a dependency somewhere.

Assuming you didn't force install the package, did you compile anything else from source?  Libraries, etc?

---

### Post by YokoZar on 2005-12-08
[QUOTE=ok67]To rule out this posibility I booted to a standard 386 kernel supplied with Ubuntu and used the nv driver instead of the nvidia driver. But with the same results as before.[/quote]Do this in general, compiling your own kernel is a good way to break things.  There are optimized Athlon kernels downloadable in Synaptic anyway.

Now, when you say you "used the nv driver", did you configure it as you would in Slackware (altering x.org's config file), or as one would do in Ubuntu?  The best way to enable/disable the nvidia driver is to do it the way the restricted nvidia package tells you, by running dpkg-reconfigure.

You are using the nvidia package, right?

---

### Post by YokoZar on 2005-12-08
[QUOTE=ok67]Stil testing some more.

By running winetools O get the following message:

Gtk-WARNING **: Unable to locate loadable module in module_path: "libredmond95.so",

How do I add: /usr/lib/gtk-2.0/2.4.0/engines
to module_path, since this is where the requested library is located.

Making ld.so.conf and add it there did not do it.[/QUOTE]This should have happened automatically when the package installing the library was installed.

In general, don't modify files by hand, especially system files like ld.so.conf. The package manager should do all that for you when you install new libraries.

---

### Post by ok67 on 2005-12-08
I am stil somewhat to much used to the Slackware way of doing things. Yes I compiled my own kernel and downloaded the drivers from nvidia and installed the that way, not the "Ubuntu way". This might be the problem. I have a closer look at it tonight.

---

### Post by ok67 on 2005-12-08
Reinstalling Ubunto seems to have solved the problem. But I had to do the reinstall two times. The first time ended in a Grub error 18......

---

