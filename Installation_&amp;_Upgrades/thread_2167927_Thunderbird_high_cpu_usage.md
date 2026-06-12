---
title: "Thunderbird high cpu usage"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by fade-wanadoo on 2013-08-15
I have a big Thundrebird mailbox (8GB). On Fedora Thunderbird did well but as soon I changed to Ubuntu 13.04, Thunderbird 17.0.8 gone crazy on cpu with the following symptoms :
[LIST]
[*]quickly increase cpu usage up to 100% of one core (even if you have an overclocked 4GHz cpu :)) 
[*]quick memory increase 
[*]not so much I/O 
[*]works slowly but still managing mailboxes 
[/LIST]

After searching the web I found that many people had the problem but none found the solution.

In the option, go to the advanced tab and turn off, in the "advanced configuration" the option called "activate search and global indexation". And then restart Thunderbird (you have to close its window and then kill it in the task manager).

I translated the option name from french so maybe it's not exactly the name, but you'll find out.

---

### Post by andrew-beals on 2014-02-19
In English, the path is Edit->Preferences->Advanced->General->Enable Global Search and Indexer

---

