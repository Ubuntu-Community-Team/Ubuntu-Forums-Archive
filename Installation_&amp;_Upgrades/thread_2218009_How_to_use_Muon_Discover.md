---
title: "How to use Muon Discover"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Manish_Kumar_Singh on 2014-04-19
Yesterday I installed Kubuntu 14.04. When i opened up the muon discover, i showed me the app that's already installed in the laptop. It gave no list of new app like vlc. Although my laptop is connected to wifi, I think the muon is not connected to the net. So how do i do that.
Thanks in advance

---

### Post by ronnoc on 2014-04-21
WHat version of KDE are you running? I believe recent changes to Muon Discover will not show installed apps by default anymore. As for not connected to the net, I'm not sure I understand your question.

---

### Post by wieman01 on 2014-04-21
Could you open Firefox to check if you are online? Second, could you please upload a screenshot so we can see for ourselves what is going on?

---

### Post by htclunde on 2014-07-29
> **wieman01 said:**
> Could you open Firefox to check if you are online? Second, could you please upload a screenshot so we can see for ourselves what is going on?

Same problem here, it show on installed software under "Discover"

Screenshot: [https://plus.google.com/photos/112307079676719497672/albums/6041619438333773585?authkey=CM_PqPyl7qOdMQ](https://plus.google.com/photos/112307079676719497672/albums/6041619438333773585?authkey=CM_PqPyl7qOdMQ)

---

### Post by htclunde on 2014-07-29
Found a fix for it, at least it worked here.

I openend a terminal and run: sudo apt-get update

After that the gui update poped up and did all the updates.

Then I restarted and Muon Discover works

---

