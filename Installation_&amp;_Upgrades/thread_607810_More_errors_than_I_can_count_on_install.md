---
title: "More errors than I can count on install"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by impudence on 2007-11-09
This is my first attempt at ubuntu. In my attempt to get a dual boot going I've gotten up to the point where I stick the 7.10 cd in and boot from it. The menu screen comes up but when I tell it to install it loads up the kernal, then shows a splash screen with a bar at the bottom. From there I waited a while and eventually it went into initfs: or something and I restarted. I looked on the internet for help and didn't google anything helpful. I did learn that alt- f1 shows text of what's happening. Then I restarted and tried again with alt f1 during the splash screen. To make a long story shorter I've done this 3-4 times now with each time doing different errors. I've googled every error I've gotten so far but I always end up where I Started with no gained knowledge since I'm completely clueless to how linux works.

The first error is always;

Buffer I/O Error on device sr0, logical block ########

Then it's typically:
Squashfs error: Unable to read cache block and directory block.
and something about squashbread

I always get those 2 about a billion times. One time it started doing what looked like productive things:

*setting preliminary keymap...     [ok]

More errors

*setting clock...

Errors


Anyway, this has been my morning and I've gotten nowhere. Each time it stops I just restart and try again.

The cd drive has been the bane of my exsistance for a long time. It requires some persuasion to read a cd in the first place but it's been booting from the cd without any problem. Could that be the root of my problems? I did the CD check on the menu and it all checked out.

I rambled, I'm sorry.

---

### Post by creeco on 2007-11-09
Im pretty sure this is cause because your cd is flawed. Try burning a new one at the slowest speed avaiable, it really helps (around x2 x4)...

---

### Post by Pumalite on 2007-11-09
Start from basics:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x, burn as 'image' not as 'data'
To boot a Live CD you need 512 MB RAM. If ATI video, better install with Alternate CD.

---

### Post by impudence on 2007-11-09
ok I've checked the md5sum, it matches. I'm reburning it in poweriso again (I did it at 4x the first time aswell tho) I have 512 ram.

---

### Post by Pumalite on 2007-11-09
Don't unpack the iso and burn the files. You have to burn the iso as 'Image'
Use the burner that shows up in the link I gave you or download ImgBurn, install, go to MODE>ISO>Burn

---

### Post by impudence on 2007-11-09
Yea, I've got a grasp on iso. So far this is just repeating what I did originally. I can only hope that my comp did a bad job burning it the first time.

---

### Post by Pumalite on 2007-11-09
If it doesn't work; clean the lens in your burner, try the CD's in a different computer or change your burner if necessary.

---

### Post by impudence on 2007-11-09
I'm getting the same errors as last time.

I tried the first cd in this laptop and it loaded up fine with no errors at all. It's obvious now the desktop is to blame. I'm going to see if I can clean the lens on it in the hopes that that helps.

---

### Post by impudence on 2007-11-09
Woo! I oiled the rails and cleaned off the lens and it's working beautifully. It's always the simplest things. Thank you so much

---

### Post by et_tu_brute on 2007-11-18
> **impudence said:**
> This is my first attempt at ubuntu. In my attempt to get a dual boot going I've gotten up to the point where I stick the 7.10 cd in and boot from it. The menu screen comes up but when I tell it to install it loads up the kernal, then shows a splash screen with a bar at the bottom. From there I waited a while and eventually it went into initfs: or something and I restarted. I looked on the internet for help and didn't google anything helpful. I did learn that alt- f1 shows text of what's happening. Then I restarted and tried again with alt f1 during the splash screen. To make a long story shorter I've done this 3-4 times now with each time doing different errors. I've googled every error I've gotten so far but I always end up where I Started with no gained knowledge since I'm completely clueless to how linux works.

The first error is always;

Buffer I/O Error on device sr0, logical block ########

Then it's typically:
Squashfs error: Unable to read cache block and directory block.
and something about squashbread

I always get those 2 about a billion times. One time it started doing what looked like productive things:

*setting preliminary keymap...     [ok]

More errors

*setting clock...

Errors


Anyway, this has been my morning and I've gotten nowhere. Each time it stops I just restart and try again.

The cd drive has been the bane of my exsistance for a long time. It requires some persuasion to read a cd in the first place but it's been booting from the cd without any problem. Could that be the root of my problems? I did the CD check on the menu and it all checked out.

I rambled, I'm sorry.
I have had EXACTLY the same problem with the same disk errors. I received from Canonical last Friday 4 disks, Ubuntu 7.10 32 bit & 64 bit verions and Kubuntu 32 & 64 bit versions. All except Ubuntu 7.10 32 bit versions installed without any problems. However my Ubuntu 7.10 32 bit version had the exact same install errors. Any suggestions regarding checksum failure, bad ISO burns etc. are not relevent here as I am usung ORIGINAL media, not d/loaded ISOs. The CD will not operate on 2 pcs I have nor will it install via VirtualBox.
Have been looking for others with same problem and a fix before I go back to Canonical for a replacement disc.
Cheers

---

### Post by Pumalite on 2007-11-19
If I were you I would download my own iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
And follow the steps described abave.

---

