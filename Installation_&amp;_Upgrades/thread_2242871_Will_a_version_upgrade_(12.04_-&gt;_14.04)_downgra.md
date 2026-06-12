---
title: "Will a version upgrade (12.04 -&gt; 14.04) downgrade an existing package?"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by ltburch2000 on 2014-09-04
I have been trying to successfully upgrade from 12.04 -> 14.04 however the mythtv-database package always fails.  After a bit of research I found other users having upgrade issues with mythtv-database.  Turns out there is a bug in the post install script which causes it to fail.

So back in 12.04 I added the mythtv ppas to my software list and ran an upgrade, I am now on the latest (.27) stable version of mythtv and it seems to be running fine.

My question is, if I now do an upgrade to 14.04 will the ubuntu installer attempt to revert my mythtv to the version packaged with 14.04 (the myth ppas are more up to date) or will it see it is already newer than its version and leave it alone?  

Lee Burch

---

### Post by grahammechanical on 2014-09-04
My advice is to stay on 12.04. Unless you have a good reason for moving to 14.04. But I think that having software installed through that PPA may cause problems with the upgrade to 14.04. It may be that Ubuntu 14.04 has a newer version of MythTV. In which case the risk of breaking the upgrade is less. But if it has an older version the risk will be greater.

Beside which, some of us recommend fresh installs over an upgrade.

Regards.

---

### Post by ltburch2000 on 2014-09-04
I have too much meta data in myth tv to take on a fresh install lightly.  Tomorrow I will backup the image and try the upgrade again.  Either it will leave my myth alone and it will all be good but if it breaks it I will revert to myth .24 backup and run the upgrade, let it break and then fix it on the 14.04 side now that I know how.

I could stay on 12.04 but that feels like delaying the inevitable and migration difficulties only get worse over time.  I hold to only doing LTS releases on some critical components.  Has 14.04 been particularly bad, why you don't recommend it?  At this point it is up to 14.04.1 so I figured the major issues should be ironed out.

Lee Burch

---

### Post by ltburch2000 on 2014-09-05
Here is the answer:

The Ubuntu updater runs and completely leaves alone the MythTV because it is considered a "3rd party package".  It does disable the PPAs for it as part of the upgrade, so you need to go back and re add the new Tarhir PPAs if you want your Myth TV updating.

Even if you don't update the PPAs once the upgrade is complete myth runs fine even though the MythTV packages are from an older Ubuntu.

After you do update the PPAs it will want to do an "update" and get the Tarhir specific packages.  You can let it do this and when you do the myth-database post install script bug seems to not be in play as I ran it and had no issues.  Maybe that is because I updated the /home/mythtv/.mythtv/config.xml already back on the 12.04 version.

Glad to be on the 14.04 version now and I can stay here happily till the next LTS in 2 years or so.

---

