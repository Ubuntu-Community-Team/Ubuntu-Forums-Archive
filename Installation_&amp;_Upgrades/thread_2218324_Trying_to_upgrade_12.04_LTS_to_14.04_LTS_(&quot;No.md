---
title: "Trying to upgrade 12.04 LTS to 14.04 LTS (&quot;No new release found&quot;)"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by jesse-8 on 2014-04-20
I'd heard that I could upgrade between LTS releases so I've held off updating since 12.04. Now that 14.04 has been released I figured it was a good time to upgrade, but for some reason do-release-upgrade can't find the 14.04 LTS release.

If I cat /etc/update-manager/release-upgrades I can see that prompt=lts

If I cat /etc/issue the version number is "Ubuntu 12.04.4 LTS"

Am I missing anything obvious here?

EDIT: **running do-release-upgrade -d allows me to install a development build of 14.04 LTS. I guess I'll go with that now.**

---

### Post by flyingsolo on 2014-04-20
I'm wondering the same. From [this page]("https://help.ubuntu.com/community/UpgradeNotes"), it seems confusing as it recommends sequential upgrade through each version of  Ubuntu but also suggests you can go from one LTS to the next directly. However, my Update Manager is set to notify me of LTS upgrades only and has not yet indicated 14.04 is available (32 bit b/c computer is older).
This, is from the link above:
 [COLOR="#0000CD"]To avoid damaging your running system, upgrading should only be done from one release to the next release (e.g. Ubuntu 12.04 to Ubuntu 12.10) or from one LTS release to the next (e.g. Ubuntu 10.04 LTS to Ubuntu 12.04 LTS). [/COLOR]

---

### Post by mörgæs on 2014-04-20
The option will come in effect when 14.04.1 is released. Until that the "-d" is necessary.

---

### Post by flyingsolo on 2014-04-20
OK, that explains it. It just seems confusing that the home page of Ubuntu would lead one to believe that 14.04 is fully baked, ready to go but the need to use -d for the development build suggests it isn't quite ready for mass distribution.

---

### Post by fantab on 2014-04-20
For that upgrade option to be available your present ubuntu must be uptodate...

---

### Post by mörgæs on 2014-04-20
Nothing is ready at release date, neither Buntu nor Windows nor Mac OS. 
If the installed system is working fine then I always recommend waiting.

---

### Post by jhay2 on 2014-04-20
try to copy this this trusty sources.list file to your /etc/apt/ folder but make a backup first 

this might work . i did this trick when ubuntu 13.10 fails to update the temporary sources.list


and it works without any problem 

Warning: Try it with your own risk

just download my own sources.list.txt and rename to sources.list then copy on your folder /etc/apt

open terminal and update the apt list

$ sudo apt-get update

if updates command finish with no errors 

type 

$ sudo apt-get dist-upgrade


then it will download all needed upgrades for trusty tahr , including kernels and upgraded version of your all packages as well (if available) 

then reboot if done with no errors :) 


please make a backup first ! :)

---

### Post by alainbolomey on 2014-10-26
Thanks for the updated sources.list.txt, that really helped. I am upgrading from SERVER 12 LTS to 14.

---

