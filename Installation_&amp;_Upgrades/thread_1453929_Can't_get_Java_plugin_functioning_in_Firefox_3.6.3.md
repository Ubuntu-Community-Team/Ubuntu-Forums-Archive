---
title: "Can't get Java plugin functioning in Firefox 3.6.3"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by thudon on 2010-04-13
I've had a recent run of ubuntu snafus lately, most of which come back to accidentally getting firefox 3.6.4 (namaroka) installed.  I've since rolled back and gotten flash working properly again, but Zotero isn't working.  I figured out it was because java was being screwy and have been trying to repair it.  
I followed the instructions here first: [http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)
and installed version 6 update 19.  It came up as an add-on in firefox but didn't do anything.  When I pull up a page with java on it the page just says it is disabled and I can click to install it.  However, I then get was getting a box saying: "E: Unable to correct problems, you have held broken packages."
I have since removed update 19, done a complete removal in synaptic, and reinstalled JRE and the plugin by going to a page in firefox and clicking the install button.  Now it still isn't under my extensions list in firefox, it says it's disabled on pages with java, and when I click to install it says I already have it.
I'm running Karmic koala by the way.
I'm stumped

Sorry for the novel-like description, just trying to get the whole story out there.  Any help would be REALLY appreciated.

---

### Post by us11csalyer on 2010-04-14
Click Applications
Click Software-Center
Search for java
Install your needed java plug-n, ect
Make sure to close out of firefox then open it back up. Java should work now.

---

### Post by thudon on 2010-04-14
it already says its installed

---

### Post by wojox on 2010-04-14
Try this out. It hasn't failed me yet: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by thudon on 2010-04-14
Yay, that worked perfectly Wojox.  Thanks for the help!

---

