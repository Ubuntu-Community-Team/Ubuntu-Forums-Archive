---
title: "MySecureShell on Ubuntu 14.04"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by David_Datte on 2014-11-04
Hi,

I've upgraded my server from an Ubuntu 12.04 LTS to a 14.04 LTS recently and I had installed on the 12.04 MySecureShell for SFTP which worked perfectly.
Now on the 14.04 everything seems to work well except that I have no more binaries nor services to access MySercureShell.

I need to update some configuration params and I need to restart MySecureShell but I can't get hold on anything related to it except for the conf file in /etc/ssh/sftp_config.
And of course with official repo there are no version for 14.04.

Anyone has any idea on how I can restart MySecureShell or reinstall it ?

Thanks for any answers.

David

---

### Post by David_Datte on 2014-11-04
Resolved.

I did an "sftp-verif" to check the instalation and resolved the problem found : the binaries under /usr/bin and /usr/sbin were absent I symlinked them to the /bin/MySecureShell which I found was here.
Then I did an "sftp reload" and the config was reloaded and everything works fine.

Hopes that helps.

David

---

