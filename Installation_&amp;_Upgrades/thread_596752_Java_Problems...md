---
title: "Java Problems.."
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by iamjfarrell on 2007-10-29
I have gutsy gibbon and I just got sun JAVA 6 and it is not working 100% correctly. Like when I go into a chat room or something it won't scroll and freezes a lot. I did an about:plugin in firefox it says something about gcj under description. If you need any other info let me know. I have also looked at errors in the error console and the java errors are layer backgrounds if that means anything.

---

### Post by taurus on 2007-10-29
How did you install Sun java 6?  What's the output of this command from a terminal?

```
java -version
```

---

### Post by iamjfarrell on 2007-10-29
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

and I believe I installed it using the terminal

---

### Post by taurus on 2007-10-29
Did you also remember to install the plugin?

```
sudo apt-get install sun-java6-plugin
```
Restart firefox and see if you now have Sun java 6 in the plugins.

```
about:plugins
```

---

### Post by iamjfarrell on 2007-10-29
I have java 6 in the plugins. but so is the GCJ java thing too.

---

