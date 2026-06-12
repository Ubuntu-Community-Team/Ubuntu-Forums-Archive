---
title: "Edubuntu 7.04 default install doesn't have Education suite?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by altufaltu on 2007-04-21
Hi,

I did a fresh install of Edubuntu 7.04 today to find that the whole bunch of education programs (like gcompris) that came default with Edubuntu are missing :( from default installation.

Did I do something wrong? or is it expected?

Please suggest.

- Altu faltu

---

### Post by Jetjoint on 2007-04-23
I have the same problem. Installed it yesterday. All applications were there while running the live CD but the education suite was gone after installation ??

---

### Post by altufaltu on 2007-04-26
There seems a bug in installer script.

When I installed it again, I saw that at the end, installer script removes all educational packages :( 

One has to download them again from net. I could not find any way to install it again from Edubuntu  CD.

- Altu

---

### Post by The Pinny Parlour on 2007-05-06
Has this issue been sorted out yet?   One of the underlying benefits it is for the educational software isn't it?

---

### Post by mdbarton on 2007-05-08
Had the same problem on my fresh install.  Think I'll just use normal Ubuntu as I know that installs fine...

---

### Post by dspari1 on 2007-05-09
Here is the fix:

Insert the Edubuntu 7.04 CD in your CD drive
open the Synaptic Package Manager
Click in Settings=>Repositories
Unselected all the boxes in the Ubuntu Software Tab (write the marked boxes because you have to selected then after you finish)
Do the same with the others Tabs, but in the Third-Paty Software Tab leave mark the Cdrom [Ubuntu...]
Click in Close
Click in the reload
Click in the button above the green or white boxes to sort the installed package from the non installed package.
The green are the installed packages and the white are the non installed.
right click in the white package and select mark for installation.
do it to all the white package.
Click in the Apply button.
After finish:
Click in Setting=>Repositories
Select all the boxes that you unselected in all the Tabs.
Close the Synaptic Manager and capish you have all the educational suite installed.

I will later give more detailed instructions with screenshots.

---

