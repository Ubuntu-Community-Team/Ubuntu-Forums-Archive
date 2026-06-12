---
title: "[SOLVED] Can't upgrade from 6.04 to 8.10 cuz i can't update"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by lance0r on 2008-09-06
I'm trying to use kubuntu again and want to upgrade ubuntu from 6.04 to 8.10. According to the info, i should use gksu "update-manager" then when i have everything updated, i am supposed to get a box telling me there is a new release and click to upgrade. But i can't get my current update complete so i don't see the upgrade box. With adept i get an error which says cannot commit changes when i try installing the update-manager and when updating a package called locales.  So i installed synaptic with adept, and tried to update with that app.  The versions of those packages that synaptic showed as the most recent were not in the repository. A higher number was in the repository. When i tried to update the package info in the synaptic edit menu, it failed because it said the Packages.gz was not in gzip format. So i reinstalled gzip, but that didn't help.

So, how should i go forward. Abandon trying to upgrade from the internet, and start fresh with 8.10 disk? Do some simple fix somebody can tell me? Give you all more info so you can figure it out? any help will be appreciated, since i don't know what to do. thanks!!! lance

---

### Post by Sef on 2008-09-07
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=865679").

---

### Post by lance0r on 2008-09-07
This thread didn't help, cuz i didn't get to start the upgrade. My error in synaptic and update-manager was: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.7_all.deb)
and the same for update-manager. the reason for the error was that there was a newer version at the URL. So i copied the new version to my machine, and used, "sudo dpkg -i locales_2.2.18.13_all.deb"
Then when i ran update-manager i got the box at the top that said 8.04.1 is available. Whew. Sef's response helped cuz it tipped me to dkpg. 
Next i am going to click the upgrade request, but thought i better report this problem worked around. I haven't learned how to put [solved] on my reply yet. sorry

---

