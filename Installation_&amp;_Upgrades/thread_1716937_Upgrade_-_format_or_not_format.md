---
title: "Upgrade - format or not format?"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by sam_i on 2011-03-29
Hi Guys,

Sorry this has been posted many times I expect, but I did have a search and was struggling to find useful pages...

When doing an upgrade using a new cd (i.e. normally a clean format) I noticed (on the advanced formatting options) for the first time the ability to do the following steps:
 - delete a partition (in my case / mount as I have home separate), 
 - recreate the partition as it was before
 - and not click the format flag

This shows a little dialogue box which warns me the drive is not ticked for formatting. 
This box got me thinking so I stopped the upgrade and tried the same in a VM.

Running the installer works and it seems it state 'Removing conflicting operating system files', which seems reasonable. The VM install seemed to work afterwards being the newer version of the OS and with all my old options (fstab etc).

So my questions are -
 - is there any difference between this operation and a distro upgrade (i.e. sudo apt-get dist-upgrade)?
 - is this cleaner or dirtier (i.e. leaving old files behind) than a clean format? I am guessing dirtier...
 - should I even be considering this option?

Thanks for your time and please let me know if there is another post for this - thanks!

---

### Post by sam_i on 2011-07-05
Just remembered this post so I thought I would give it a bump. Anyone got any thoughts?

---

### Post by dino99 on 2011-07-05
on my side i do a fresh install (formatting) for each LTS release, otherwise i dist-upgrade. With a fresh install you are sure that old borked settings dont disturb you :)

---

### Post by nomko on 2011-07-05
Agree with dino99.
 
New release, new installation. YES format the partitions before installing a new fresh version. All settings and config files which can cause version related issues can then no longer affect your new installation. Version related issues meaning that older versions of setting files or configuration files do not conflict with the newer setting or configuration files, there might be a small chance that 1 or 2 things have been changed in the newer versions...
 
Before formatting your partitions, be sure you backed up everything you need like documents, photo's and other files.

---

### Post by sam_i on 2011-07-06
Hi,

Thanks for the replies. I would ask however did you guys understand my question correctly - as your answers seem to indicate that you are answering the clean install vs upgrade question.

What I specifically want to know - is there any difference between the operation described in the first post (i.e. delete a partition (in my case / mount as I have home separate) - recreate the partition as it was before - and not click the format flag) and a distro upgrade (i.e. sudo apt-get dist-upgrade)?
If your not sure of this operation - try it yourself using a VM and you will (seemingly) see a difference...

Your answers may also suggest that there is no difference - however please can someone clarify!

Thank you all.

---

### Post by nomko on 2011-07-06
This is how i do an upgrade or clean/fresh install:
 
First i run the Gparted Live-cd. Then i completly remove the / partition and the swap partition. I don't have to be afraid of any documents, photo's or other important left behind, i've got an external disk on which everything is stored. After applying the changes in Gparted i have to reboot. During reboot i can change the Gparted live-cd with the Ubuntu live-cd.
 
When my system has rebooted the Ubuntu live-cd starts up. I follow the installation instruction untill i reach the section of disk partitioning. I always do it manually. I create a new / partition and a new swap partition. I never tick off the format option. I believe when a new partiton is created it is ticked on automaticly. Then i continue the setup till everything is finished.
 
Why removing the partitons with the Gparted live-cd? Then i'm 100% sure everything is gone which can cause any issues with my new/fresh installation.

---

### Post by 73ckn797 on 2011-07-06
I format the "/" partition and simply designate /home to that partition without a format. My data is not lost. It is good to delete typical folders that are created in /home that are not application specific. I keep the Mozilla, Libreoffice, Thunderbird and other similar folders. My latest install was due to a borked config file, though I could not find out which one, that made window borders not show in 11.04 Ubuntu Classic DE. I reverted back to 10.04 without deleting any of the /home folders and on restart the border problem was still there. I deleted those other folders and re-installed and the problem was solved. I still did not lose any settings specific to my programs.

---

### Post by sam_i on 2011-07-06
Thanks for the replies.

+1 for the gparted route, same way I do all my partitioning. I have separate /home, swap, /opt / partitions too. 

But again, please try what I have suggested through a VM and you will see.

But I am not asking which is the best root at this stage (as fersh beats upgrade any day), I am just questioning if the described method does anything different to a standard upgrade i.e. does this method do anything cleaner than a normal upgrade....

Thanks for your time.

---

### Post by sam_i on 2011-07-08
Final bump at this post - sorry about that - but I would like to know if there is any difference. Cheers!

---

### Post by mörgæs on 2011-07-08
> **sam_i said:**
> 
But again, please try what I have suggested through a VM and you will see.


You are putting a big work load on people helping you. 

Do you actually expect people to install a VM and after that try a full-scale upgrade on their systems in order to answer this question?

---

### Post by Blasphemist on 2011-07-08
If you didn't do any of the partition changes that you are and choose to do an upgrade (this tries to not loose any files or programs), you would accomplish the same thing with less risk. This doesn't seem like a good choice to me. You're not doing the best upgrade process nor the best clean install process.

---

### Post by sam_i on 2011-07-21
Ok guys,

thanks for the info.
It looks like I should ignore this option and just carry on as normal - clean format per each dist upgrade. New distro = new home partition too.

Cheers for all your posts. 

PS. - I recommend someone have a go at this if they have the time, it really appears like a different option!

---

### Post by sam_i on 2011-07-21
> **mörgæs said:**
> You are putting a big work load on people helping you. 

Do you actually expect people to install a VM and after that try a full-scale upgrade on their systems in order to answer this question?

Nope, just thought a lot of people we like me and already have one created and therefore its a 10min test. Always wrong to presume! Thanks for pointing that out.

---

