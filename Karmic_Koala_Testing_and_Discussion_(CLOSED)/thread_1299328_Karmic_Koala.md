---
title: "Karmic Koala"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hosmion on 2009-10-23
If someone could please find a tutorial on how to install the Karmic Koala Beta Test that would be awesome.

---

### Post by Hosmion on 2009-10-23
Bump

---

### Post by Matt__ on 2009-10-23
alt+f2

```
update-manager -d
```then follow prompts

---

### Post by mikewhatever on 2009-10-23
Do you want to dual boot with Windows or single boot Karmic only? The installer hasn't changed since a few releases back, so that a tutorial for Jaunty should do well.
Here is one ->[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

---

### Post by Hosmion on 2009-10-24
I want to be able to dual boot.

---

### Post by Hosmion on 2009-10-24
> **Matt__ said:**
> alt+f2

```
update-manager -d
```then follow prompts


Can someone verify that this is not a malicious command please?  I opened the regular update manager and it didn't ask me to upgrade..

Sorry.

---

### Post by hugmenot on 2009-10-24
```
$ update-manager --help
Usage: update-manager [options]

Options:
  -h, --help            show this help message and exit
  -V, --version         Show version and exit
  --data-dir=DATA_DIR   Directory that contains the data files
  -c, --check-dist-upgrades
                        Check if a new Ubuntu release is available
[B]  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible[/B]
  -p, --proposed        Upgrade using the latest proposed version of the
                        release upgrader
  --no-focus-on-map     Do not focus on map when starting
  --dist-upgrade        Try to run a dist-upgrade
  -s, --sandbox         Test upgrade with a sandbox aufs overlay
```

---

### Post by Hosmion on 2009-10-24
Ok, thanks :D

---

### Post by Hosmion on 2009-10-24
Does the upgrade-manager -d allow me to dual boot?

---

### Post by slakkie on 2009-10-24
Don't upgrade, wait for the stable release. Please, for your sake and ours.

---

### Post by Hosmion on 2009-10-24
I will, but why?

---

### Post by slakkie on 2009-10-24
Because of the type of questions you ask. If one would run a development release they would know how to setup a multi-boot system. They would know what a safe command is, or they would know how to check if a command was safe to run.

Since you have the attitude of, I have this problem, you fix it, I don't think it is wise for you to run a development release. You would need to invest your time to fix issues if they arise.

---

### Post by Hosmion on 2009-10-24
Oh, I'm sorry, I'm not trying to have an attitude about it..  I am not very experienced in UBuntU and all of its qualities and conditions, so I don't know barely anything about it..  I will try and fix that problem.  Sorry again if I sounded like that.

---

### Post by Menthu_Rae on 2009-10-24
> **Hosmion said:**
> Oh, I'm sorry, I'm not trying to have an attitude about it..  I am not very experienced in UBuntU and all of its qualities and conditions, so I don't know barely anything about it..  I will try and fix that problem.  Sorry again if I sounded like that.

Nobody was trying to say anything bad mate - just sit back and enjoy your 9.04 release for the moment.

When 9.10 is ready (only a week to go!) you can upgrade away as usual without the need to dual-boot. :)

So yeah, chill and let the bugs get ironed out before you jump in head first :guitar:

---

### Post by slakkie on 2009-10-24
> **Hosmion said:**
> Oh, I'm sorry, I'm not trying to have an attitude about it..  I am not very experienced in UBuntU and all of its qualities and conditions, so I don't know barely anything about it..  I will try and fix that problem.  Sorry again if I sounded like that.

:) No problem, the question about: could someone check if x is a malicious command triggered me to say something about the attitude you had. 

Just play it safe for now, once you become accustomed to Ubuntu and how to maintain the system (not just use it), then you could jump on the band wagon and help test it. 

And if you don't know please ask, but also try to look up answers yourself. Best of luck in finding your way in Ubuntu!

---

### Post by philinux on 2009-10-24
> **Hosmion said:**
> Oh, I'm sorry, I'm not trying to have an attitude about it..  I am not very experienced in UBuntU and all of its qualities and conditions, so I don't know barely anything about it..  I will try and fix that problem.  Sorry again if I sounded like that.

I think what slakkie was trying to say is this. If someone needs to ask those sorts of questions then they are better of staying put on the stable release until the time comes when **it** tells you it's time to update. Even then you have a choice.

---

### Post by Hosmion on 2009-10-24
Ok, I'll try my hardest to figure this stuff out for myself :D

---

### Post by philinux on 2009-10-24
> **Hosmion said:**
> Ok, I'll try my hardest to figure this stuff out for myself :D

Asking questions is the right way. Probably saved yourself some grief by asking here. So dont stop.

Good place to start are the stickies on this forum. It's a steep learning curve but worth the effort.

---

### Post by m4tic on 2009-10-24
4 days to go mate don't worry about the Karmic beta, look for the final version coming up. 
What the previous guy was saying is, any version named "BETA" means it's not stable as the final will be. Rather play it safe

---

### Post by kansasnoob on 2009-10-24
I must say I always clench my teeth a bit when people ask questions that can be answered just by reading the release notes, which if one goes to the Ubuntu home page:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

and click on the huge "9.10 coming soon" is just where you land:

[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

> Upgrading from Ubuntu 9.04

To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions.   

Even once a new release becomes available there are always inevitably some "issues" that require a bit of reading.

---

### Post by Hosmion on 2009-10-24
I had been there before..  But it doesn't matter :D..  I'm just going to wait for the stable release..  When I download the new one though in 5 days, will it upgrade my Ubuntu and not delete my Windows?  I have a lot of stuff that I bought for real money on my Windows so I can't lose it..

---

### Post by philinux on 2009-10-24
> **Hosmion said:**
> I had been there before..  But it doesn't matter :D..  I'm just going to wait for the stable release..  When I download the new one though in 5 days, will it upgrade my Ubuntu and not delete my Windows?  I have a lot of stuff that I bought for real money on my Windows so I can't lose it..

you dont need to download it if you just want to upgrade.

I assume you got Jaunty on there now dual booting, is that correct?

---

### Post by Hosmion on 2009-10-24
> **philinux said:**
> Have you run ubuntu before? 

Have you got ubuntu on this machine now?

Yes I have ubuntu on my machine right now.

---

### Post by philinux on 2009-10-24
> **Hosmion said:**
> Yes I have ubuntu on my machine right now.

I reread you posts and sorry I edited my post please see above.

---

### Post by Hosmion on 2009-10-24
Yes I am dual booting right now.

---

### Post by slakkie on 2009-10-24
Then you should have a dual boot system after the upgrade.

---

### Post by philinux on 2009-10-24
> **Hosmion said:**
> Yes I am dual booting right now.

Ok so after next Thursday when the system checks for updates it will tell you that there is a new release and ask if you want to upgrade. No need to download the new iso unless you intend to do a clean install.

---

### Post by Hosmion on 2009-10-24
Ok, thanks :D

---

### Post by andrewabc on 2009-10-24
> **philinux said:**
> Ok so after next Thursday when the system checks for updates it will tell you that there is a new release and ask if you want to upgrade. No need to download the new iso unless you intend to do a clean install.

It would be a very good idea to download/burn the iso and test it to make sure everything works (video/internet/drivers). If everything works on the livecd, then you could do your upgrade. And if something horrible breaks during upgrade and you are forced to format/fresh install, you will have the CD ready.

---

### Post by VMC on 2009-10-24
> **Hosmion said:**
> I had been there before..  But it doesn't matter :D..  I'm just going to wait for the stable release..  When I download the new one though in 5 days, will it upgrade my Ubuntu and **not delete my Windows**?  I have a lot of stuff that I bought for real money on my Windows so I can't lose it..

That's what backups are for.

 If you upgrade, its not going to touch any Windows partition.

 If, on the other hand, you do a fresh installation you need to know how ubuntu's ubiquity works. I have seen many people wipe out their entire hard drives by just not following the instructions.

---

### Post by mikewhatever on 2009-10-24
> **Hosmion said:**
> I had been there before..  But it doesn't matter :D..  I'm just going to wait for the stable release..  When I download the new one though in 5 days, will it upgrade my Ubuntu and not delete my Windows?  I have a lot of stuff that I bought for real money on my Windows so I can't lose it..

The only way to keep your files safe is have a backup. An upgrade should not delete Windows, but playing safe is your best bet. By the way, you should have mentioned the dual boot setup in post #1.

---

