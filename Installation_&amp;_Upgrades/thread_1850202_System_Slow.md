---
title: "System Slow"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-09-26
I am running xubuntu 10.04 and over the last few months the whole system has started to run slower and slower. I only use the laptop for web and e-mail so is there a 'down-grade' I can do to help the system? Would removing other programs help?

Would there be any other reasons for the slow browser response, slow program loading, when I type now it takes a few seconds for the letters to appear on the screen...!!!

Thanks.

---

### Post by lightwarrior on 2011-09-26
I would check:
High CPU temp (old laptops tend to dry thermal paste and suffer cpu throttling if cpu gets too hot).
Hard Disk Integrity: If your hard disk is failing, maybe it is bottlenecking your system if attempting too many read/writes to get a good access.
Swap File non existant... should not be an issue, unless you have less than 512MB of RAM.

---

### Post by raja.genupula on 2011-09-26
> **bigtel said:**
> I am running xubuntu 10.04 and over the last few months the whole system has started to run slower and slower. I only use the laptop for web and e-mail so is there a 'down-grade' I can do to help the system? Would removing other programs help?

Would there be any other reasons for the slow browser response, slow program loading, when I type now it takes a few seconds for the letters to appear on the screen...!!!

Thanks.

are you updating your system frequently? what kind of browser you're using? best browsers are Firefox and Google Chrome in my consideration.Among these two i Vote for Chrome.

---

### Post by mörgæs on 2011-09-26
You could try to keep **top** running in the background while doing your normal work. It will tell in anything is pulling a heavy load on the CPU.

Please also give a hardware description.

---

### Post by bigtel on 2011-09-26
I am updating frequently, the system is currently giving me the option to upgrade to 10.10, but I am reluctant to do it.

Can I ask what **TOP **is?

My system is an Acer Aspire laptop, 1GB memory and 100GB hard drive. The laptop is about 6 years old now and as such is a single core running at 1.2GHz processor speed.

---

### Post by raja.genupula on 2011-09-26
> **bigtel said:**
> I am updating frequently, the system is currently giving me the option to upgrade to 10.10, but I am reluctant to do it.

Can I ask what **TOP **is?

My system is an Acer Aspire laptop, 1GB memory and 100GB hard drive. The laptop is about 6 years old now and as such is a single core running at 1.2GHz processor speed.

top command going to display a detailed information about how much amount of RAM and CPU using by the all applications which are running in your system . 
open your terminal and type top . you are going to get clear idea about what i am saying .

All The Best.

---

### Post by collisionystm on 2011-09-26
install htop. Its much more accurate. 

sudo apt-get install htop

run that from terminal as well. How often do you reboot? My Ubuntu generally needed a nightly reboot because it would dump its ram into the swap partition over night. Therefore making the computer drag like crazy the next day. It was horrible.

---

### Post by bigtel on 2011-09-27
I have installed and run top (and htop) and they are both telling me that Seamonkey is using 74% of the CPU. I am running seamonkey as my e-mail client. The next highest CPU figure is an audio driver at 6%.

How can I take a screen dump of the htop screen?

...also I do reboot nightly.

---

### Post by raja.genupula on 2011-09-27
Hi
Limit the CPU Usage of your Seamonkey. By doing that your issue gonna solved .To do that there is step by step process, look at here.
[http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux](http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux)

---

### Post by SecretCode on 2011-09-27
To get top information posted here, you could select all the text and press Edit > Copy or Shift-Ctrl-C ... but that's a bit fiddly.

Better to run top in batch mode:
```
top -b -n 1 | head -n 20
```

It seems odd that Seamonkey is using so much CPU. Does it stay high if you watch top for a minute?

If you're only using the mail portion of it have you considered moving to Thunderbird?

Also, you should not have to reboot so often!

---

### Post by bigtel on 2011-09-27
If I watch the CPU usage it fluctuates between 75% down to 68%.

I may look at Thunderbird, but I have a lot of settings and mail to move over and I am not sure how to do that.

I will try limiting the CPU usage and see how that works. Thanks for your advice.

---

### Post by SecretCode on 2011-09-27
Do you have any add-ons installed in Seamonkey? It might be worth investigating further what's causing it.

---

### Post by bigtel on 2011-09-27
I think I do - it is worth a check and disabling them I suppose.

Thanks.

---

