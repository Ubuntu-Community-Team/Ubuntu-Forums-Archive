---
title: "Migrate Documents and Settings does not complete loading"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by bzimage on 2007-04-20
Hi all,

I am installing from the Live CD. When I get to step 5, the installer looks for Documents and Settings to migrate. For some reason the installer stays busy and will not let me move forward without migrating a user. How do I tell the installer to stop looking for accounts to migrate and finish the installation process?

thank you very much

---

### Post by bzimage on 2007-04-20
the version is 7.04

---

### Post by bzimage on 2007-04-21
no one ever met this problem?
what can I do to install 7.04?

---

### Post by bzimage on 2007-04-21
finally I got the solution:
boot into X from the install CD, edit file /usr/lib/ubiquity/migration-assistant/ma-ask,
put a new line at header position:
exit 10
then run install icon on desktop, it will fail on the step, continue anyway.
It works.

---

### Post by alextj on 2007-04-27
Hi! I have exactly yhe same problem.
Can you explain a little, what is "header position" within ma-ask file?
I have pasted new line with "exit 10" at the very beginning and some other random places, but it didn't really work :P

Can you help please?

I am quited tired of this Migration Assistant that I don't need at all, that prevents me from installing Ubuntu and cannot be canceled easily. Real bummer!

---

