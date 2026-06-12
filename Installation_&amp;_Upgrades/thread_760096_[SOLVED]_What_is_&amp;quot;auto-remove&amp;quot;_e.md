---
title: "[SOLVED] What is &amp;quot;auto-remove&amp;quot; equivalent in synaptic ?"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by realn on 2008-04-19
I understand that if I do 'sudo apt-get remove --auto-remove packagename' , the packagename along with the dependencies which were found AT THE MOMENT OF INSTALL will be uninstalled.
 How can I do it through synaptic ?
 Thank you all !

---

### Post by overdrank on 2008-04-19
> **realn said:**
> I understand that if I do 'sudo apt-get remove --auto-remove packagename' , the packagename along with the dependencies which were found AT THE MOMENT OF INSTALL will be uninstalled.
 How can I do it through synaptic ?
 Thank you all !

HI and in synaptic you can mark for complete removal. :KS

---

### Post by realn on 2008-04-19
I quote from the following post :
[http://ubuntuforums.org/showthread.php?t=660078&highlight=autoremovable](http://ubuntuforums.org/showthread.php?t=660078&highlight=autoremovable)

To get rid of all the packages that were installed as dependencies, but are not needed any more as the original program has been removed, just go to Synaptic, click the 'Status'-button in lower left corner, then select the 'Autoremovable' and uninstall everything that it shows. Or just run "sudo apt-get autoremove" from a terminal..

In fact the command 'sudo apt-get remove --auto-remove packagename' uninstalls only the packages no longer needed by packagename or just simply all from the section "Autoremovable"?

---

