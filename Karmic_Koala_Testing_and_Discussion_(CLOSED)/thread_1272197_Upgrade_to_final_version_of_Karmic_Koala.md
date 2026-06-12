---
title: "Upgrade to final version of Karmic Koala"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by simpat1zq on 2009-09-21
Hi, I have an Asus netbook 1005HA, and it looks like the networking doesn't work out of the box for Jaunty. But, people are saying that it does for Karmic. 

So I was just wondering, if I install the Alpha of Karmic right now, will it be a fairly simple upgrade path to the final version when it is released in a few weeks?

---

### Post by stlsaint on 2009-09-21
if you install karmic right now you will have more issues than you bargained for. karmic alpha 6 is still unstable...i recommend you try to compile network driver yourself then install that way...updating to karmic now probably isnt the best solution. 
heres a link on [Compiling]("https://help.ubuntu.com/community/CompilingEasyHowTo").

you can also head over to the networking forum for more help as well!!

---

### Post by simpat1zq on 2009-09-21
I don't have any version of Ubuntu installed right now. And I will be dual booting, so Windows will still be my primary OS. I would rather deal with the quirks of an Alpha build than spending more time compiling drivers. 

I just want to make sure that I will be able to update to the final build. If updating won't be possible, I will just wait the few weeks until release.

---

### Post by QIII on 2009-09-22
Wait until the release.

Alphas are for testing.  Karmic is not even a Beta yet.

You will not be satisfied with Ubuntu if an Alpha is your first experience.

---

### Post by OrangeCrate on 2009-09-22
> **simpat1zq said:**
> I don't have any version of Ubuntu installed right now. And I will be dual booting, so Windows will still be my primary OS. I would rather deal with the quirks of an Alpha build than spending more time compiling drivers. 

**I just want to make sure that I will be able to update to the final build**. If updating won't be possible, I will just wait the few weeks until release.

Since no one else seems to want to answer your question, I will...

Assuming that you know the pitfalls of working with an Alpha release, if you choose to upgrade now, and you keep installing the updates, you'll end up with the final version on the release date.

---

### Post by simpat1zq on 2009-09-22
Thanks OrangeCrate. That is the answer I was looking for. 

I have no problem running an alpha build, and I have used Ubuntu many times before. I just didn't feel like spending a lot of time messing with drivers. 

Thanks everyone.

---

### Post by QIII on 2009-09-22
Just a bit of warning...

The Alpha 6 iso from Sept 17 will likely result in a borked system.

If you install Alpha 5 and upgrade, you *may *get a relatively clean upgrade.  But when I tried to upgrade from 5 to 6, I ended up with the same problems as attempting a fresh install of Alpha 6.  I had to do a dist-upgrade to 6.

I would recommend a fresh install of Alpha 5, then a dist-upgrade from Alpha 5 to Alpha 6 and updates from there.

Just a word of warning from someone who has actually been down that road.

---

### Post by kasl33 on 2009-09-22
> **simpat1zq said:**
> Thanks OrangeCrate. That is the answer I was looking for. 

I have no problem running an alpha build, and I have used Ubuntu many times before. I just didn't feel like spending a lot of time messing with drivers. 

Thanks everyone.

One word of advice though, if you manage to install Karmic and everything works, you may just leave it that way and not do any upgrades until the final is out. I am telling you this from experience. I installed Karmic and then saw all kinds of updates, so I ran them and them my system was borked. If I'd have left it alone, I wouldn't have had to reinstall it.

---

### Post by simpat1zq on 2009-09-22
Just installed it. The only problem I got is that it didn't pick up the XP installation I had in grub. But I'll be able to take care of that. 

Sound and wireless works great. Haven't had a chance to test wired, but I would imaging it will work. I'm thinking that most problems with it will be hardware specific. 

And anyways I'm just using this install as a means to have linux around when I need it. So I can wipe it clean and start over at any time.

---

### Post by QIII on 2009-09-22
Karmic doesn't use the old GRUB, but GRUB2, so you won't be able to use menu.lst to edit your OS selections.

```
sudo apt-get install os-prober
```

(Depending on which Alpha you got installed, you may already have the latest.)

```
sudo os-prober
```

```
sudo update-grub2
```

---

### Post by simpat1zq on 2009-09-22
Wow. I didn't know that. That you for that. I would have spent an hour trying to figure that out.

Where do I go to configure stuff like which OS to boot as the primary, and the timeout and stuff. 

I see that update-grub2 generated a grub.cfg. But I can't seem to find the location of it.

---

### Post by simpat1zq on 2009-09-23
It looks like I spoke too soon. There was one small glitch. After I ran the updategrub, it found the Windows OS, and I was able to boot to it from grub.

But Windows wouldn't boot. The boot screen would come up and just get stuck there. Going to safe mode, I saw that it got stuck at Mup.sys. Google search indicated that was normally a hardware problem, but could be caused by a long list of things. So I decided to just reinstall Windows. 

After reinstalling Windows, the boot loader on the new installation picked up the old installation. So I decided to try booting from it, and it worked just fine.

I'm guessing it has to do with the way grub was passing control to Windows, but That's just a guess. Any ideas?

I can't get to the Ubuntu installation right now, so I can't check the grub config at the moment.

---

