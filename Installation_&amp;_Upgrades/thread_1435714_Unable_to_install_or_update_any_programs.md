---
title: "Unable to install or update any programs"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by Deep Thought on 2010-03-21
Hi,
Now that I've performed a clean install of 9.1 I am unable to install or update any programs. When I attempt to use Update Manager to install system updates, after it gets about halfway through it says, "Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages? The options are yes and no, but it doesn't matter what I pick. When I try to install programs through the Ubuntu Software Center, on those rare occasions when the "download" button is actually displayed, I get a message telling me to check my internet connection. If I try to install using terminal using sudo apt-get install "program name" it says it can't find the package. I also get the following error when trying to use the update manager:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

I've checked to be sure that all the appropriate software sources are checked, and I'm using the ideal server(s) for my location. I've gone so far as to re-install the OS twice, so I'm not really sure what else I should do. TIA for any help!

---

### Post by oldos2er on 2010-03-21
Check System, Administration, Software Sources to make sure you have all repositories enabled.

---

### Post by Deep Thought on 2010-03-22
Thanks, but I've already done so.

---

### Post by oldos2er on 2010-03-22
Assuming your network connection is working properly, have you tried different servers?

---

### Post by Deep Thought on 2010-03-22
I had, but this was not the problem; apparently it is an issue with out college network, and I'm working with IT to solve it. Thanks much for your help.

---

