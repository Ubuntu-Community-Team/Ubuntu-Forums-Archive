---
title: "Synaptic and Update error after finally getting X Server running"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Morbett on 2006-03-04
This post is from another thread about X Server, but since I got that working I am starting a new thread for my new problem.

Now that I have GNOME up and running after updating to Breezy, I have some updates. However I get some errors when I try to update as well as try opening synaptic.

I get :

> 

Failed to run /usr/sbin/synaptic:
Unable to copy the user's Xauthorization file.  

and 



> 
Failed to run /usr/bin/update-manager:
Unable to copy the user's Xauthorization file.  


Any idea how to fix this? 

(Also, I noticed that when I go to System -> About Ubuntu, that it still says "Welcome to Ubuntu Linux 5.04 : The Hoary Hedghog". Does this mean I didn't upgrade to Breezy ?

---

### Post by Xian on 2006-03-04
Try renaming that Xauthority file, then logout/login.
It should create a new file for you and fix the issue.

---

### Post by Morbett on 2006-03-04
[QUOTE=Xian]Try renaming that Xauthority file, then logout/login.
It should create a new file for you and fix the issue.[/QUOTE]

Thanks Xian.

Do you know where the Xauthority file would be?  I did a search but have no idea where it is.

---

### Post by kaamos on 2006-03-04
Do
```
locate .Xauthority
```
should return "/home/*yourusername*/.Xauthority". You can press ctrl+h in nautilus to view hidden files.

---

