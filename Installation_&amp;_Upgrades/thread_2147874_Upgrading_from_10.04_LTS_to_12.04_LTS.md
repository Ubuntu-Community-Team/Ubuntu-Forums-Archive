---
title: "Upgrading from 10.04 LTS to 12.04 LTS"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by Seinfeld on 2013-05-23
Hi ..

Now, I want to upgrade to 12.04 from 10.04. Any one could tell me please, how can I keep my gnome desktop settings such as, panels, icons, wallpaper, gconf settings etc.. ??
I did upgrade 12.04 on another machine and after installing gnome-shell and gnome-session-fallback, it took me several hours to arrange my desktop the same it was from scratch.
Also, I would like to use my 10.04 gdm screen too if possible. Is there a folder(s) that stores my old desktop settings so I can back it up and overwrite the new 12.04 one with it ??

Thanks so much

---

### Post by Bucky Ball on 2013-05-23
***Thread moved to Installation & Upgrades***

I have moved your thread to its own thread as your question has nothing to do with the thread title of the thread you posted on. This will improve your chances of getting help for your issue specifically. 

Note to all: Please refrain from hijacking other threads; it is unfair to the OP, confusing, and dilutes community's ability to assist. Post a new thread for your problem with a descriptive tile and as much info as you can muster about your issue. If you have two problems (disrelated) post them in separate new threads. Thanks. 

Good luck.

---

### Post by fantab on 2013-05-23
> **Seinfeld said:**
> Now, I want to upgrade to 12.04 from 10.04. Any one could tell me please, how can I keep my gnome desktop settings such as, panels, icons, wallpaper, gconf settings etc.. ??
I did upgrade 12.04 on another machine and after installing gnome-shell and gnome-session-fallback, it took me several hours to arrange my desktop the same it was from scratch.
Also, I would like to use my 10.04 gdm screen too if possible. Is there a folder(s) that stores my old desktop settings so I can back it up and overwrite the new 12.04 one with it ??

Ubuntu and Gnome have undergone massive changes from 10.04 to 12.04. Gnome-shell and gnome-session-fallback are not exactly gnome2 with panels, underneath you have gnome3. It will be better if you will do a clean install of 12.04 and customize accordingly.

Having said that, your preferences and settings will be stored in dotfolders in Home, they are hidden with dot, you have to Ctrl+H to reveal them. You can save these .folders and try to reuse them. However I don't recommend it and do it on your own risk.

Good Luck...

---

### Post by ibjsb4 on 2013-05-23
What "fantab" said, plus you can have the old 10o4 desktop in the new 12o4 install by installing the Gnome-Classic desktop.  Trying to save your gnome2 settings to gnome3 is hit and miss, but you can try it with a version upgrade.  It can be successful or it can be a can of worms.

Gnome classic desktop

```
sudo apt-get install gnome-session-fallback
```

---

### Post by grahammechanical on 2013-05-23
Also many themes that worked on 10.04 do not work on 12.04 because they were built using a different tool kit. You will need to install new themes.

---

### Post by Seinfeld on 2013-05-23
Dear Bucky Ball.

I apologize for posting my question in a thread that might not be discussing the very same problem. I tried hard to search for a similar issue but wasn't lucky enough. I did not by all means mean to hijack, violate or breach any forum regulations. 

Thank you!

---

### Post by Seinfeld on 2013-05-23
Thanks all for the replies.

Yes, I agreee, a clean install is the best way to go. But, 12.04 deosn't recognize my ATI video card driver. It worked fine with 10.04 and it continued to work fine only with upgrading :( 
Now, I have another machine with 12.04 that has my customized gnome3 with session-fallback and -shell, do you mean that I can just copy the .folders/files from there and overwrite the new ones on the new machine ?
I always do that with .mozilla and .thuinderbird and it works. I will give it a try.
Thanks !!

---

### Post by Bucky Ball on 2013-05-23
Doesn't pick up ATI? Do an update, check 'Additional Drivers'.

You can also try installing 'fglrx' and 'fglrx-amdcccle', reboot then check 'Additional Drivers'.

---

### Post by Seinfeld on 2013-05-23
Thanks for the reply Bucky Ball

I tried really hard. It is actually my new laptop Thinkpad with an ATI FireGL 570V. 
I started with a clean install as recommended and spent several hours trying hard to get the driver working. I installed every package that has an ATI/AMD driver related while from the software center at 12.04. I even tried to insatll it from the AMD website, so frustrating. The Settings->Addtional Drivers icon on Unity does not show any driver installed. I had to go down again to 10.04 which when I do, the Proprietary Driver notfication pops up on Gnome desktop and -> click, reboot boom..I am done.
I then had not choice, I had to go down to 10.04 (even 9.10 recognized) and then upgrade to 12.04.. I wish, wish I had a clean insatall but it is a nightmare to let the ATI FireGL 570V. working.. Any help ?? 
Thanks again..

---

