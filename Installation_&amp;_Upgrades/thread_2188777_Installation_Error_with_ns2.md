---
title: "Installation Error with ns2"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by jivan.gulhane on 2013-11-19
Ubuntu Forume,
                       sir there is serious problem to install ns2 on ubuntu 12.10 
                       
                       after these "sudo apt-get install ns2" command error through like that""      


                            "Reading package lists... Done
                             Building dependency tree       
                             Reading state information... Done
                           [COLOR=#ff0000]  E: Unable to locate package ns2"[/COLOR]
HOW TO SOLVE IT?

---

### Post by steeldriver on 2013-11-19
Hello and welcome to the forums

Have you made sure that the 'Universe' repository is enabled? If not, please enable it 

[http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository](http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository)

and then update and try again

```

sudo apt-get update

sudo apt-get install ns2

```

---

