---
title: "update-manager from commandline"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by zakhooi on 2007-01-17
Hi,

Since we have a server running Ubuntu, we don't use it's desktop-environment that often for daily work.
Because of that. we are not aware of any available updates reported by the update-manager.

I was wondering whether there is a console command/tool that can check for the same updates as the update-manager so that we can write a script that does this check and send us an email to notify us about any available upgrades.

Thanks in advance

---

### Post by aidanr on 2007-01-17
first install sendemail
```
wget http://ftp.uk.debian.org/debian/pool/main/s/sendemail/sendemail_1.55-1_all.deb
sudo dpkg -i sendemail_1.55-1_all.deb
```
_**or**_ if you're not sending from gmail or don't need to use tls (the older version in the repos doesn't support tls, therefore doesn't support gmail)
```
sudo apt-get install sendemail
```

next, the script
```
sudo nano /usr/local/bin/email_updates
```
```
#!/bin/bash

apt-get update && apt-get -s upgrade > /tmp/updates.txt && sendEmail -f sender@gmail.com -t receiver@yahoo.co.uk -a /tmp/updates.txt -u updates -m see attachment -xu username -xp password -s smtp.gmail.com:25 -o tls=yes
```
ctrl+o to save, ctrl+x to exit
```
sudo chmod +x /usr/local/bin/email_updates
```

apt-get update - updates from the repos
apt-get -s upgrade - installs available updates, the -s means simulate, which means it will print out as though it has run through the process but instead it just simulated it
> /tmp/updates.txt - writes the output of the last command to a text file
see "man sendEmail" for explanations of the various switches

then you can use cron to automatically run the script once a day or once a week or whatever, also you have to run it  with sudo, i don't know a lot about cron so you'll have to figure that part out yourself

---

### Post by zakhooi on 2007-01-17
Thanks for the hint, but this script is sending a mail every time it's executed and that's not what I'm looking for.

I rather have a solution where a script (can be triggered by cron) will check for updates and ONLY IF there are updates, sends me an email just to trigger me to check out the update-manager.

I hope this clearifies...

Thanks in advance

---

### Post by aidanr on 2007-01-17
yeah i searched for something like that and didn't find anything, maybe someone else has a better suggestion, good luck

---

### Post by aidanr on 2007-01-17
another idea might be subscribing to the ubuntu security announcement mailing list
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

---

### Post by zakhooi on 2007-01-18
anyone else who can help me out?

---

### Post by zakhooi on 2007-01-25
There must be some sysadmin out there that must have come across this same question.....

Please help me out here, it's weird that a proper distro like Ubuntu hasn't got a tool for this....

---

