---
title: "Switch between java installed?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by erikja on 2010-05-07
Hi.

How do I switch between different java's installed here on ubuntu 10.04 ?

---

### Post by QIII on 2010-05-07
Do you mean tell your machine to use Sun Java instead of OpenJDK or visa versa?

I don't use OpenJDK, so I can't tell you.  But to get Sun Java to be your alternative, open the terminal and type

```
[FONT=Verdana][SIZE=1]update-java-alternatives -s sun-6-java
```

Someone will be by shortly to tell you how to get it back to OpenJDK.

[/SIZE][/FONT]

---

### Post by erikja on 2010-05-07
> **QIII said:**
> Do you mean tell your machine to use Sun Java instead of OpenJDK or visa versa?

I don't use OpenJDK, so I can't tell you.  But to get Sun Java to be your alternative, open the terminal and type

```
[FONT=Verdana][SIZE=1]update-java-alternatives -s sun-6-java
```

Someone will be by shortly to tell you how to get it back to OpenJDK.

[/SIZE][/FONT]

Thank you for your reply. It's the vice versa I need :-)
From Sun Java to OpenJDK.
Trust that someone will give me the needed information here, TIA.

---

### Post by 2hot6ft2 on 2010-05-08
Is this what you're waiting for?
```
sudo update-java-alternatives -s java-6-openjdk
```

More info in the help pages here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
:guitar:

---

