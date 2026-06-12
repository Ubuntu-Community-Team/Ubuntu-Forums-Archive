---
title: "Does an app upgrade if you remove the repo in the sources list?"
date: 2021-02-12
forum: Installation &amp; Upgrades
---

### Post by windows-to-linux on 2021-02-12
Hello, and thanks for taking the time to answer my question.

If I add a ppa to my sources.list.d, install an application and then remove the ppa from my sources, will the application still update when I run the update & update command in the Terminal? The application is not found/from the Canonical or ubuntu community sources. Is it safe to assume applications check on their own for upgrades when you open/run the application? 


-Greg

---

### Post by howefield on 2021-02-12
No, if you remove the ppa the application will not be aware of an update therefore you will stick with the version that you installed.

---

### Post by windows-to-linux on 2021-02-12
I didn't see how to like your answer so I'll just say thank you very much!!!

---

### Post by tea for one on 2021-02-12
> **windows-to-linux said:**
> I didn't see how to like your answer so I'll just say thank you very much!!!

It is better to mark the thread as solved so other users can reap the benefit of the answer.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

