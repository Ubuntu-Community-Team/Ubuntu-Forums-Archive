---
title: "Upgrade Hardy--&gt;Lucid, Keep /home"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by leehach on 2010-06-04
I've looked at several guides and posts regarding this, and would like some feedback.

I intend to do a clean install of Lucid, but keep my Hardy install on a separate partition until everything is working. (Actually, I have already done a test install and it looks good.) I have /home on a separate partition (as well as a separate /data partition, so /home is mostly configuration files). Having a separate /home partition served me well when I reinstalled Hardy after an abortive attempt to upgrade to Intrepid (after which I decided to stick with Hardy until the next LTS). 

I was thinking of installing Lucid and just mounting the existing /home partition as /home for the new install, but several people pointed out that after the applications upgraded, the old versions installed on Hardy might not work with the updated configuration files.

So I think what I need to do is either:

Make a complete duplicate of /home to a new partition. Install Lucid, pointing to the new (duplicate) partition as /home. Reinstall desired packages.

Or,

Create a new, clean partition. Install Lucid, pointing to the new partition as /home. Mount old_home in Lucid. Copy over specific desired application configuration folders (.mozilla, .amarok, etc.). Reinstall desired packages.

The main advantage of the second route would be to lose some bloat for applications I might not be using, without having to wade through folder by folder to figure out what I want to keep. The main advantage of the first route would be to keep everything as close as possible to my old settings.

Questions: What's the easiest way to duplicate the entire old /home partition? Is the order in route 2 (copy configuration folder, reinstall app) correct? Which plan seems better?

Best,

---

