---
title: "Cant run (or delete new programs)"
date: 2018-11-07
forum: Installation &amp; Upgrades
---

### Post by aiden007700 on 2018-11-07
[COLOR=#242729][FONT=Arial]I installed Ubuntu 18.4 on my new device a few days ago and everything went fine. The first thing I installed was VScode (using Ubuntu software). The app installed and I was even able to find it in finder, but when I opened it my screen flashed black and I saw multiple"@@@@" symbols in the upper left hand of the corner of the scene. The flash lasts just a fraction of a second and it takes me to the Ubuntu login screen, after signing back in all my apps that where running are closed. I uninstalled & reinstalled it a few times but the same result occurred each time. I figured that the version of vscode on the Ubuntu software app is bugged. I download it directly from Microsoft on the vscode website, and it worked fine, no more problems.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Today I decided to install mainspring from the Ubuntu software app, but it did not open, I uninstall and reinstall it a few times same result, however attempting to open mainspring did not crash my current session.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]At this point, I see its the same thing that happened with vs code so I install Spotify and Skype to see if they will open. Same behavior, however, Skype actually crashes my session just like vscode did and I see the multiple"@@@@" symbols in the upper left hand of the corner of the scene.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I figured that I will install mainspring using the command line, and just like before the app won't start. Since I did not install it with the Ubuntu software app it doesn't show up there for uninstall so I attempted to run both sudo apt-get remove mailspring and sudo apt-get purge mailspringhowever, the response is the following:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]aiden@aiden-XPS-15-9570:~$ sudo apt-get remove mailspringReading package lists... DoneBuilding dependency tree
Reading state information... DoneE: Unable to locate package mailspring[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The icon does show up when I search for mainspring, but it won't open. It looks like I can't run any apps installed with the command line or Ubuntu software app. All the apps that do run on my system now came preinstalled, or I downloaded them from their company site (chrome, gitkracken, vscode).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm running Ubuntu 18.04.01, and the device is dell XPS 9570.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What can I do to resolve the issue? Other then this huge problem everything works fine, but I need to be able to install programs using the software app/terminal.[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-11-07
I wonder if you are installing and using (or trying to use) snap packages rather than the more normal .deb packages.
What does ```
snap list
``` in terminal show you?

I do not use, and never have used, the Ubuntu software application; if I want a GUI, I always use synaptic, but normally the command line **sudo apt install package-name** does it all and also give you a lot of info while installing, which GUIs don't.

Try starting one of your problem applications using the terminal as that will usually show errors if there is a problem.

---

