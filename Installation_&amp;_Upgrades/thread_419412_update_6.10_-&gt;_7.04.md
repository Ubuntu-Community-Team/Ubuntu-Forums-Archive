---
title: "update 6.10 -&gt; 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2007-04-23
If I enter   $ gksu "update-manager -c"   into Terminal, it gives me     bash: $: command not found    .   If I enter gksu, it gives me "run program", where if I put in  "update-manager -c"  it doesn't give me the option to upgrade to 7.04 .  If I just start update manager, same story.

I have a full install CD of 7.04.  What happens if I just install it over 6.10  -  or can I do that at all?

---

### Post by mouseclone on 2007-04-23
I just did it though add remove.  There was an option to upgrade.  took me about 2+ hours and it had a problem mounting my second HD because of the way it was mounted.  Just make sure any spare drives that you are mounting are not using /dev/hd??  unless you are using the ext2 file system.  That was the only thing that gave me trouble so far.

---

