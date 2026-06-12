---
title: "Package authentication error"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by RoverSM on 2012-03-16
Hi all,
       I have setup a debian repository on one of my servers. 
i have signed one package using the dpkg-sig command. The client machine 
is able to fetch the servers address without any error on running the apt-get update command.
I have also exported the gpg key and it shows under the apt-key list command.
But when i try to install a package that i have signed the following error
is shown. It is an urgent project requirement , so any help would be appreciated.


[B]WARNING: The following packages cannot be authenticated!
Install these packages without verification [y/N]?[/B]

---

### Post by raja.genupula on 2012-03-16
yeah they are third-party software . say yes if you're sure with what software you're installing . other wise say no .

---

### Post by RoverSM on 2012-03-19
hi Raja,
      I have already signed the packge on my server but still this error comes up, that is my question.

---

