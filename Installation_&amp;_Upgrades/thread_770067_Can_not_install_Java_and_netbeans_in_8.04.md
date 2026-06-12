---
title: "Can not install Java and netbeans in 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by chicken_java on 2008-04-27
Dear Ubuntu team,
When i use version 7.10, i can install java and netbeans perfectly. However, when i upgrade to version 8.04, java and netbeans can not install automatically as version 7.10.
So, how can i install them on version 8.04?

---

### Post by LaRoza on 2008-04-27
```

sudo apt-get update && sudo aptitude install sun-java6-jdk netbeans

```

First, enable all available applications in Add/Remove then run that command.

---

