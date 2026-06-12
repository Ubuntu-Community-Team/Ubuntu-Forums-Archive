---
title: "Is something terribly wrong with my 7.10 installation?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by mhall on 2008-01-06
**Hi, fellow Ubuntu users.**

Today, I installed Ubuntu Gutsy i386 on my Acer Aspire 5102WLMi laptop. I've been using both Edgy and Feisty before, but now **everything** seems to go wrong.

1. **I cannot install one single package normally** in a terminal. My computer can't find neither msttcorefonts nor irssi. Am I wrong when I say that these packages have been perfectly accessable directly after installing 6.10 and 7.04?

2. **I cannot install Automatix2** (and this has never every been any problem before). It says something about dependency packages, and unfortunately I haven't had this kind of problem before so I don't know how to solve it.

[I]"The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: tango-icon-theme but it is not installable"[/I]

3. **I cannot install the Adobe Flash-plugin** for Firefox. This has not been a problem since 6.10, WHY the hell doesn't it work now? *"Cannot find flashplugin-nonfree"*.

Now, is 7.10 the most buggy release I've ever installed in my entire life, or what the hell is wrong? I'm really stressed about this, as I have to get my computer to work properly with all of the applications I need tonight, as I'm moving back to my apartment after spending Christmas break at my parents' house.

Thank you on beforehand,
Martin

---

### Post by PmDematagoda on 2008-01-06
All your problems are due to one thing:-
**Missing repositories**

To be able to install the packages you need, you have to do these two things:-
1) Open Software Sources in System>Administration>Software Sources. When it opens, enable all the the Ubuntu Software repositories, then close the window and reload the sources list when asked.

2) Add the Medibuntu repositories by following the instructions given [here]("https://help.ubuntu.com/community/Medibuntu"), after which you execute:-
```
sudo apt-get update
```

After those two steps are done, your problems should be solved:).

---

### Post by mhall on 2008-01-06
> **PmDematagoda said:**
> All your problems are due to one thing:-
**Missing repositories**

To be able to install the packages you need, you have to do these two things:-
1) Open Software Sources in System>Administration>Software Sources. When it opens, enable all the the Ubuntu Software repositories, then close the window and reload the sources list when asked.

2) Add the Medibuntu repositories by following the instructions given [here]("https://help.ubuntu.com/community/Medibuntu"), after which you execute:-
```
sudo apt-get update
```

After those two steps are done, your problems should be solved:).
Oh, thank you very much. That pretty much solved my problems.

Although the Flash plugin seems pretty weird? It doesn't work properly at all, and I don't know why since it worked just fine in Feisty... It pretty much ***** up the entire Flash things totally, everything is misplaced and no buttons can be clicked on.

Do you have any idea why this happens?

And once again, thanks for your fast repliance.

---

