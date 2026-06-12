---
title: "Lubuntu Software Center doesn't load!"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by manishmunikar on 2011-10-15
Hello, I'm a Lubuntu newbie. I installed Lubuntu 11.10 and then installed **Lubuntu** Software Center in it. It was working nicely. Then I decided to install **Ubuntu** Software Center. After finding that Ubuntu Software Center runs very slow in my computer, i decided to uninstall it. Since then, my **Lubuntu** Software Center doesn't load. When I click on 'Lubuntu Software Center' in the Application menu, nothing happens. I reinstalled **Lubuntu** Software Center, but it didn't solve the problem.

I think something must have happened when I uninstalled **Ubuntu** Software Center. Does anyone have any idea of this?

I want to use Lubuntu Software Center. It would be grateful if anyone could solve my problem.

Thanks in advance

---

### Post by amjjawad on 2011-10-16
Hello and Welcome to Ubuntu Forum :)

First thing first, please be advised that Lubuntu Software Center (LSC) is under development and as of today, there is no stable version.

Now, to install LSC, please do this:

```
sudo add-apt-repository ppa:lubuntu-desktop/ppas
```
```
udo apt-get update
```
```
sudo apt-get install lubuntu-software-center
```

To make sure LSC is still on your system, please open LXTerminal and type:
```
lubuntu-software-center
```

What gives?

I personally don't like any software center, I just use the terminal and Synaptic when I have to. But that's me :)

---

