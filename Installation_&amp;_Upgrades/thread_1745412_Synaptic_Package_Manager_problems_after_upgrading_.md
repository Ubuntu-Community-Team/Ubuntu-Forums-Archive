---
title: "Synaptic Package Manager problems after upgrading to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by ByTheNine on 2011-05-01
Pre update (10.10) Synaptic Package Manager would allow me to delete residual config files by clicking the Apply button after marking them. Post update, the Apply button does not highlight or allow me to click it when I mark packages for complete removal. 

Any ideas?

---

### Post by StephenWoods69 on 2011-05-01
It seems you have to install or remove something at the same time to remove the residue config in synaptic

---

### Post by ByTheNine on 2011-05-02
> **StephenWoods69 said:**
> It seems you have to install or remove something at the same time to remove the residue config in synaptic

What do you mean? The packages I'm trying to remove are libraries of some sort. I don't even know what they're from. 

In the past with 10.10 I would periodically check SPM for residuals and then just delete them. I wouldn't know what they were from. I'm just wondering if possibly it could be an 11.04 issue and/or what could be done about it.

---

### Post by tedrogers on 2011-05-09
Hello,

I am having this exact problem too.

I have tried removing the residual files from synaptic, when they are marked the green Tick does not highlight, so the removal process cannot be started.

When I try and purge through the terminal, it also fails.

The following command produces no result, as it reports there are no autoremove packages, yet they still remain in Synaptic:

```
sudo apt-get autoremove --purge
```

Any ideas? It's very annoying.

Thanks.

---

### Post by NEXTLOVER on 2011-05-10
Welp, I'm also having the same problem with this & it IS very annoying. I've searched a lil' bit around and it seems this "bug" has been going on since April... & it seems to affect ppl that have upgraded rather than a clean install. So hopefully someone can provide a solution soon.

---

### Post by tedrogers on 2011-05-10
> **NEXTLOVER said:**
> Welp, I'm also having the same problem with this & it IS very annoying. I've searched a lil' bit around and it seems this "bug" has been going on since April... & it seems to affect ppl that have upgraded rather than a clean install. So hopefully someone can provide a solution soon.

Got excited at the new reply then, only to find it is someone else with the same problem and not a solution. 20 lashes for you! :P

---

### Post by ByTheNine on 2011-05-13
Well guys, you'd think since this is happening to several of us there'd be a solution! Maybe there is now, and I'm behind? Anyone?

---

### Post by ByTheNine on 2011-05-15
I found something that may help. It's not a perfect fix to the problems with Synaptic Package Manager, but it seems to be able to remove residuals. It's a program simply called "Remove orphaned packages". You can get it from the Ubuntu Software Center. 

I would prefer that something be done about the problems with SPM, but until then I'm going to use this.

---

### Post by tedrogers on 2011-06-06
I will give that a go and if I'm not back it worked! ;)

---

### Post by 3602 on 2011-06-06
Would Ubuntu Tweak work in this case? Worth a try, eh?

---

