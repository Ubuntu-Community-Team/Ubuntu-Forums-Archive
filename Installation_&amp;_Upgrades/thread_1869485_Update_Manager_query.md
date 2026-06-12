---
title: "Update Manager query"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by JAS40 on 2011-10-25
I am a bit puzzled and would like some help with this query please.  I have been using the update manager in Ubuntu 11.10 and to date there have not been too many important updates since I upgraded to 11.10 and it has been working fine.  Today however when I checked for updates it has come back with 203 updates. 3 of them important security updates and 200 appear to be updates for programs which I thought had been removed during the upgrade process. (not sure why I think that, except some games were listed which I thought had gone).  When I try to install the updates it produces an error message explaining that there are unmet dependencies and I should disable all third party repositories.  I have tried this, disabling all the other software sources but to no avail.  I ran 'sudo apt-get check' in a terminal and have been advised to run 'apt-get -f install' to correct unmet dependencies.
I really don't know that much about these things and need to know if this is advisable.  I really don't want to break my system and have to start over.  can anyone offer some help please.  Apologies for the convoluted way of explaining things.

---

### Post by raja.genupula on 2011-10-26
what you are getting while you're doing 

```
sudo apt-get update
``` 

if its ok with no errors then post what are the errors you are getting while you are doing 

```
sudo apt-get upgrade
```

actually for unmet dependencies problem 

```
sudo apt-get install -f 
```

will solve the issues (it gonna install all required dependencies)

all the best

---

### Post by JAS40 on 2011-10-26
> **raja.genupula said:**
> what you are getting while you're doing 

```
sudo apt-get update
``` 

if its ok with no errors then post what are the errors you are getting while you are doing 

```
sudo apt-get upgrade
```

actually for unmet dependencies problem 

```
sudo apt-get install -f 
```

will solve the issues (it gonna install all required dependencies)

all the best

Thankyou very much.  After several attempts to fix 'broken' packages in Synaptic Manager and several more updates everything now appears to be working much as I'm used to.  The 'unmet dependancies' have been resolved and the broken packages fixed and all 200+ updates have been installed and there does not seem to be any adverse conditions.  Many thanks again for your response.  (Watch this space)

---

### Post by raja.genupula on 2011-10-27
I am glad that your issue got solved . please mark the thread as solved from thread tools.

Enjoy the Ubuntu

---

