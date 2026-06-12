---
title: "Will hard disk frequent load/unload problem be fixed in Intrepid final release?"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter Frank on 2008-09-15
I found my hard disk clicking about 2.5 times/minute with AC power. Come on, this has been around for 2 years and it's the third bug listed on the Launchpad main page.

---

### Post by olskar on 2008-09-15
This is the latest comment on the bug:

> 

I'm highly in favor of the blacklist approach used by Novell/openSUSE as well. It tracks different laptop/hard disk combinations and knows exactly which apm value (254/255) fixes the problem for each entry. The storage-fixup script was written and is maintained by kernel developer Tejun Heo by the way, you can read more information and find the latest version of the script and config file at [http://ata.wiki.kernel.org/index.php/Known_issues](http://ata.wiki.kernel.org/index.php/Known_issues)

If your drive isn't listed yet, you can add the config yourself by looking at the examples and comparing with the output of "dmidecode", "hdparm -I /dev/sda" and "smartctl -a /dev/sda" on your system. You're encouraged to send Tejun Heo this information and whether hdparm -B 254/255 fixes it, so the drive db gets more and more complete. You can do this by mailing [email]linux-ide@vger.kernel.org[/email] like I did here: [http://marc.info/?l=linux-ide&m=122082089712147&w=2](http://marc.info/?l=linux-ide&m=122082089712147&w=2)

This way regular users won't need to use trial and error to see which apm value is needed to disable it.


Sounds like a very good solution to me?

---

