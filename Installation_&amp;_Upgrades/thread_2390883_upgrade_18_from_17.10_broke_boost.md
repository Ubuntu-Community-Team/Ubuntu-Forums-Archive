---
title: "upgrade 18 from 17.10 broke boost"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by doktour on 2018-05-03
I have been running a cryptocurrency node on my Ubuntu for some time now, since version 14. Each dist-upgrade went ok until this one. It seems the upgrade from 17.10 to 18 had remove or replaced boost 1.62 with boost 1.65 and somehow broke the server. (cannot find boost libraries error). Worse still the original src will no longer compile.

I must upgrade still another machine running the same crypto server, but before I do, can someone tell me how to prevent the upgrade from replacing the 1.62 version of boost, or perhaps offer advice as to why the new version seems not to be downward compatible.

Thank you

---

### Post by dino99 on 2018-05-03
boost1.65 is in use, but 1.62 is still found into the archive (does not know if both can be installed together without trouble)

---

### Post by doktour on 2018-05-04
Thank you dino99 I finally figured that out :) and yes, they both seem to be able to co-exist. (Don't allow the upgrade to remove old programs allows old boost to remain)

For the sake of others that may have the issue, here is my solution *_if you already purged the old boost during the upgrade_*:

Since pinning seems to be broken in the version 18 upgrade, it can be done using aptitude: 

[B][I]apt-get install  libboost-*1.62-dev

[/I][/B]It is also a good idea to mark libboost1.62 as manual to prevent autoremove from deleting it: [B][I]

sudo apt-mark manual libboost*1.62*[/I][/B]

I also discovered that the newly installed version of openssl is not backward compatible, which caused the compile errors I referenced above. To fix this required a little more work:
1, Uninstall libssl-dev 
2. Download an older version of openssl (I used openssl 1.0.2g)
3. Compile and install the older version of openssl - This will place them in /usr/local/ssl
4. In my case, the program I was compiling was unable to find the needed files in /usr/local/ssl directory, so I had to move the files to there default location.
Here is what I did:
[I][B]
cd /usr/local/ssl/lib
sudo cp lib*.* /lib/x86_64-linux-gnu

cd /usr/local/ssl
sudo cp -r private /etc/ssl
sudo cp -r openssl.cnf /etc/ssl
sudo cp -r certs /etc/ssl

cd /usr/local/ssl/include
sudo cp -R openssl /usr/include

cd /usr/local/ssl/bin
sudo cp * /usr/bin[/B]

[/I]After doing this, the program complied properly and ran normally.

I must have missed the memo on the lack of backward compatibility of the upgraded programs :)

Hope this helps someone else facing this issue.

---

