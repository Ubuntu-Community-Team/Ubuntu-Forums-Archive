---
title: "Keeping track of applications"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by henriette_holm on 2005-05-20
Hi.
I did a "clean" install of Ubuntu 5.04 a while back and after that I have installed various applications. Now I'm thinking about whiping my dual-boot and doing 100 % Ubuntu. Is there anyway of finding out which applications are installed on my computer - not counting the ones that come with the standard install of Ubuntu?

Thanks

---

### Post by Sniffer on 2005-05-20
[QUOTE=henriette_holm]Hi.
I did a "clean" install of Ubuntu 5.04 a while back and after that I have installed various applications. Now I'm thinking about whiping my dual-boot and doing 100 % Ubuntu. Is there anyway of finding out which applications are installed on my computer - not counting the ones that come with the standard install of Ubuntu?

Thanks[/QUOTE]

The only way i know is going by Synaptic and search what you have installed.

You can see as well by the terminal....but is better and easy by synaptic.

Sniff.

---

### Post by henriette_holm on 2005-05-20
How do I search what I have installed?

-Henriette

---

### Post by apollyonis on 2005-05-20
In Synaptic, go to the bottom left, click Status, then right underneath "All" there should be an option for "Installed". Click it, wait for the list to reload, then to filter it further, where it shows "S, blank box, Package Version, Installed Version, Latest Version, and Description" click the blank box and it should rearrange which are the original packages (which have the Ubuntu logo beside the description) and which have been installed (the ones with no logo). Careful, because if you've added the Backports repository and upgraded anything off of there, then those will show up as Non-Ubuntu packages...such as Synaptic itself so be careful on what you delete!

---

### Post by henriette_holm on 2005-05-20
Don't worry - I'm not about to delete anything - except for my whole hard drive  ;-) 
No, I just want to make a list of all the nice apps I have installed - so I can install them again after I kill off my windows partitions.

-Henriette

---

### Post by apollyonis on 2005-05-20
Lol! Ok. I misread what you had originally asked. You still have to go to the menu Status -> click Installed (example of selection is in the screenshot) -> File -> Save Markings As... 
Save that file to a disk. Then when you reinstall Ubuntu, go back into Synaptic and go to File -> Read Markings. It will reselect everything that you have selected. Then you should be able to do an Apply and it will redownload and install everything. I'd make sure all of my repositories are the same as before you wiped it clean.

---

### Post by bruizer on 2005-05-20
This is great for keeping track of what all was installed, but it will not help you keep some of your stuff configured. There was a really good HowTo on Backup and Restore for a Linux system here:

[HowTo: Backup and Restore your Linux System](http://www.ubuntuforums.org/showthread.php?t=35087) 

This may save you some time in trying to get the system back up and running after the format.

Good Luck!

---

### Post by henriette_holm on 2005-05-21
Thanks a lot for all the suggestions  :) 

- Henriette

---

