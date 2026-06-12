---
title: "Unable to upgrade"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Trifud on 2009-12-03
Hi,
I have Ubuntu Network Remix 9.10 but for some time now I cannot upgrade. I launch the upgrade manager and I get a message "Not all updates can be installed" and then I click on Partial Upgrade. After that I get a message "Could not calculate the upgrade. An unresolved problem occurred while calculating the upgrade: E:Unable to correct problems, you have held broken packages."

How could I resolve the problem?

---

### Post by Chrissss on 2009-12-03
Try this...

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by Trifud on 2009-12-03
> **Chrissss said:**
> Try this...

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```

What was that thing? When I run the last command, I got a message that something was wrong with the network. After the upgrade the network disappeared. I restarted and surprise: from the boot menu I chose Ubuntu and in the boot manager I could only see the Windows loader. The Ubuntu had disappeared. But it's OK. I'll make a clean install. You can't learn some OS without reinstalling it many times.

---

