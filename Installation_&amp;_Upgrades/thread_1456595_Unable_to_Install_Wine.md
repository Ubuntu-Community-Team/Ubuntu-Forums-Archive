---
title: "Unable to Install Wine"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by Graywolf0 on 2010-04-17
Well I wanted return to FFXi , so I read about its installation on Ubuntu and saw that wine 1.1.29 is needed , I installed wine , but it seems I installed it wrong (I downloaded it as compressed file and extracted the files :/ ) so I said i'll remove it and reinstall it 

I opened Synaptic Package manager and removed it but its still there under "Application" tab so I went to Home folder and removed the .wine file too (I also tried removing it using the terminal but it didnt seem to work) and the wine is still under App. tab

I thought if I installed wine from terminal or by the right way , it would replace the old one but I couldnt install wine
I tried many command lines in the terminal and non seem to work and this result is what I get 


graywolf0@GrayWolf:~$ sudo apt-get install wine 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

Any help would be appreciated :)

Also the wine should be set to Vista mode , how's that done too? :)

---

### Post by zvacet on 2010-04-17
User system>admin>software sources check all under Ubuntu software and first two under updates tab.Reload.Try to install wine again.

---

### Post by Graywolf0 on 2010-04-24
Thank You! I checked everything but source and that seemed to get it working 
Btw sorry for late thank you :/

---

