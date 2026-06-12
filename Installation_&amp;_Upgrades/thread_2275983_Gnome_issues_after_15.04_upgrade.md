---
title: "Gnome issues after 15.04 upgrade"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by egruber on 2015-04-29
Last week I was on 14.04 using Gnome.  I upgraded to 14.10 and immediately to 15.04.  After the upgrade, I noticed the following issues with Gnome.  I use Gnome Flashback...I didn't like the newer look.

All of these worked fine while on 14.04.  But all of these work fine with Unity.  Any ideas?

1. The All Settings Menu has two printer icons (see attached)
2. Some of the selections in All Settings come up with transparent windows when clicked (see attached).
3. My dropbox icon no longer appears in my status panel.  But it is there in Unity.

---

### Post by dino99 on 2015-04-29
its hard to get a multi dist-upgrades without some weird sad effects ;)
take time to clean the system: clean, autoclean, autoremove, gtkorphan
and also glance at /etc/rc?.d for possible broken links (which can be safely removed)
and using journalctl can also point out some usefull errors

---

### Post by egruber on 2015-04-29
Thanks for the tips...but I'm not that great with the linux lingo.  Can you provide the steps to do the things you suggested and I'll give them a try?  And I forgot to mention that when I checked for software upgrades, it told me I had to do a partial upgrade...which I did.  It didn't change things, though.

---

### Post by muktupavels on 2015-04-30
To fix missing dropbox icon copy /usr/share/applications/dropbox.desktop to ~/.local/share/applications/dropbox.desktop and open it for editing. Then change Exec line to this:
```
Exec=env XDG_CURRENT_DESKTOP=Unity dropbox start -i
```

---

### Post by egruber on 2015-04-30
I only found that file in my .config/autostart and not in the usr/share/applications directory.  I did copy it to where you said, but it won't let me open it for editing.  It says 'untrusted application launcher'.  Weird.

---

### Post by muktupavels on 2015-04-30
Then you probably did not need copy and you can delete that copy.

Open Text Editor and use File -> Open. This way you will be able to open ./config/autostart/dropbox.desktop file.

---

### Post by egruber on 2015-04-30
I couldn't open it there because I think Text Editor cannot work with hidden files. So, I copied it to the desktop, edited it and then saved it back to the autostart directory.  I logged out and in and it worked fine, but when I restarted, the file in autostart reverted back to the previous version without my changes.  Weird again.

---

### Post by egruber on 2015-04-30
I think the problem is that in older versions of ubuntu, I could edit those files as root...but I can't with the current version.  i have a root ID and password set up, but whenever I try to edit and save any of these system files, it reverts back to the old version the next time I boot.  I have been searching the forums, but everything I try gives me errors.

---

### Post by deadflowr on 2015-05-01
> **egruber said:**
> I couldn't open it there because I think Text Editor cannot work with hidden files..
No, they can.
In gedit, click on Open and in the main window area that lists the files right click on select the option Show Hidden Files.
I think this behavior is similar across various text editors.
I know kate also has this option, though I think it is in a different place...

---

### Post by wildmanne39 on 2015-05-01
I would reformat the ubuntu partition and do a fresh install if you do not have much on your computer or do a back up first. Upgrades can go wrong from time to time,but given you did a partial upgrade you almost assuredly corrupted your system because a partial upgrade should be avoided at all costs. Usually there is a temporary issue with the server or repository or something like that and will be resolved shortly so you should always wait and not do a partial upgrade.

---

### Post by egruber on 2015-05-01
> **deadflowr said:**
> No, they can.
In gedit, click on Open and in the main window area that lists the files right click on select the option Show Hidden Files.
I think this behavior is similar across various text editors.
I know kate also has this option, though I think it is in a different place...

Thanks for the gedit tip!  I didn't know you could right-click and see hidden files.  So now I can edit the file.  

That being said, here is the weird part.  I edit the file, make the changes and save it.  I check the saved file and it is correct.  I logout and log back in, check the file...and it has reverted to the old version!  Any idea what is happening here?

---

### Post by muktupavels on 2015-05-05
Well it looks like you need to edit two files:
1. Stop dropbox.
2. Change Exec line in /usr/share/applications/dropbox.desktop
3. Change Exec line in ~/.config/autostart/dropbox.desktop

---

### Post by egruber on 2015-05-05
> **albertsmuktupavels said:**
> Well it looks like you need to edit two files:
1. Stop dropbox.
2. Change Exec line in /usr/share/applications/dropbox.desktop
3. Change Exec line in ~/.config/autostart/dropbox.desktop

I only have one dropbox.desktop file and it's in the autostart directory you reference.  I don't have the other one.  Do I need to place one there?

---

### Post by muktupavels on 2015-05-05
How did you install dropbox? Then maybe you have extra file under ~/.local/share/applications/?

---

### Post by egruber on 2015-05-05
There are no dropbox files in the .local location you specified.  Mostly files for chrome.

Dropbox was already installed a long time ago before I moved to 15.04 and I don't recall if I got it from the ubuntu software store or the dropbox site.  But after I upgraded and had this problem, I downloaded the deb file dropbox_2015_2.12_i386 from the dropbox site and installed that.  Dropbox is running because the folder is there and it does sync.  I just don't have the panel icon.

---

### Post by muktupavels on 2015-05-05
You can try to copy that file. Edit that Exec line then copy file:
sudo cp ~/.config/autostart/dropbox.desktop /usr/share/applications/dropbox.desktop

I tried in virtualbox. File was reverted for me too, but it stopped when I edited second file.

---

### Post by egruber on 2015-05-05
That worked!  Though I don't understand why and if you have a brief explanation I would like to hear it.  

I tried to copy and paste the edited file into the applications directory, but I didn't see it.  I then used the cp command you provided.  It didn't give any error, but I still don't see it in that directory.  But the icon now works.  Thanks so much for sticking with this.  :p:p

---

### Post by muktupavels on 2015-05-05
Now that you say that you don't see file I would say that you had dropbox.desktop file in /usr/share/applications. Why it works? Probably some application is comparing files and if they are not equal then it "restores" it to original state. That is my guess, I don't know.

---

### Post by egruber on 2015-05-05
If I browse that directory from Places, I only see icons and not file names.  There is only one dropbox icon in there and no other dropbox files.  If I open gedit and navigate to that directory, I see file names...not icons...and the dropbox.desktop file is there.  I guess that file is shown as the dropbox icon.  but it doesn't appear that way in other directories...and if I use the file search it doesn't come up.  When I copied the edited file, I didn't get a file replacement warning, either.  Weird, huh?  Again...thanks for all the help.  You were great.

---

### Post by muktupavels on 2015-05-05
That directory shows application name instead of filename. If file exists cp will overwrite it.

---

### Post by RobertoRecordo on 2015-08-27
I installed Ubuntu-Gnome 15.04 amd64
I read the release notes before installing, so the blank screen when I first stated Ubuntu was no surprise, and the second boot started with no apparent problems.

Good News / Surprise: I was running 12.10, and wanted to do a clean install I repartitioned my drive and moved my 2 home folders (2 users on this computer) to remote partitions. The installer found them, and they are both available in the file system.

[SIZE=3]**What is not working**[/SIZE]: I have a local printer that I share with other computers on my LAN. I can not find the GNOME equivalent of the printer server dialogue that is in other versions.

added 29 August 2015
The printer problem may or may not be a UBUNTU GNOME problem. Ubuntu 12.04 had a button in the printer dialogue that allowed sharing a printer, but I have forgotten what I had done in November 2012 when I first installed a shared printer on this computer. 
[URL="http://ubuntuforums.org/showthread.php?t=2292405"]http://ubuntuforums.org/showthread.php?t=2292405
[/URL]has the details or how I got my printer online.



[SIZE=3][B]
I can not find a way to start the server!

-Rob
[/B][/SIZE]

---

