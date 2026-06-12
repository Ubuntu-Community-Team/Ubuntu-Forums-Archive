---
title: "Trouble installing Input-Remapper 2.0.1"
date: 2024-08-28
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2024-08-28
I installed Input-Remapper 1.4.0-1, but later realized I probably need the latest version 2.0.1.  No big problem.  I found no PPA for it, but there is a deb file.  In Kubuntu's GUI, I have two choices: 
QApt Package Installer
Software Install

I first used Muon Package Manager to "purge" the old version, which appeared to work.  

So then I tried to install version 2.0.1 via its deb file with QApt Package Installer.  That did not work, and QApt didn't even tell me that it failed or why.  So I tried with Software Install.  That also failed, but at least it told me why.  It complained that it could not overwrite a directory named inputremapper, which contained python files.  I then tried from the command line as follows: 

```
sudo dpkg -i input-remapper-2.0.1.deb
```

Still no luck.  I got this error message: 

```
Error trying to overwrite '/usr/lib/python3/dist-packages/inputremapper/__init__.py', which is also in package python3-inputremapper 1.4.0-1
```

So I figured it was a file permissions problem, and I would up the file permissions on the inputremapper with chmod, as follows: 

```
sudo chmod -R 777 inputremapper
```

That ran without error.  However, upon running the same "sudo dpkg ..." command, I got the same error message.  So I ran Krusader as root, trying to rename that inputremapper directory, and that would act the same as deleting it and saving a backup.  Nope!  An attempt to rename it gets me an "access denied" message.  I don't get it.  the chmod command let me elevate everything to the highest permissions level.  I also don't get why the Muon Package Manager's "purge" command let that behind.  

It's driving me nuts.  I have the deb file, which usually makes installing something a cinch.  I also don't know why I still can't do whatever I want with that directory after chmod let me elevate the permissions all the way.  I've also looked for a Flatpak install file for the newest Input Remapper, but had no luck.  The Flatpak repository page says it's unable to package this type of app.  

I'm stuck.  Why won't it just let me install this deb file?  And why does the system deny me access to modifying, renaming, or moving that inputremapper directory.  If anyone has any insight on how I can make this work, I would appreciate any advice.  Thanks.

Edit/Update: 
I found a solution.  There's a command that forces an overwrite.  Warning: According to the places I found this, this method could possibly trash other applications that have the same dependencies, so use with caution.  What I did was I used the Timeshift app to back up my system first.  That way, I could revert to how things were before if I ran into any problems.  I did this: 
1. Back up with Timeshift
2. sudo dpkg -i --force-overwrite input-remapper-2.0.1.deb
3. Test run other applications that use Python.  Found no problems.

---

