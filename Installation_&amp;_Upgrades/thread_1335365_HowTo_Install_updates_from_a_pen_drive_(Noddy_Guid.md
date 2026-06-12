---
title: "HowTo: Install updates from a pen drive (Noddy Guide)"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Kevbert on 2009-11-23
I'm running several copies of the same kernel of Ubuntu on the same machine (such as 9.04) and used to update each kernel separately. This meant that I downloaded the same files several times. The method detailed below will also work on near identical computers where internet access is only available on one computer.
When installed, Debian packages (.deb) are normally stored in the /var/cache/apt/archive/directory, so firstly we want to empty this directory ready to install our new updates via Accessories-Terminal with the command
```
sudo aptitude clean
```
Now using Nautilus filemanager browse to this directory to make sure it is empty (apart from a Lock file). This can be done via the Places-Computer menu item. Now click on Filesystem - var - cache - apt - archive.
In Terminal enter
```
sudo aptitude update
sudo aptitude safe-upgrade
```
The first command updates the package list and the second installs all updates.
Nautilus will show a number of new .deb files in the /var/cache/apt/archive directory. These are the files we need to copy to the removable pen drive.
Plug in the pen drive, a new Nautilus window will open for the pen drive. Right-click on any empty space in this window so that a menu appears and select 'Create Folder' enter Packages.
Double-click on the Packages Folder to open it. Now you should have two Nautilus windows open (one for /var/cache/apt/archive, the other for /Packages). Select the new .deb files you've just downloaded by left- clicking on the first file, then hold down the Ctrl key and click on the other .deb files, so that all files are highlighted. Now right-click on the last file and select 'Copy' from the menu that appears. Release the Ctrl key.
Now go to the empty Packages window and right-click any empty space select 'Paste' from the popup menu.
Press Ctrl-W twice to close the Nautilus windows.
On the desktop will be displayed an icon for the pen drive (something like xxGb Media). Right-click on this icon and select 'Unmount Volume'. Once this icon has disappeared you can safely remove the pen drive.
Now connect the pen drive in the other PC (in my case I have to reboot first). A Nautilus window will display the contents of the drive including the /Packages directory. Open a new Nautilus window for the /home directory of the PC (via Places-Home Folder). Right-click on the pen drive /Packages directory and select 'Copy'. Right-click on any empty space in the /home directory window and select 'Paste' so that the /home directory has a new /Packages directory in it.
Open a terminal (via Accessories-Terminal) and enter the commands
```
cd Packages
sudo dpkg -i *.deb
```
The second command will check that all dependency (support) files are available and install all the updates in the /Packages directory.

---

