---
title: "ubuntu broken"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by mikishua on 2008-11-02
I recently switched from windows to ubuntu with a 7.10 boot CD and used this for a few weeks and then i tried to upgrade from 7.10 to 8.04 using the update manager and i set it going and then left my laptop running and went out for the evening. When i came back later my laptop was switched off and when i tried to boot i get to the login screen put my username and password in as normal but then i just get a blank screen with nothing happening. At the moment i am using the 7.10 install CD to run ubuntu and i can still get to all my files but i cant download anything to that directory as i dont have permission and i dont have enough space on this temporary directory to download a new CD image so that i can upgrade using the CD and hopefully fix it that way. So my question is, is there way to fix this problem so i dont have to boot from my CD or how do i wipe my hard disk so i can just start again. I dont really have much data on my HD at the moment and nothing that i cant get again easily so if wiping the disk is the easier option i dont mind doing this at all but i dont know how.

---

### Post by taurus on 2008-11-02
If you want to reinstall Ubuntu on the same partitions, just do so from the LiveCD.  When you get to the partition screen, pick whichever partition to mount it as / and format it so the partition would be clean.

Or you can boot into recovery mode from GRUB menu and reconfigure your X server again to see if that fixes the problem.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Neobuntu on 2008-11-02
Please do not use an older CD with plans to "simply" upgrade to the newest version. Much work has been done. While it can work, my experience is it is not faster or less trouble. YMMV. It is also less of a known foundation.

Please remember, "clean" installing Kubuntu is no where near as time consuming as installing Windows.

I recommend getting a newer CD via download or order or friend. You may even be able to download faster at some libraries that are set up with faster broadband. 

The question is, which release? Here's where things differ from the closed software world. Right now, the brand new (K)ubuntu is out and with Kubuntu, a new and experimental KDE4. While this is officially "released", it is a experimental release "Intrepid", where new users might better enjoy the stability of the "Hardy", 8.04 (04=April) version. After all, Hardy is a Long Term Support (LTS) release and thus still very, very, supported for now and for some time.

Generally, and for a predicted Three more months (at least), please stay with Hardy. I prefer Kubuntu to keep it simple (Windows refugees). This assumes you have at least 384MB RAM for the live "Desktop" CD. 192MB to 384MB, get the "Alternate" CD(or better, more RAM). Please note, one does **NOT** have to delete Windows, to try it. Usually, new users bounce back and forth for about Six months of real use, before they realize (K)ubuntu is better for them. It's an easy "dual boot" and on your same hardware set. Please use your newest computer and fastest hard drive. 

Remember, **every OS system** can get out of whack (problems). Kubuntu is the lesser of "evils", by far.

---

