---
title: "unable to uninstall teamviewer"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by ltoso on 2010-12-10
Hi,
I installed Teamviewer 6, it installed through wine, but my older version of teamviewer is still their but is not opening how can i uninstall it, i have checked in the ubuntu software center it is not available there

Please recommend

---

### Post by sikander3786 on 2010-12-10
Applications > Wine > Uninstall Wine Software, did you try that?

There is a hidden .wine directory (Press Ctrl + H) in your /home folder. All the software get installed to that, if you can't un-install that, you can manually remove however not recommended.

~/.local/share/applications/wine/Programs/ cotains Wine shortcuts. You can manually remove if they don't get removed after un-install.

---

### Post by ltoso on 2010-12-10
Thanx for fast reply sikander, 
i don't have .wine in the /home/username 
however i think the older version for team viewer was not installed through wine as when it got installed there was no wine in applications menu, 
it is simply installed in 
applications>internet>teamviewer
Can you tell me how can i modify the links in the internet menu and where they lead to 
or some command that can uninstall it

the newer version of teamviewer has an uninstall present in the wine menu in applications

Please recommend

---

### Post by ltoso on 2010-12-10
Hi,
i found out the way
go system>administration> synaptic pacakage manger
search for teamviewer, select the one you want to uninstall and it uninstalls
but then the menu item still remains in order to remove the menu item from the 
applications>internet 
go to 
prefrences>menu 
here you can select the menu item that you want to delete 

Hope somebody looking for the same thing will have a solution now

---

### Post by sikander3786 on 2010-12-10
Did you download the Linux version of Teamviewer and installed that previously?

Go to Synaptic Package Manager under System > Administration and search for Teamviewer, it will appear if it is installed and you can remove it there.

**Added:** Glad you sorted it yourself. You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by mbeach on 2013-01-13
for my sake if I run into this again (just updated to teamviewer8) I needed to edit the 
/usr/share/applications/desktop.en_CA.utf8.cache
file to get rid of what appeared to be orphaned items in the menu. Alacarte (System-Preferences-Main Menu) wouldn't let me delete them, and if opened from a terminal, you could see an error indicating the associated desktop file didn't exist.

I'm sure if I had installed something else through synaptic the cache file would be rebuilt but in this case I only realized that after the fact.

using lucid 10.04.

mb.

---

### Post by overdrank on 2013-01-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

