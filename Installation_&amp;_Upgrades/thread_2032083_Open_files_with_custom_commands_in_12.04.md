---
title: "Open files with custom commands in 12.04"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by Duveltje on 2012-07-23
Hi

As an astronomer, I frequently use ds9 to open .fits files. Ds9 comes in a bin file and I but it in the home/username/bin folder, which is added to my .profile file. I can open .fits files with ds9 via terminal commands, and the program runs fine.

However, when I double click on a .fits file, I can't open it with ds9 because it doesn't appear in the 'open with' applications list.

How do I add custom bin apps to this list?

Thanks!
D.

---

### Post by dino99 on 2012-07-23
.bin is a special piece of the system, and it is not a good idea to set an app to be the default, it will disturb and confuse the system.

so either you continue using the terminal or you might rename that .bin differently, then you will be able to set a "open with" app for it.

---

### Post by efflandt on 2012-07-23
dino99 didn't quite read carefully enough that you are not trying to open a .bin file, but a .fits file.

From Help in the file manager:

[COLOR=#3C3C3C][FONT=sans-serif]
[LIST]
[*]Select a file of the type whose default application you want to change. For example, to change which application is used to open MP3 files, select a [FONT=monospace].mp3[/FONT] file.
[*]**Right-click** the file and select **[COLOR=#6C6C6C]Properties[/COLOR]**.
[*]Select the **[COLOR=#6C6C6C]Open With[/COLOR]** tab.
[*]Select the application you want and click [COLOR=#6C6C6C]Set as default[/COLOR]. By default, the file manager only shows applications it knows can handle the file. To look through all the applications on your computer, click [COLOR=#6C6C6C]Show other applications[/COLOR].
If [COLOR=#6C6C6C]Other Applications[/COLOR] contains an application you sometimes want to use, but don't want to make the default, select that application and click [COLOR=#6C6C6C]Add[/COLOR]. This will add it to [COLOR=#6C6C6C]Recommended Applications[/COLOR]. You will then be able to use this application by right-clicking the file and selecting it from the list.
[/LIST]
 [/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]This changes the default application not just for the selected file, but for all files with the same type.[/FONT][/COLOR]

---

### Post by Duveltje on 2012-07-24
Hi guys, thanks for the replies.

I indeed need to open a .fits file using a program located in my local bin folder, which is added to my .profile.

I can open .fits files using the command $ ds9 <filename>, but I want to be able to open .fits files by double clicking on them.

Attached is a screenshot of the 'open with' tab of a .fits file.
As you can see, Ds9 is not in the 'other applications' list and I have no idea how to get it in that list (as it once did on Ubuntu 10.04)

---

### Post by IraGainesUK on 2012-09-16
Hi Duveltje, 

Fellow astronomer here, and I hit the same problem trying to set up TOPCAT to be the default app for opening .fits catalogue files. I don't think either of the previous posters entirely grasped the problem.

I also can't believe it me took this long to figure out how to do such a simple thing in 12.04(!!), but the simple way is this:

1) Install Ubuntu Tweak:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

2) Open it up on the command line, $ ubuntu-tweak

3) Navigate to Admins > File Type Manager and click 'All'. This may take a moment whilst it scans all your mimetypes. 

4) Uncheck 'Only show filetypes with associated applications' at the bottom (again, may take some time).

5) Click anywhere in the right-hand panel and start typing 'fits' to begin searching for the 'FITS document' mimetype. Hopefully you should find it.

6) Double click it, and click 'Add' and then your custom command (for me, topcat, for you, ds9).

[N.B.: If you don't find the FITS mimetype listed, I would recommend installing GIMP as GIMP seems to have the FITS mimetype listed as a format it can open. You can also check the current mimetype of your .fits file by right-clicking it and selecting 'Properties' and then looking at 'Type'.]

Enjoy! I can't believe such simple functionality has been removed from Ubuntu, it really has gone downhill over the last two or so years. Sad to see.

Hopefully that helps, 

Cheers!

---

### Post by aleandrodasilva on 2012-09-30
Hi,

install the file manager thunar. It has the old good Gui to choose the commands.

I would open a bug. Such a simple and useful function removed..........

Bug already opened. Please log in and submit the affection.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/984930](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/984930)

Cheers

---

### Post by Duveltje on 2013-01-03
> **IraGainesUK said:**
> Hi Duveltje, 

Fellow astronomer here, and I hit the same problem trying to set up TOPCAT to be the default app for opening .fits catalogue files. I don't think either of the previous posters entirely grasped the problem.

I also can't believe it me took this long to figure out how to do such a simple thing in 12.04(!!), but the simple way is this:

1) Install Ubuntu Tweak:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

2) Open it up on the command line, $ ubuntu-tweak

3) Navigate to Admins > File Type Manager and click 'All'. This may take a moment whilst it scans all your mimetypes. 

4) Uncheck 'Only show filetypes with associated applications' at the bottom (again, may take some time).

5) Click anywhere in the right-hand panel and start typing 'fits' to begin searching for the 'FITS document' mimetype. Hopefully you should find it.

6) Double click it, and click 'Add' and then your custom command (for me, topcat, for you, ds9).

[N.B.: If you don't find the FITS mimetype listed, I would recommend installing GIMP as GIMP seems to have the FITS mimetype listed as a format it can open. You can also check the current mimetype of your .fits file by right-clicking it and selecting 'Properties' and then looking at 'Type'.]

Enjoy! I can't believe such simple functionality has been removed from Ubuntu, it really has gone downhill over the last two or so years. Sad to see.

Hopefully that helps, 

Cheers!

This solved my problem. Many thanks IraGainesUK! Good luck with your research ;)

---

### Post by namitasheth on 2013-04-12
[**[COLOR=#000000]IraGainesUK[/COLOR]**]("http://ubuntuforums.org/member.php?u=787718") :: Thanks Also solved my problem for the PHP file open with zend studio in ubuntu 12.04

---

