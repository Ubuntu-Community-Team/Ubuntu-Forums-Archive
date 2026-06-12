---
title: "Software Updates - Non Certified,why?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by waynepr72 on 2007-05-14
I have recently decided to install Ubuntu and move off Windows due to the vast number of Spyware and viruses we here everyday out there that appears to hit XP. So I have read that Linux is a more solid OS with less vunerabilities to exploit, hense less chance of been hit with something nasty.

Anyway thats there reason I have here.  I would like to know why in Ubuntu we are given software update notices (Icon at top of desktop) and then when you go to install, for example the other day I have one for Automatix, I was then warned when I went to install it was not a certified update and could pose a threat to my system etc, etc if I continue.

Why are these types of updates allowed unless they have been checked to be safe to do so. I understand installing software poses risks but an official update notice you would expect to not pose this type of risk surely?

Can anyone shed any light on my concerns here?

Thanks,

Wayne

---

### Post by x64Jimbo on 2007-05-14
Sometimes if you follow a tutorial to tell you how to install some cool new piece of software, or if a script you run is poorly programmed, you can have new repositories added to your repo list but not have installed the gpg key necessary to ensure that the file integrity is good. If you keep your installation plain vanilla and don't install anything besides what you get in the normal repositories, you won't get these warnings.

---

### Post by ajgreeny on 2007-05-14
x64Jimbo is basically correct. but once you add anything outside the official ubuntu repositories there will often be updates with these warnings showing from these.  You look to have used Automatix and that is probably the source of your apparent "Not certified" message.  However if you keep to trusted repositories such as Automaix or Easyubuntu's medibuntu repos, there shouldn't be any reason to feel very vulnerable, so go ahead with your updates.  Just make sure you don't add any repos that you can find no information about, and always check on these forums for information first.

---

### Post by x64Jimbo on 2007-05-14
Well, something needs to be said here... Without the gpg key, there's really no way to be sure that you aren't being MITM'd when you get your updates. The key ensures that the packages are coming from who they are supposed to. They are digitally signed. Merely ensuring that the repository URLs are "trusted" is not enough. You need to install the gpg keys for any repositories that you use to ensure that the packages are always coming from the source that they claim to.

---

### Post by ajgreeny on 2007-05-16
I agree and did not mean you could or should use repos from anywhere.  If you stick with easyubuntu or automatix the gpg key instruction are all part of the instructions I think.  They certainly are for easyubuntu, anyway.  Never used automatix so can't say about that for sure.

---

