---
title: "Help! Can't upgrade from 18.04.1 LTS to 18.10. &quot;Could not calc the upgrade&quot;?"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2018-10-19
I am unable to upgrade my 18.04.1 LTS install to 18.10. Every time I try, I get the following message:

**"Could not calculate the upgrade."**

[https://drive.google.com/open?id=1kv8fsJzqyXCVzWv6pjInifMaiwz5dJXK](https://drive.google.com/open?id=1kv8fsJzqyXCVzWv6pjInifMaiwz5dJXK)

...at which point any changes are reverted back to where I started. The most likely reason of the three listed is #3 (I'm not using the "pre-release" of anything.)

How do I overcome this? :o

---

### Post by deadflowr on 2018-10-19
> The most likely reason of the three listed is #3 
huh?
What's the context?
Is this in reference to something?

Edit: I see the added link now, okay.


so...
what 3rd party repositories or software have you added or installed?
While the upgrader will disable any 3rd party repos like ppa and such.
It will not downgrade the added software if it needs to.
Depending on what software was added you might need to either remove the software or see if you can run ppa-purge against it, which would downgrade it to the versions used in Ubuntu.

A little on ppa-purge here:
[https://askubuntu.com/questions/307/how-can-ppas-be-removed]("https://askubuntu.com/questions/307/how-can-ppas-be-removed")

---

### Post by Mugsy323 on 2018-10-19
> **deadflowr said:**
> huh?
what 3rd party repositories or software have you added or installed?
While the upgrader will disable any 3rd party repos like ppa and such.
It will not downgrade the added software if it needs to.
Depending on what software was added you might need to either remove the software or see if you can run ppa-purge against it, which would downgrade it to the versions used in Ubuntu.

A little on ppa-purge here:
[https://askubuntu.com/questions/307/how-can-ppas-be-removed]("https://askubuntu.com/questions/307/how-can-ppas-be-removed")

Thx for the reply.

I have 3rd Party repositories for Wine and DxVk (a beta "DirectX to Vulkan" translator) and maybe 1 or 2 more for other things I'm not sure. But I unchecked every 3rd party Repository (everything below "Canonical") and I still get the same error:

Disabled Repositories:
[https://drive.google.com/open?id=1cMs4tR3aUlWqJktnzTCOVLmJecdOQxsJ](https://drive.google.com/open?id=1cMs4tR3aUlWqJktnzTCOVLmJecdOQxsJ)

Any ideas?

---

### Post by wildmanne39 on 2018-10-19
*Thread moved to **Installation & Upgrades for a more appropriate fit**.*

---

### Post by Mugsy323 on 2018-10-20
I can never tell the appropriate forum. It seems everything I post gets moved. :(

---

### Post by dino99 on 2018-10-20
That error seems affecting randomly system needing some cleaning, or too fully partition.
Partition should never be used more than 85 % because there is need for temporary calculation/upload/....

Clean the system with gtkorphan and bleachbit (as root, select carefully settings)
You also need a working swap file (default nowadays) or partition.

---

