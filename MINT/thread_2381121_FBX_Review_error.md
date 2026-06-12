---
title: "FBX Review error"
date: 2017-12-27
forum: MINT
---

### Post by miguelangel.ae on 2017-12-27
Hi guys

I have a big problem, help please :)

- I have installed wine1.8 via ppa
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main (sources)

My computer:
########################################
miguelangel@HP-ENVY-15-LMM-A
----------------------------
OS: Linux Mint 18.2 Sonya x86_64
Host: HP ENVY 15 Notebook PC
Kernel: 4.8.0-53-generic
Uptime: 14 hours, 16 mins
Packages: 2560
Shell: bash 4.3.48
Resolution: 1920x1080
DE: MATE
WM: Metacity (Marco)
WM Theme: Mint-X
Theme: Mint-X [GTK2/3]
Icons: Mint-X [GTK2/3]
Terminal: mate-terminal
Terminal Font: Monospace 10
CPU: Intel i7-4712HQ (8) @ 3.300GHz
GPU: Intel Integrated Graphics
GPU: NVIDIA GeForce GTX 850M
Memory: 5916MiB / 11946MiB
########################################

- And i have installed winetricks and playonlinux from the official repositories.

- With winetricks i download vcrun2012 ("Visual C++ 2012 libraries (atl110, mcfc110, mfc110u, msvcp110, msvcr110, vcomp11)" from Microsoft dll to run FBX Review, i think with that the program runs but not runs.
- Ok, i will tell you an information, when i try to install after the installation of vcrun2012 a window appears and show this "Working around wine bug 17273 - Manually extracting dlls"
How i can solve this? but, the dll has been installed "correctly" and i can see it in the dll panels of winetricks.
- All looks good, but when i run the exe via using command "wine explorer" and run FBX Review from this command i can see this output:

## wine explorer (terminal)

[http://pasteall.org/737046/](http://pasteall.org/737046/)

- And i run this command wine '/home/miguelangel/.wine/drive_c/Program Files (x86)/Autodesk/FBX Review/fbxreview.exe' 

- Nothings happen and i have a big error
- This is the output of the terminal:

## wine '/home/miguelangel/.wine/drive_c/Program Files (x86)/Autodesk/FBX Review/fbxreview.exe' (terminal)

[http://pasteall.org/737050/](http://pasteall.org/737050/)

Here, you can see and download the files:
[https://www.dropbox.com/sh/in8db2975dvyxyd/AABVyDkWjoroc02naCqrLHQFa?dl=0](https://www.dropbox.com/sh/in8db2975dvyxyd/AABVyDkWjoroc02naCqrLHQFa?dl=0)

Thanks


[COLOR=inherit !important][FONT=X-LocaleSpecific]


[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-12-27
*Thread moved to **MINT**.*

---

