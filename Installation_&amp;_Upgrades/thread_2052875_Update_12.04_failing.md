---
title: "Update 12.04 failing"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by fathercisco on 2012-09-04
Hi All,

I am having an immense amount of trouble getting my 12.04 to update and am hoping that one of you good people will be able to help.
So far i have trawled the forum and tried sudo apt-get update and removing recommended updates all to no avail!.
I am new to ubuntu and linux in general and would really appreciate any help anybody can give.
Thank you in advance.

---

### Post by dino99 on 2012-09-04
usually speaking, an issue is half solved by asking the good question :p

what is yours ?  saying "have huge problems" does not tell much about it ;)  Do you get errors ? which ?

you can install synaptic for easier experience:

```
sudo apt-get install synaptic
```

then running it: ```
sudo synaptic
```

you still can reading the community help link below.

---

### Post by fathercisco on 2012-09-05
Hi 

Yes i'm sorry that wasn't very descriptive was it?. :P
The issue i am having is the untrusted packages issue, although most people that have experienced this have a list of one or two apps that won't update whereas i have a very long list, in fact it appears to me that most of the updates required are listed.

I have tried 
```
sudo apt-get update
```

But this returns "no known address " for every line of the update ( i apologise at this point if my explanation is making things less clear).
I can copy the exact output if that would make things easier.

---

### Post by Frogs Hair on 2012-09-05
Posting the entire output may offer some clues .

---

### Post by fathercisco on 2012-09-06
Hi All,

Thank you for your time and help, i have gone with dino99's sugestion of synaptic and that appears to have done the trick although there are some packages that it can't find, however in order that i learn something from this could anybody explain to me why this worked and update manager did not ?.

Again thank-you all for your help.

---

