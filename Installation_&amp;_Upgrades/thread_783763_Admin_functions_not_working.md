---
title: "Admin functions not working"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by freebird54 on 2008-05-06
This is an odd one.  Early details were posted on beginners - but It may be beyond that now!

Whenever, and HOWever I try to run admin level functions (such as Software Sources or Synaptic or Add/Remove Progs) I get a lower panel entry saying "Starting Administrati" for a few seconds, then it goes away without any further sign of its having been selected.  This applies whether it is 'ordered up' from the menus, clicked on from the "Control Centre" (which I activated from the menus just to see) or whether I just try to run it from terminal.  Regardless of whether I try with gksu of gksudo (or even just sudo in the case of Software Sources) - the same result.  By the way - there is NO error output into the terminal, and I have to use CTRL-C to get the prompt back after the program exits.

This behaviour is strange enough - but it differs from what I got yesterday.  Yesterday I had a fresh Hardy install, and the programs would run only from the terminal (without error msgs there too) but would not from the menus.  So - today I put a fresh Gutsy on, updated fully, then upgraded to Hardy online.  This process went cleanly, but with the results as described.

Anyone have any ideas?  Beyond the obvious, like going back to Gutsy (which had video anomalies that seem to be gone with Hardy) or even to Feisty (which worked fine)?  Being patient and hope an update fixes it (assuming that the update manager will run - which was NOT the case on the first run-in with this problem). Switch to another distro?  My hardware shouldn't be too weird- all intel desktop MB, processor, video,sound - 4Gb RAM, 500 G drive, MS keyboard/mouse - pretty normal stuff!

Thanks in advance.... I want to keep on with FF 3 too!

---

### Post by pardillo on 2008-05-06
Hello. I've got the same problem and still looking for a solution. But I've run synaptic using the root account. In a terminal, making "su" and providing root password, and just running "/usr/sbin/synaptic" it worked as it worked before upgrading.

Hope someone has a better idea.

---

### Post by Matoridi on 2008-05-06
I had the same problem after adding a domain name to my host in System|Administration|Network.  I removed it in the "General" tab, edited my host name in the "Hosts" tab in order to remove the .domain part added previously, rebooted...  And voilà, everything is back to normal!


Hope this helps

---

### Post by freebird54 on 2008-05-06
I am still at a loss to understand why - but this fix definitely WORKS! :)

Mucho Gracias!

I suspect I would never have found THAT connection on my own - did you discover this by starting from a working system, then encountering a problem?  Or did you actually conceptualize a potential conflict, and hit on this one???

Either way - thanks again - apparently all is well (standard programs added, codecs found, and setup continuing)....

---

### Post by Matoridi on 2008-05-06
Well, I don't know if you're answering to my post (though I would guess so), but to answer your question :

I tried launching synaptic through the terminal (with sudo) and then received the error message that it could not resolve my host...  Then I remembered encountering a similar problem in Feisty or Gutsy after adding a domain name to my host name... (I experiment a lot with my computer...).  I also remembered a post about this problem (I think this was one : [http://ubuntuforums.org/showthread.php?t=753429]("http://ubuntuforums.org/showthread.php?t=753429")

That's it...  No great analysis here, I'm afraid. :)


Regards

---

### Post by Ozzee on 2008-05-07
Removing the domain in my network settings worked for me as well. 
Thank You! :)

---

### Post by freebird54 on 2008-05-07
Well - whatever the mechanism of discovery was, it worked very well!  From the thread you noted I gather that some sufferers from this problem are lucky enough to get error messages (which I did not) - so that makes it even more appreciated.  Official thanks are entered... :)

---

### Post by roger_1960 on 2008-06-05
> **Matoridi said:**
> I had the same problem after adding a domain name to my host in System|Administration|Network.  I removed it in the "General" tab, edited my host name in the "Hosts" tab in order to remove the .domain part added previously, rebooted...  And voilà, everything is back to normal!


Hope this helps

Hi and many thanks - this worked but not sure why!  I had been following a thread which would have me uninstall all earlier versions of the kernel in order to get over this problem.  I had just installed Hardy xubuntu and then upgraded to latest kernel and it was reasonable to guess the upgrade was the problem rather than the network setup!

---

