---
title: "Full install on USB not finding network card"
date: 2022-01-09
forum: Installation &amp; Upgrades
---

### Post by manitislate on 2022-01-09
I installed a fully loaded version of Ubuntu onto my usb card, but it is not seeing my internal components. Trying to get at least the wifi to work.

If I go to settings/wifi it finds nothing. 
However, running sudo lspci finds everything and also sudo lshw -C network, finds my network card.

I looked, but couldn't figure out how to solve this. Any help would be appreciated.

---

### Post by yancek on 2022-01-09
Why don't you post the out put of the commands you refer to in you initial post, someone might have a suggestion.

---

### Post by manitislate on 2022-01-09
> **yancek said:**
> Why don't you post the out put of the commands you refer to in you initial post, someone might have a suggestion.
Thanks for the suggestion:

---

### Post by MAFoElffen on 2022-01-10
I am seeing with that Intel 2725 Wifi Card... that it is supported by Linux Kernel 5.10 and newer. 

What is your current kernel Version?
```

uname -r

```

---

### Post by manitislate on 2022-01-10
> **MAFoElffen said:**
> I am seeing with that Intel 2725 Wifi Card... that it is supported by Linux Kernel 5.10 and newer. 

What is your current kernel Version?
```

uname -r

```

says 5.11.0-27-generic

---

### Post by MAFoElffen on 2022-01-10
I did some research... and Found that a User was still having a promblem with this card (an Intel Card with that Chipset) with Linux kernel 5.11.0-36-generic... Look at the second answer for his solution that worked for him...
[https://askubuntu.com/questions/1295662/intel-wifi-6-ax210-not-working-on-ubuntu-16-04](https://askubuntu.com/questions/1295662/intel-wifi-6-ax210-not-working-on-ubuntu-16-04)

Disclaimer: I don't have this card, so can not personally verify that. But it worked for him. And at least his answer/fix changes it to a backup file, so if it doesn't work, you can just change it back.

EDIT:
But then again... Then I found this from Intel themselves, which says your Kernel should have worked for that...
[https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html)

---

### Post by manitislate on 2022-01-10
> **MAFoElffen said:**
> I did some research... and Found that a User was still having a promblem with this card (an Intel Card with that Chipset) with Linux kernel 5.11.0-36-generic... Look at the second answer for his solution that worked for him...
[https://askubuntu.com/questions/1295662/intel-wifi-6-ax210-not-working-on-ubuntu-16-04](https://askubuntu.com/questions/1295662/intel-wifi-6-ax210-not-working-on-ubuntu-16-04)

Disclaimer: I don't have this card, so can not personally verify that. But it worked for him. And at least his answer/fix changes it to a backup file, so if it doesn't work, you can just change it back.

EDIT:
But then again... Then I found this from Intel themselves, which says your Kernel should have worked for that...
[https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html)

Thanks for your help, this is amazing. Never could have found it on my own.

Just for reference, if anyone else needs to know. I did not have the file iwlwifi-ty-a0-gf-a0-pwm. The closest thing I found was iwlwifi-ty-a0-gf-a0.pnvm. So the name was the same, but the file type wasn't. I ran the script, renaming the pnvm file to a bak file, restarted, and wifi was working.

Thanks again for all your help :)

---

### Post by MAFoElffen on 2022-01-10
You are welcome... 

Please remember to go to the "Thread Tools" link in the upper right of this Page, to mark this as "Solved" so that other Users with the same problem can find a solution to their similar problem.

---

