---
title: "I am still on 11.04, what are the implications?"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by vincegata on 2012-10-22
Hi,

As the title says, I am still running 11.04 because I like it, what are the implications when support expires on Oct 28?

There won't be any Ubuntu updates? There won't be any application updates? What else?

Thanks.

---

### Post by cortman on 2012-10-22
You won't receive updates, both normal and security. I would suggest you upgrade to 12.04 (which will be supported for five years).

---

### Post by BlinkinCat on 2012-10-22
> **cortman said:**
> You won't receive updates, both normal and security. I would suggest you upgrade to 12.04 (which will be supported for five years).

And if you don't like Unity, there are numerous alternatives -

Cheers - :P

---

### Post by vincegata on 2012-10-22
My multifunction Canon MF-4150 does not work on 12.04, and for a couple of other reasons I do not want to upgrade. 

Thx for posting.

---

### Post by vincegata on 2012-10-22
> **BlinkinCat said:**
> And if you don't like Unity, there are numerous alternatives -

Cheers - :P

:) yes, and because I do not like Unity I do not want to move to 12.04.

---

### Post by irv on 2012-10-22
Are you running the Unity Desktop? The reason I ask is because 12.X really made so nice improvements in 12.04 which has 5 years support. I keep hearing about 12.10 and the improvement they made with this release so this morning I install it and I am really liking it.
To be honest with you I find backing up my personal files and installing a fresh copy of Ubuntu and restoring my files and reloading my apps to be a very fast and easy process.
For some reason I like using the latest releases of any distro. By the way, I was one who liked 11.04 when it came out, but 12.10 has so many nice things. Do a search on the Internet to check out all the new things they added.
[ATTACH]225933[/ATTACH]

---

### Post by jerome1232 on 2012-10-22
> **vincegata said:**
> :) yes, and because I do not like Unity I do not want to move to 12.04.

Change is good, try a new desktop environment or use gnome-classic, I'd move to 12.04 lts and sit on it for awhile imo.

Don't be the guy that is still using Windows XP  in 2020 because he refuses to accept change.

---

### Post by irv on 2012-10-22
> **vincegata said:**
> My multifunction Canon MF-4150 does not work on 12.04, and for a couple of other reasons I do not want to upgrade. 

Thx for posting.

I posted my other post before I saw you didn't like Unity. What desktop are you using?
A good way to check out your hardware is to boot into a live OS from a DVD or USB and test your hardware. One thing about using Linux we have so many nice distros to chose from. I have tried many different ones and always come back to Ubuntu. And using Ubuntu you have so many nice Desktop to chose from also.

---

### Post by vincegata on 2012-10-22
> **irv said:**
> I posted my other post before I saw you didn't like Unity. What desktop are you using?
A good way to check out your hardware is to boot into a live OS from a DVD or USB and test your hardware. One thing about using Linux we have so many nice distros to chose from. I have tried many different ones and always come back to Ubuntu. And using Ubuntu you have so many nice Desktop to chose from also.

I am using Classic desktop on 11.04. I have a double boot with CentOS 6.3 & Gnome2 but it is really a server OS as it does not have few applications that I am using on Ubuntu (for photography), and I do not want to compile them.

I am thinking what to do... :) I could live without regular updates for sometime until find a solution but missing security updates is sort of dangerous.

---

### Post by jerome1232 on 2012-10-23
I still don't understand why you wouldn't want to use gnome-classic on 12.04, it looks a lot like gnome2

---

### Post by irv on 2012-10-23
> **vincegata said:**
> I am using Classic desktop on 11.04. I have a double boot with CentOS 6.3 & Gnome2 but it is really a server OS as it does not have few applications that I am using on Ubuntu (for photography), and I do not want to compile them.

I am thinking what to do... :) I could live without regular updates for sometime until find a solution but missing security updates is sort of dangerous.
When you said "it is really a server OS", did you mean you are using it as a sever? If it is a Internet server you might want to have security updates.
I have a private Internet server that I keep audio files on, and I am running an old release of Ubuntu with no security update, but I don't care if someone hacks into it because I don't have anything worth stealing. I keep all my files backed up, and it only take me a few hours to get everything running again if someone were to wipe it out.
By the way this has never happened and I have never gotten a virus on it, and it has been running for many years now. (I am running 10.04 on it).

---

### Post by vincegata on 2012-10-23
> **jerome1232 said:**
> I still don't understand why you wouldn't want to use gnome-classic on 12.04, it looks a lot like gnome2

1. My multifunction Canon MF-4150 does not work on 12.04.
2. I need to have System Monitor running as indicator in panel so I can see when MATLAB (math application) is done calculations instead of me switching back and force to see if it's done. It's absent in 12.04 GNOME Fallback (that's what GNOME Classic called in 12.04).
3. GNOME Fallback does not work properly on 12.04 - color is off out of the box (fixable), the order of applets on the panel gets messed up.

It looks like they did not put much effort into Fallback. 

I did install 12.04 with GNOME Fallback, I used it for about three hours and had enough.

---

### Post by jerome1232 on 2012-10-23
> **vincegata said:**
> 1. My multifunction Canon MF-4150 does not work on 12.04.

I can't address this specifically, although you didn't detail any attempts at trouble shooting. A quick google search on my part I noticed something about the package gs-esp being gone and there are workarounds to get it to work. I don't know if that's your specific issue or not. This is what my quick google search yielded [http://www.howtoforge.com/forums/showthread.php?t=53681&page=2](http://www.howtoforge.com/forums/showthread.php?t=53681&page=2)

> **vincegata said:**
> 2. I need to have System Monitor running as indicator in panel so I can see when MATLAB (math application) is done calculations instead of me switching back and force to see if it's done. It's absent in 12.04 GNOME Fallback (that's what GNOME Classic called in 12.04).

Install indicator-multiload, it puts an indicator on the panel that looks just like the old system monitor one for gnome2.

> **vincegata said:**
> 3. GNOME Fallback does not work properly on 12.04 - color is off out of the box (fixable), the order of applets on the panel gets messed up.

Sounds more like a graphics driver issue to me? What video card are you using, what driver?

---

### Post by vincegata on 2012-10-23
> **jerome1232 said:**
> I can't address this specifically, although you didn't detail any attempts at trouble shooting. A quick google search on my part I noticed something about the package gs-esp being gone and there are workarounds to get it to work. I don't know if that's your specific issue or not. This is what my quick google search yielded [http://www.howtoforge.com/forums/showthread.php?t=53681&page=2](http://www.howtoforge.com/forums/showthread.php?t=53681&page=2)



Install indicator-multiload, it puts an indicator on the panel that looks just like the old system monitor one for gnome2.



Sounds more like a graphics driver issue to me? What video card are you using, what driver?

1. Concerning Canon multifunction there is a thread:
[http://ubuntuforums.org/showthread.php?t=1723101](http://ubuntuforums.org/showthread.php?t=1723101)

It's integrated gfx on Intel Arrandale, HD3000 I think what it's called, on Dell Latitude 6510.

2. I tried indicator-multiload but it disappeared after reboot.

3. Buggy color on Fallback panel is fixed:
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289)

Looks like they've done some fixes on gnome-fallback. I've just made some space for playground on my HDD and I will try 12.04 again over the weekend. If not I'll try XUbuntu 12.04. We'll see... I am certainly having a dilemma here.

THX for your input.

---

### Post by jerome1232 on 2012-10-23
[INDENT][INDENT]you have to add indicator-multiload to your list of startup apps. I'll check out your printer thread later.

xubuntu is very nice these days, a good alternative to gnome2.
[/INDENT][/INDENT]

---

