---
title: "get and install the suggested updates package from the command line"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by herbert tamayo on 2012-01-18
hi, when I used the graphical mode in my ubuntu, the update manager tells me that there are suggested updates of some packages and it gives me the option to install them, so, my question is:

is there any commands to do this from command line? i mean, some command to check if there is some updates, and some other command to install them?

I have used apt-get update, but i think this command get the list updates of the reports, but i can't see if there are some update suggestions.

thanks and regards

---

### Post by arpanaut on 2012-01-18
```
sudo apt-get update && sudo apt-get upgrade
```Would be the command to check for updates and afterward to show you what will be upgraded.
at the end it will give you the option of continuing or aborting.

```
man apt-get 
```Will give you the manual for apt-get.

---

