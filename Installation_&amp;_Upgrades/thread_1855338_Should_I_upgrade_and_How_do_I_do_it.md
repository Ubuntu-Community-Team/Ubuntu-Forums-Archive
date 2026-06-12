---
title: "Should I upgrade and How do I do it???"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by JoshuaMiller0 on 2011-10-06
I have recently been thinking of upgrading Ubuntu 10.04 to Ubuntu 10.10. I refuse to use 11.04 as it is the newest version and therefore probably the buggiest and least stable.

From what I have heard 10.10 is better and I will go with that unless I am convinced otherwise. 

But the main reason for this thread was I am unsure how to install 10.10 running off a 10.04.

---

### Post by dino99 on 2011-10-06
sudo gedit /etc/apt/sources.list

change "lucid" by "maverick"

then update, upgrade, that it :)

---

### Post by mastablasta on 2011-10-06
in software manager click upgrade. it will upgrade to 10.10.

---

### Post by JoshuaMiller0 on 2011-10-06
> **dino99 said:**
> 
change "lucid" by "maverick"


I do not understand.

Do you mean change "lucid" ***to*** "maverick"?

If not what did you mean?

If so which lucid? there are hundreds! all of them?
One of them?

PS. I am very new to customizing things on Ubuntu and you must be very clear and specific for me to make sense of things and do them correctly.

---

### Post by JoshuaMiller0 on 2011-10-06
> **mastablasta said:**
> in software manager click upgrade. it will upgrade to 10.10.

I was told specifically not to do it this way as I was told "It is not a good way to do it"

---

### Post by lcman on 2011-10-06
> **JoshuaMiller0 said:**
> I have recently been thinking of upgrading Ubuntu 10.04 to Ubuntu 10.10. I refuse to use 11.04 as it is the newest version and therefore probably the buggiest and least stable.

From what I have heard 10.10 is better and I will go with that unless I am convinced otherwise. 

But the main reason for this thread was I am unsure how to install 10.10 running off a 10.04.

It's not buggy at all and you should use it instead of 10.10 because the latest stable version is always best. Maybe you won't like Unity but hey, you can choose classic mode anytime!

Or do not upgrade at all! 10.04 is LTS therefore much better than 10.10.

So, either 11.04 or 10.04! But, it's up to you really...:guitar:

---

### Post by lcman on 2011-10-06
> **JoshuaMiller0 said:**
> I do not understand.

Do you mean change "lucid" ***to*** "maverick"?

If not what did you mean?

If so which lucid? there are hundreds! all of them?
One of them?

PS. I am very new to customizing things on Ubuntu and you must be very clear and specific for me to make sense of things and do them correctly.

Everywhere you see lucid, you change it to maverick.

EDIT: oh and, apt-get update && apt-get upgrade

---

### Post by JoshuaMiller0 on 2011-10-06
> **lcman said:**
> ...because the latest stable version is always best....


That is exactly why I wish to use 10.10

> **lcman said:**
> Everywhere you see lucid, you change it to maverick.


So I can go ctrl+F and go find and replace and find lucid and replace with maverick?

> **lcman said:**
> EDIT: oh and, apt-get update && apt-get upgrade

So after I have replaced all "lucid"s with "maverick"s I enter that into terminal?

And in all these steps it does not mention what version I want to update to and I would presume it would automatically go to the latest (11.04). Have you forgotten something or do you do it after "apt-get update && apt-get upgrade"?

And finally in "apt-get update && apt-get upgrade" is there meant to be a 'sudo' in front of that?

Overall thanks for your help so far! Keep it up!

---

### Post by mastablasta on 2011-10-06
> **JoshuaMiller0 said:**
> I was told specifically not to do it this way as I was told "It is not a good way to do it"
 
you were told not to do it in a way that the designer of this system made it? 
 
well if you have any PPA you need to disable them first and do an upgrade. But if you don't then it will just upgrade the OS. It's what it is ment to do. ok maybe some older things get left behind. but that is not necessarily bad.
 
i upgraded like this form 9.10 to 10.04 and then to partial 10.10 (long story) and then to full 10.10 . it all worked well. 
 
still in the end i set up Kubuntu :-)
 
another option is to cretae spearate HOME partition, move files form home folder to it and then you can just reinstall the OS every time instead of upgrade. This will leave you data intact. it's like having separate C (with windows) and D (with data) disk

---

### Post by JoshuaMiller0 on 2011-10-06
> **mastablasta said:**
> 
well if you have any PPA you need to disable them first and do an upgrade.


What is PPA?

> **mastablasta said:**
> another option is to cretae spearate HOME partition, move files form home folder to it and then you can just reinstall the OS every time instead of upgrade.

How would I do this?

---

