---
title: "Is it possible to download updates on another PC ?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Bernie_the_bolt on 2008-01-05
I have a Pc running Windows XP and Edgy as dual boot. My internet access was via dial up and very slow, so I still have about 140 updates not yet downloaded.
However I now have satellite broad band up and running, but the hardware / softwaredoes not suppport linux yet.
Therefore my question :_ Can I download the updates I need for Edgy,by using  Xp and downloading them _to a cd / dvd / file ? (I can read the windows partition from Ubuntu).
NB:I do not wish to download the full repository as discussed elsewhere on this forum, although I can see the benefit, I would not have the harddrive space necessary and my download speed is not that fast.

---

### Post by Partyboi2 on 2008-01-06
You should be able to do it using the "**Generate Package Download Script" **under Synaptic Package Manager
For this way to work you will need a ubuntu live cd and usb stick 
_** On the Edgy machine**_
Open up "Synaptic Package Manager"
Click on "Mark all upgrades"
It will list all the packages to be upgraded
Click on "Mark"
go to "File" and select "Generate Package Download Script"
Save the script as edgy.sh to your /home folder
Copy that file over to a usb stick
_**Windows Machine**_
Boot your windows Pc with the ubuntu live cd
When you get to the Desktop make a folder on the Desktop  called "downloads". Copy the saved edgy.sh file from the Usb stick into the "downloads" folder
Then open a terminal (Applications>Accessories>Termnial)
Change to Desktop directory
```
cd Desktop/downloads
```then run the script
```
sh edgy.sh
```It will download all the packages you need for the edgy machine into the downloads folder(all going well) 
Then after it has downloaded all the packages that are required. Copy the "downloads" folder to the Usb stick. Then Shut down the live cd and go back to the Edgy machine taking with you the "downloads" folder on the usb stick
[U][B]Back on Edgy Machine
[/B][/U] Move the Downloads folder from the Usb stick to the Desktop or where ever you like.
Open "Synaptic Package Manager" again, go to "File" and select "Add Downloaded Packages" 
Browse to the directory where the "downloads" folder is (probably Desktop)
Then "**[COLOR=Lime]Apply[/COLOR]**" to install them.

---

