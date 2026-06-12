---
title: "Rolling Screen Problem"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by jazzmasterd on 2012-04-23
I just installed lubuntu on my old gateway tablet pc. I installed the lubuntu 11.10. Everything was working well, I upgraded all the security stuffs that it asked me to and went to class. 

When I returned the entire screen was 'flipping' or 'scrolling'. What in the world is going on? How do I even begin tackling this problem? 

Thank you in advance for assistance with this. 

-John

---

### Post by Rex Bouwense on 2012-04-23
I'll bet that was a surprise.  Did this occur after the updates were installed?  Can you reboot?  Have you done so?

---

### Post by jazzmasterd on 2012-04-23
Yes a surprise, and painful to look at. :) 

Yes, I have rebooted, shut down, and started up several times. 

When I left everything seemed completely normal and nothing was downloading or updating to the best of my knowledge.

I can move the cursor around the screen and open files normally. Its just really difficult because the screen is 'scrolling'.

---

### Post by Rex Bouwense on 2012-04-23
OK.  Did you try Lubuntu on your machine before you installed to see if everything would work?  I know the next questions are or sound simple but did you check the md5sum on the download and burn the ISO at the lowest possible speed?  Since you just installed and you probably don't have any data on your machine yet, it might be simpler and quiker to just re-install.
I also assume that whatever OS was on your machine was working and you could boot it without the flipping screen.  Is that correct?

---

### Post by jazzmasterd on 2012-04-23
You will not insult me with any simple questions; this is my first time doing anything outside of windows. :) 

No I did not try lubuntu first, I had nothing of value on the machine and it was just sitting in the closet so I figured I'd give linux a shot so I just went for the full install right out of the gate. 

I don't know what it means to check the md5sum. I used the default setting for burn speed on newly downloaded 'infrarecorder'.

Windows XP tablet edition was working fine before I changed OS.

I am currently re-installing the OS.

---

### Post by Rex Bouwense on 2012-04-23
For future reference,  it is a good idea (although not really necessary) to take the linux OS "for a spin"just to see if it plays well with your hardware.  There are over 300 different Linux Operating Systems out there and if one doesn't work or you don't like it, others can be tried and all it costs you is a CD or your time if you are using a flash drive.

OK, this site will tell you all about the md5sum.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
To put it in a nut shell, it just checks to see if the download was good.

Burning the ISO at the lowest possible speed just increases the chance that the burn will be good.  Many people don't even bother with that any more.

Good luck.

---

### Post by jazzmasterd on 2012-04-23
Ok, the problem starts after I do the security upgrades. Should I just not do any of them?

---

### Post by Rex Bouwense on 2012-04-23
If you are going to get on the Internet, security updates are a must.  As you know from Windows they patch holes or fix bugs.
Have you perhaps changed the refresh rate?  I have just completed a search for stopping a rolling screen and come up empty.  Not sure what else I can tell you.  Let me do some more searching.

---

### Post by jazzmasterd on 2012-04-23
Thank you so much for trying to help me. I'm not sure what the refresh rate is or how I would have changed it. 

Is there any way to know before installing the upgrades which one is causing the problem? There are a ton of them and re-installing the OS takes way to long to try them out one-by-one.

---

### Post by Rex Bouwense on 2012-04-24
I'm not sure that an update would cause the monitor screen to roll but since it happens only after you install the updates to a fresh install it seems to point in that direction.  There is no way to my limited knowledge to know which one(s) of the security updates (if any) is causing the problem.  Sorry.  At least you get a bump out of this.

---

### Post by amjjawad on 2012-04-24
Hello and welcome to Ubuntu Forum and thanks for choosing and using Lubuntu :)

Rex has done a great job to guide you through the steps that I would suggest or advise so he saved my time and did what I would do :)

Now, I assume you can login but it is hard to look at the screen, right?
If yes, please press: Alt+Ctrl+F1

You will see the CLI (Command Line Interface) instead of your GUI (Graphical User Interface) where you can use only your keyboard.

Type:
```
sudo lshw -C display
```

Copy and paste the output here please and make sure to wrap up the text with "CODE" tags or just highlight the text and press "#".

Also, run:
```
uname -r
```

Copy and paste the output here as well and please do as advised previously.

Usually, updates should help you and make your machine even better but sometimes, for some odd reason, that could break your system or cause problems.
Let's hope we will able to fix that :)

I would also recommend to go through Rex's suggestions. Checking MD5SUM is a MUST if you ask me. Also, it is much better to try Lubuntu from the LiveCD or LiveUSB before anything else ;)

I know some terms look hard but, I have managed to fix that for new comers by creating a thread with many useful links. Have a look at my signature and check Lubuntu One Stop Thread. Just have a look at the first post at the first page. Don't panic if you see many pages and posts ;)

---

### Post by Rex Bouwense on 2012-04-25
Thanks amjjawad.  I was getting frustrated.  I will monitor this thread to the conclusion as well.

---

### Post by amjjawad on 2012-04-25
> **Rex Bouwense said:**
> Thanks amjjawad.  I was getting frustrated.  I will monitor this thread to the conclusion as well.
I'm at your service as always, my friend and you know my motto, anything for Lubuntu and its users :D

---

