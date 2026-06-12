---
title: "Upgrade froze in middle, and now &quot;New Distribution&quot; message is not in Update Manager?"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by Riothamus on 2012-06-09
I was running Ubuntu on my desktop. I think it was version 10. something, but unfortunately I can't be sure what it was now due to the failed upgrade. I chose to hold off on upgrading to 11.01, and when I found out that 12.04 LTS was available, I decided it was time to upgrade. But the upgrade manager only said version 11.10 was available, so I figured you had to upgrade to that first, and then to 12.04. So I began the upgrade.

It said it would take upwards of 8 hours and it listed about 1,000 new files it had to download. I figured that was because I'd put off upgrading for so long, so I went ahead. After several hours it stopped, saying it couldn't download anymore packages and to check my Internet connection. I checked it and it was working fine, so I ran Update Manager, clicked Check twice so that the Upgrade button would appear, and began the upgrade again. After a few minutes, the same message came up, saying it couldn't establish a connection. This was late last night at about 3am, so I figured maybe the server was just performing maintenance or something. So I left the computer on all night and decided to try again today.

Now when I try, I keep clicking Check on the Update Manager, and no information about a new distribution being available is coming up. I tried restarting the computer and trying again, and still nothing. I've also tried typing sudo apt-get dist-upgrade, and it says this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Typing cat /etc/lsb-release lists the current version as 11.04, but I'm fairly certain the upgrade was never completed, as the freeze happened in the middle of downloading files, and it never ran the Applying Changes part or anything after that. So I know for sure the distribution wasn't upgraded.

Any ideas on how I can fix this?

---

### Post by Riothamus on 2012-06-11
NO ONE has any ideas???

---

