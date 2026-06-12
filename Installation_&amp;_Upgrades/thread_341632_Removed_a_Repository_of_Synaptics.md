---
title: "Removed a Repository of Synaptics"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by mmendez on 2007-01-18
Well I was trying to add a custom repository to download a video editor and by mistake I unchecked a what I believe was a cd-rom repository and it disappeared. I checked to see if this is normal so I unchecked the newly added repository and it also disappeared. I wanted to check if it would also happen if I clicked the remove . So I clicked the button while on the wine repository and the same thing happened. Now my problem is that now Synaptics wont load ANYTHING. When I close and reopen synaptics a window appears that says

"E: Malformed line 39 in source list /etc/apt/sources.list (dist)
 E: The list of sources could not be read.
 Go to the repository dialog to correct the problem."

Then when I insert my Dapper Cd and click 'add Cd rom' I first get a new window that says "Please insert a disc in the drive" even though I have two of the same discs in BOTH drives.
So I click ok and a window with a progress bar that was up in the background can be seen saying
"Mounting CD-ROM" then
"Scanning disc for index files" then
"Copying package lists" then finlally
"Unmounting CD-ROM" 
where it seems to stay at
so I click close and it says repositories have changed reload, I do, and then I get a new window in front of the package information download window saying
"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

I click ok and another window pops up saying 
"E: Malformed line 26 in source list /etc/apt/sources.list (dist)
 E: Unable to lock the list directory"

](*,) Sorry if I am going to make you pull out your hair also please take into account still a bit of a noob](*,) 

thanks _ALOT_

---

### Post by dcstar on 2007-01-18
> **mmendez said:**
> Well I was trying to add a custom repository to download a video editor and by mistake I unchecked a what I believe was a cd-rom repository and it disappeared. I checked to see if this is normal so I unchecked the newly added repository and it also disappeared. I wanted to check if it would also happen if I clicked the remove . So I clicked the button while on the wine repository and the same thing happened. Now my problem is that now Synaptics wont load ANYTHING. When I close and reopen synaptics a window appears that says

"E: Malformed line 39 in source list /etc/apt/sources.list (dist)
 E: The list of sources could not be read.
 Go to the repository dialog to correct the problem."

Then when I insert my Dapper Cd and click 'add Cd rom' I first get a new window that says "Please insert a disc in the drive" even though I have two of the same discs in BOTH drives.
So I click ok and a window with a progress bar that was up in the background can be seen saying
"Mounting CD-ROM" then
"Scanning disc for index files" then
"Copying package lists" then finlally
"Unmounting CD-ROM" 
where it seems to stay at
so I click close and it says repositories have changed reload, I do, and then I get a new window in front of the package information download window saying
"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

I click ok and another window pops up saying 
"E: Malformed line 26 in source list /etc/apt/sources.list (dist)
 E: Unable to lock the list directory"

](*,) Sorry if I am going to make you pull out your hair also please take into account still a bit of a noob](*,) 

thanks _ALOT_

```
sudo gedit /etc/apt/sources.list
```
Will allow you to examine and manually edit the sources.list file (look at the line 26 that is reported as a problem).

Do a forum search for a default sources.list for your version, you may want to replace it if it is too far gone.

---

### Post by mmendez on 2007-01-19
Worked like a charm thanks alot :biggrin:

---

