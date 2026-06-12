---
title: "add/remove progams relocated?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by P4man on 2009-09-22
I see its now in system > administration

While I agree it makes sense to have it there, I deeply regret this change. 

New ubuntu users are not used to installing software from repositories, they are used to hunt the internet and download apps, and will probably not even look in system > adminstration.  If they do look there, they will figure its the equvalent to windows (ie, just to remove software).

Where it was, it was great to help ppl get started and make them aware of one of the fundamental differences (and advantages) of using ubuntu over windows or OS-X. And even for seasoned users, I thought it was a good place for add/remove software.

:(

---

### Post by philinux on 2009-09-22
New addition.

Applications> Ubuntu Software Store

---

### Post by taavikko on 2009-09-22
Hmm, I see "Ubuntu software store" under Applications menu...
Like the Add/Remove used to be...

---

### Post by P4man on 2009-09-22
ugh.. seems I removed software store for some reason.. sorry folks :)

---

### Post by Sophont on 2009-09-22
> **P4man said:**
> I see its now in system > administration
Where it was, it was great to help ppl get started and make them aware of one of the fundamental differences (and advantages) of using ubuntu over windows or OS-X. And even for seasoned users, I thought it was a good place for add/remove software.

:(

Perhaps you need to install some updates or restart your machine - because an equivalent Programm is still on the bottom of the Applications menu. "Ubuntu Software Store" offers basically the same functionality as Add/Remove did and is meant as a replacement.

No idea why the old "Add/Remove Applications" is still around at all - perhaps just put temporarily under Administration until USS is seen to be sufficnently stable. I don't think Add/Remove will be under Administration for long.

---

### Post by P4man on 2009-09-22
> **Sophont said:**
> Perhaps you need to install some updates or restart your machine - because an equivalent Programm is still on the bottom of the Applications menu. "Ubuntu Software Store" offers basically the same functionality as Add/Remove did and is meant as a replacement.

As posted above, indeed I somehow managed to remove the software store package. Its below my application list again now :)

I still feel "software store" is a great regression from add/remove programs. It requires a lot more clicks and doesn't look half as good. At the very least they should expand a selected program below or in a right pane without having to click and then click again (and its not clear where to click) to go back to view another program. Browsing the list is a bit of a pain, and it used to work quite nice: do a search, then browse the list using arrow keys or selecting the apps and viewing the details in the same screen.

---

### Post by forumache on 2009-09-23
I have:

Applications|Ubuntu Software Store
System|Administration|Add/Remove Applications
System|Administration|Ubuntu Software Store

and of course
System|Administration|Synaptic Package Manager
System|Administration|Software Sources
System|Administration|Update Manager

too many things.

I think we will need:
Ubuntu Software Store for newbies.
Synaptic Package Manager for the rest (software sources is accessible from synaptic).
Update Manager should pop up automatically for newbies (like it does now) and be accessible from synaptic (the reload option, mark all upgrades, somehow improved) for the others

Anyway, I read that this is the plan for next version.

---

### Post by ad_267 on 2009-09-23
> **forumache said:**
> 
too many things.

I think we will need:
Ubuntu Software Store for newbies.
Synaptic Package Manager for the rest (software sources is accessible from synaptic).
Update Manager should pop up automatically for newbies (like it does now) and be accessible from synaptic (the reload option, mark all upgrades, somehow improved) for the others

Anyway, I read that this is the plan for next version.

Have a look at the wiki page for the Software Store. It's designed to replace Add/Remove, Update Manager and Synaptic. At the moment it only implements functionality from Add/Remove so is only replacing that. Eventually it will provide the functionality of all three and will replace them.

---

### Post by VMC on 2009-09-23
> **taavikko said:**
> Hmm, I see "Ubuntu software store" under Applications menu...
Like the Add/Remove used to be...

Yea, its in two places now. I guess they don't want you to miss it :)

---

### Post by Sophont on 2009-09-25
My guess is that the current duplication is just a temporary thing. 

And P4man - I agree - Add/Remove looked better than the current USS. But It's an early iteration and it's safe to assume they'll imporove it over time.

The only functional improvement so far (taken over from Synaptic) is that it lists installed software too.
But moving the categories from the left list to the right icon display as departments doesn't make much sense yet.

Besides - a lot of software is not available via USS yet. I recently tried to look for gtkparasite and bootchart - neither can be installed via USS (View is set to "All Applications").

I get that it makes sense to filter out many packages. -dev Packages and those that only contain libs to be used by apps should be filtered by default as they are not of direct interest to regular use. But we still to get to them somehow before Synaptic can be replaced (sure I can always go via apt-get/aptitude - but visual browsing has its charms).

---

### Post by rburkartjo on 2009-09-25
be  interesting to see how this works out in the final release

---

### Post by ad_267 on 2009-09-25
> **rburkartjo said:**
> be  interesting to see how this works out in the final release

I don't think its going to change much before the final release of Karmic. It's only going to start to be an improvement over Add/Remove + Synaptic + Update manager in the next release or the one after.

---

### Post by oldgeekster on 2009-09-25
> **ad_267 said:**
> I don't think its going to change much before the final release of Karmic. It's only going to start to be an improvement over Add/Remove + Synaptic + Update manager in the next release or the one after.Software Store is now "Software Center" as of today. ;)

---

