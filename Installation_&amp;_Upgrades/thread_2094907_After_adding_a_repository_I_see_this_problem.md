---
title: "After adding a repository I see this problem"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by sinaphysics on 2012-12-15
I want to upgrade to gnome 3.6 so I add a repository and try it but when I want to use ```
sudo apt-get update
``` 

I receive this error

```
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
E: The list of sources could not be read.

``` 

How can I fix this problem ?

---

### Post by jerome1232 on 2012-12-15
sounds like the line is malformed, what does it say?

```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
```

---

### Post by sinaphysics on 2012-12-15
I fix it myself. I'm using for 2 year Ubuntu but always I feel amateur in ubuntu  but I fix it. Maybe it's too easy.
> Sudo rm /etc/apt/sources.list.d/gnome3-team-gnome3-precise.listand then run

> sudo apt-get update

thank you [jerome1232]("http://ubuntuforums.org/member.php?u=453029"). Is it possible to explain what "cat" do ?

---

### Post by ibjsb4 on 2012-12-15
Kittie command

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cat&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cat&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by jerome1232 on 2012-12-15
> **sinaphysics said:**
> I fix it myself. I'm using for 2 year Ubuntu but always I feel amateur in ubuntu  but I fix it. Maybe it's too easy.
and then run



thank you [jerome1232]("http://ubuntuforums.org/member.php?u=453029"). Is it possible to explain what "cat" do ?

it's a command used to concatenate files, meaning join them together, however it's also frequently used to simply read a files contents to standard output (your terminal).

That's all my command was doing, was reading the contents of the troublesome repository file and displaying them in your terminal.

---

