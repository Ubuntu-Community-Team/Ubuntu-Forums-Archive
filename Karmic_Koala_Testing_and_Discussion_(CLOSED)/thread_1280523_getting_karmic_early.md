---
title: "getting karmic early"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jarrah-95 on 2009-10-02
can i get the beta of karmic and when the full version comes out can i just update to it instead of doing a full upgrade (in other words without downloading the full 650 mb of the update twice)
im thinking about this as i am just getting back from holidays when the release comes out and dont want to have to set it up then.
thanks.

---

### Post by infinitejones on 2009-10-02
If you mean "can I download a Karmic Beta ISO now, and then use update-manager or aptitude to upgrade to karmic final when it's released", then yes, you can, although in my experience (since 6.10):

1) If you upgrade to Karmic Beta now, you'll find that there are daily updates coming through update-manager that will require you to frequently download more stuff to fix bugs, resolve security issues and so on. So it might not actually save that much bandwidth.

2) It's ***always*** easier to just to wait until the final release, download the ISO and do a fresh install (having [moved your home directory to a different partition]("http://www.google.com.au/search?q=ubuntu+home+directory+separate+partition") first). Fewer bugs, less general messing around and inconvenience.

If you're worried about using your bandwidth on a good old Australian capped download plan, check whether your ISP has the Ubuntu repositories on their own servers. Mine does (iinet) which means that anything downloaded from them (aptitude upgrades and ISOs) doesn't count towards my download limit. Click System, then Software Sources, and dropdown where it says "Main Server" or "Server for Australia". Click "other" and see if your ISP is in the list.

BTW while I was typing this I ran "sudo update-manager -d" and let it calculate the current upgrade from Jaunty to Karmic - it would be an 1100MB download (!!). So by just waiting until the final release and downloading the ISO, I'll save my 400MB of bandwidth and an awful lot of hassle.

---

### Post by markbuntu on 2009-10-02
Daily updates from betas and even releases can really use up a lot of bandwidth. If you are concerned about that then definitely wait until about a month after the release. The alpha testing community tests a lot but not all posible hardware configurations. Betas increase that by about 10x and the release another 10x so a lot of bugs get filed and fixed in a short period with multiple multiple updates to the same packages and frequent large size kernel remodels. 

After about a month that calms down and the updates from iso are mostly stabilized. So, if you are limited in bandwidth waiting is better.

---

