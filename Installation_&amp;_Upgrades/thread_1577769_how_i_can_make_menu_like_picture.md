---
title: "how i can make menu like picture ?"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by m-r-r on 2010-09-19
Hello, i want make some menu for users to do some works like restart system, restart, shutdown, changing system ip address and etc. but i don't know how.
can you help me ?

i want do like this :
[IMG]http://vzz.ir/files/yho6ur6nalsqpngzalqn.png[/IMG]

thanks.

---

### Post by s5GbJReJ on 2010-09-19
You can probably make a menu system like this by using shell scripts. Your best bet is just plain old bash - there's a tutorial on bash shell scripting/programming here: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by sisco311 on 2010-09-19
If you are looking for a fancier menu, then try dialog. It's in the repos. It provides a method of displaying several different types of dialog boxes from shell scripts.

```
dialog --menu Menu 20 40 5 [W] "How to" [U] "Global admin" [Q] "Exit"
```

[http://www.linuxjournal.com/article/2807]("http://www.linuxjournal.com/article/2807")

---

