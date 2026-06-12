---
title: "Ubuntu 9.04 Adobe Flash kinda works"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ryanparrish on 2009-04-05
Hello All, 

My flash player kinda works youtube works vimeo and hulu don't work on flash content when the page first loads there is a grey box with a triangle with a circle around it, I searched and figure it out maybe some one knows :)

---

### Post by fixitdude on 2009-04-05
Search kinda works too :)

[http://ubuntuforums.org/showthread.php?t=1092624](http://ubuntuforums.org/showthread.php?t=1092624)

---

### Post by ryanparrish on 2009-04-05
Yeah that post just says no one has a fully functional fix, I wonder what happened from 8.10 to 9.04 because it was working in 8.10 I guess I will have to wait for adobe or ubuntu to come with a solution or revert to previous version

---

### Post by ryanparrish on 2009-04-08
bump

---

### Post by Jammy4041 on 2009-04-08
After upgrading to the Jaunty beta, from Intrepid, I did notice quirky flash. Games websites which required flash, Youtube and others such as Walkers Crisps didn't work. 

This was odd as synaptic and apt-get reported flashplugin-nonfree was installed.

I did an apt-get update, and then an apt-get upgrade, and then

```
sudo apt-get purge flashplugin-nonfree
```-to remove the Intrepid version of the non free flash plugin 
and then 

```
sudo apt-get install flashplugin-nonfree
```-to install Jaunty's version. 

Flash now works in Firefox. But this was strange as they were both the same version. But it worked for me. Try giving this a go- it may work for you too.

P.S: I do believe-correct me if I'm wrong, that their is a specific development forum for Jaunty. Please post future posts about Jaunty in here, and file any bugs on Launchpad so that the developers can fix them. Thankyou. ;)

---

### Post by ryanparrish on 2009-04-09
Thanks for the  help I am going to  post a bug in  launchpad I gave the purge and reinstall a go but no go it still doesn't fully work :)

---

