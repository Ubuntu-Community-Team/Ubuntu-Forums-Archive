---
title: "use root with live cd"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by txtinman on 2010-09-09
I have a couple of hard drives on my computer that I need to access with the live cd before I install Ubuntu. When I try to access them I get a message that says I don't have permission. How do I use root with the live cd, or how can I get access to these drives?

Mike White

---

### Post by ajgreeny on 2010-09-09
Open nautilus with ```
gksudo nautilus
``` No password is needed, but you still will have root access.

---

### Post by txtinman on 2010-09-10
Thanks, that got me root access, but I still can't access the hard drives. They don't show in the Nautilus window, and if I click on the computer icon I get this: [COLOR="Red"]**_Could not display "computer:".Nautilus cannot handle "computer" locations_**[/COLOR]. Any other ideas how I can access these drives?

Mike White

---

### Post by ajgreeny on 2010-09-10
This could be pointing to a bad Live CD.  Boot to it and check the CD when it boots by hitting any key after pressing the power button.  A menu should appear with an entry for "Check install media" or something similar.

---

### Post by txtinman on 2010-09-11
Not sure what the problem was. I re-booted the CD and everything worked fine. I was able to work with the files on the two hard drives and then install from the CD with no errors. Thanks for the help.

---

