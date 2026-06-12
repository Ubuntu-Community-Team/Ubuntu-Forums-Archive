---
title: "Wireless problem / Empty Hardware Drivers List"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by s4udem on 2010-03-31
Brand new to Ubuntu.  Installed 9.10.  Install went smoothly, except, of course, for wireless.  Why is wireless always the hardest thing?

If I run from the Live CD, the System->Administration->Hardware Drivers utility will show me a list of drivers.  I selected Broadcom STA and activated it, and my wireless worked.  Woot!  Woot!.  

But if I run the installed version from my laptop, the Hardware Drivers utility comes up  completely empty.  There is nothing for me to choose/activate, and my wireless card does not work.

Any ideas?

---

### Post by JustinR on 2010-03-31
Hi,

Unfortunately, I've had this problem before, with the exact same wireless driver.
After I installed 9.10 I knew I needed an Nvidia and Broadcom STA driver but it didn't show up -  but it did in previous 9.10 installations.

It fixed itself after I reinstalled 9.10 but I'm sure you can download the packages from Ubuntu online:

Broadcom Wireless STA Driver:

[http://packages.ubuntu.com/lucid/broadcom-sta-common](http://packages.ubuntu.com/lucid/broadcom-sta-common)

Couldn't find the 9.10 driver online - but if the 10.04 driver doesn't work I still have the original 9.10 driver .deb.

Goodluck!

---

### Post by mcoleman44 on 2010-03-31
sudo apt-get update
sudo apt-get upgrade
sudo reboot
It will be listed under hardware drivers now.

---

### Post by s4udem on 2010-04-01
Thank you!  Thank you!  Thank you!  I did the apt-get update stuff and it worked like a charm.

Back story:  I've been struggling with this** all week**.  NDISWrappers.  firmware.  this that.  whatever.  Actually re-installed Ubuntu to get a clean slate before posting here.  It was an aggravating week and I am very grateful for your help.  Laptop now boots in 50 seconds.  XP was taking several minutes.  I am doing the dance of joy.

---

### Post by leorolla on 2010-04-13
Nice to see a happy newbie post!

After a few weeks of Ubuntu I couldn't even hear the sound of Windows login anymore. After a few months I realized that I was booitng Windows every 20 days, running the scheduled anti-virus scan and tinkering with Wubi. Now Windows is fired for good.

---

### Post by skikir on 2010-04-14
> **mcoleman44 said:**
> sudo apt-get update
sudo apt-get upgrade
sudo reboot
It will be listed under hardware drivers now.


Can someone translate this for me?  I have the same problem and don't know what he's talking about.

TIA

---

### Post by howefield on 2010-04-14
> **skikir said:**
> Can someone translate this for me?  I have the same problem and don't know what he's talking about.

TIA

Open a terminal (Applications > Accessories > Terminal) and type the following

```
sudo apt-get update
```

Enter your password, you won't see it being typed but it is.

Once that has completed, enter the following into the same terminal (although you shouldn't have to, just to get the the hardware drivers)

```
sudo apt-get upgrade
```

Finish off with a reboot of your machine, and try System  > Administration > Hardware Drivers again.

---

### Post by roundhead on 2010-04-14
Thanks for the post. I am also new to Ubuntu and have been searching all week for an answer to the wireless problem. I found this thread the most helpful. I am almost wireless but the icon just runs and runs even though I am right next to the router. It keeps asking for the password and I keep typing it in but the icon just keeps spinning. any ideas? thanks

---

### Post by mcoleman44 on 2010-04-14
What drivers were listed when you opened hardware drivers? There were most likely two wirelsess drivers listed.

---

### Post by roundhead on 2010-04-14
Thanks, there was another Broadcom driver B43 listed. I will try to deactivate that. your in the ville? I lived there for 4 years...great city. I live in Cincy now. I will try and repost

---

### Post by roundhead on 2010-04-14
Now it is only showing the STA driver and no longer can find the B43 driver. but it still does not work...just keeps running

---

### Post by mcoleman44 on 2010-04-14
Do you know what wireless card you have? Did you activate STA or B43? 
```
lspci
```
That will show you which wireless card you have. It will be listed somewhere near the bottom.
Yeah, I live in the Ville alright, I love it. Do you  miss it?

---

### Post by mcoleman44 on 2010-04-14
Did you  restart after you deactivated STA?

---

### Post by roundhead on 2010-04-14
actually I activated the B43 first and then the STA (I know very little about computers) but I really like Ubuntu and the forums are great. It looks like "network controller" is Broadcom Corp BCM 4312 but I do not know if that is the card or the router. what is the card called?
Yeah we really miss Louisville...great parks and clean city. great for bicycles and coffee

---

### Post by mcoleman44 on 2010-04-14
Thats the card. Did you restart after you activated the STA? It takes a couple of restarts sometimes.
Does your router have a password? Can you get a connection using ethernet?

---

### Post by roundhead on 2010-04-14
ok I restarted again. I can connect with the ethernet fine. I just wonder if the other driver is still active and in conflict with the STA. I dont know...I may reinstall because now Dell wants the password everytime I start up and the Network manager wants to unlock the keyring everytime. its starting to act kinda funny

---

### Post by mcoleman44 on 2010-04-14
Im not really sure what to tell you to be honest, Im hoping someone a little more knowledgeable will join in.

---

### Post by roundhead on 2010-04-14
OK thanks for helping. You got me this far which is bettern than where I was before. I may try to start a new thread to see if that draws some interest. Thanks, enjoy Spring
Stewart

---

### Post by leorolla on 2010-04-15
Let me see if I got it right.

Now you have wireless ineternet working fine, but what bothers you is that it asks for the password to unlock the keyring everytime you login?

---

