---
title: "upgrading to 10.04 stuck on 22 min left &quot;preparing memtest86+&quot; for 3 hours"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by dsamaha131 on 2010-04-29
so im installing 10.04 right now  and in terminal it keeps loading the same script- "found linux image:  /boot/vmlinuz-2.6.32-21-generic 
its been here for about 3 hours. is that normal? or how do i get out of it?
heres a screen shot

thanks

---

### Post by P4man on 2010-04-29
nope, that cant be right. Is this a 10.04 RC -> LTS upgrade, or from 9.10 ?

---

### Post by andey on 2010-04-29
suksss

---

### Post by dsamaha131 on 2010-04-29
im an idiot.
i upDATED 9.40 last night. but i guess i should have up dated 9.40 this morning too?
so i guess im gonna have to start all over. 
could i abort terminal and start over without having to download the 10.04 upgrade again?
and any suggestions?
do i need to reinstall 9.40?
thanks
sorry my friend is teaching me about linux and ubuntu so im trying to get better and understanding how it works and what i can do with it.

---

### Post by dsamaha131 on 2010-04-29
its LTS

---

### Post by P4man on 2010-04-29
There is no 9.40. There is a 9.04, and you cant upgrade that to 10.04 directly (nor should update manager suggest it or allow it). You can upgrade 9.04 to 9.10 and 9.10 to 10.04. What exactly did you try? Or did you run an upgrade without rebooting and then upgrade again?

Regardless, update manager should not allow you to make mistakes, so Im curious what you did exactly.

> could i abort terminal and start over without having to download the 10.04 upgrade again?

Packages are cached, so I guess yes, but the question is if you can update at all. Also, depending what you did, its entirely possible your machine will not boot. If you have anything to back up, do it NOW (you should have before upgrading, but consider this your last warning :) )

---

### Post by catxk on 2010-04-29
I got the exact same problem. Upgrading from 9.10 to 10.04, with a Wubi install upon Windows 7.

Any solution or course of action would be appreciated. Feels a bit risky to simply abort the upgrade half-way through. Thanks!

---

### Post by P4man on 2010-04-29
Thats not good.. at all. Some googling suggests this bug has been around since beta:
[http://swiss.ubuntuforums.org/showthread.php?p=9044763](http://swiss.ubuntuforums.org/showthread.php?p=9044763)

That user could not reboot, he got a kernel panic.

So, back up what you need first.

Then, you will have no choice but to abort the upgrade. Kinda pointless to leave it like that for a few days. Dont reboot though.

Instead, open a terminal and type:

```
sudo dpkg --configure -a
```

Try starting the upgrade again after that.

Honestly though, Im not too hopeful. I can only recommend to prepare for a reinstall and I would strongly suggest no to do a wubi install this time.

---

### Post by catxk on 2010-04-29
Thanks for your reply. I will give it a try and report back how it goes.

---

### Post by P4man on 2010-04-29
Also, may I suggest you copy the contents of 

/var/log/installer/

to a stick or somewhere safe? If could be extremely useful for in a bug report. It wont solve your issue here and now, but at least lets make sure it does get fixed for others.

---

### Post by gluxon on 2010-04-29
I just had the same exact problem.

Press Ctrl + C and abort the current operation. The installer then skips this step. I can't guarantee something bad won't happen for you though. :(

---

### Post by dsamaha131 on 2010-04-29
sorry, i was doing my math hw and i had numbers all jumbled in my head.
i updated the 9.10 files and i installed 10.04.
sorry

---

### Post by cuberts on 2010-04-29
> **dsamaha131 said:**
> so im installing 10.04 right now  and in terminal it keeps loading the same script- "found linux image:  /boot/vmlinuz-2.6.32-21-generic 
its been here for about 3 hours. is that normal? or how do i get out of it?
heres a screen shot

thankswell try to wait a little longer and if it is still stuck then I think that you might as well cancel it and try it again :(

---

### Post by Rawrmage on 2010-04-29
I don't know what to do but I wouldn't cancel it...
I cancelled it and now my machine won't boot.
I have the same type of set-up, a Wubi install from Vista.
If I manage to fix my machine I will post here how. Thanks.

---

### Post by dsamaha131 on 2010-04-29
did you cancel or abort?

---

### Post by dsamaha131 on 2010-04-29
ya yurr its working :D
:guitar:

---

### Post by jblaine271 on 2010-04-30
I'm having a similar problem... so what'd you do to get it working?

---

### Post by ebola1717 on 2010-04-30
I cancelled too (though unintentionally - i wanted to see if i could and meant to hit no).  It's currently continuing the installation.  I'm keeping my fingers crossed.  Luckily I don't have any super critical files on it right now.

EDIT:
I just finished installing and rebooted.  It seems to be working fine.

---

### Post by catxk on 2010-04-30
Good for you! My installation got fried, so I'm starting over. It's fine though, as I only had the Wubi installation to familiarize myself with Ubuntu.

Let me just say this: I aborted the installation (killed the upgrade) and Ubuntu would not boot afterwards. Windows 7 obviously booted fine.

---

### Post by MarvinK on 2010-04-30
Same problem here.
I'm running Wubi 9.10, installed in XP.
I couldn't boot that kernel properly either (see [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/387326](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/387326)).
Installation got stuck and I skipped the step with ctrl+c.
Installation went on and asked me to reboot.
I clicked ok and got a whole lot of blinking colorful pixels.
I shut my laptop down by holding the power button.
I turned my laptop on again and grub went to rescue mode upon starting.
I used the win XP CD to recover the MBR.
Rebooted
XP and Ubuntu were on the list but Ubuntu wouldn't start anymore (don't know the error anymore).
Removed Ubuntu in XP and now I'm downloading 10.04

---

### Post by dashingdon on 2010-05-01
same issue ... stuck at "preparing memtest86+". 

XP with wubi install of 9.10 gnome desktop. trying my luck by aborting the upgrade. 

Will update the progress.

Update : 
--> used CTRL +C to skip the step
--> Wizard continued with remaining steps
--> when asked for reboot , select reboot later
--> Open terminal and run "sudo dpkg --configure -a" Note : No output was generated
--> Reboot

:) .. I am on working 10:04 . However all windows are top aligned.. something for another thread. 

Hope this helps

---

### Post by scvblwxq on 2010-05-03
My wubi upgrade also hung. I selected the window, pressed ctrl+c and nothing happened. I kept trying to cancel it then placed the cursor in the black pane of the window where the messages are and hit ctrl+c and it unfroze and is continuing the upgrade.  Now "Debconf on ubuntu" is asking where to install GRUB and giving me 3 choices. What to do? I guess I'll look through the posts and see if anyone has an answer. Took Help's advice and installed GRUB to all 3 locations and the upgrade is running again with 1 hour to go. Finished in 20 minutes and restarted OK. Whew!

---

### Post by magicker on 2010-05-03
looks like the whole wubi thing has not been tested.. same probs here on both wubi and xp and wubi and windows 7...

the windows 7 install is dead cos i bottled it.
xp gets to live another day as i did the ctrl c thing and it went on... so far so good.. fingers crossed fro the reboot

---

### Post by liutszho on 2010-05-05
Has this been solved?

I'm on a 9.10 wubi ubuntu and want to upgrade to 10.4.

I don't want to lose all my installed software/preferences by doing a clean install.

---

### Post by magicker on 2010-05-05
i have failed to upgrade on 2 machines now :(

had to remove and reinstall... pita

---

### Post by catzlai on 2010-05-05
Same problem. It cannot stop looking for linux image. It seems to be a problem with wubi only? I don't have this problem on my other desktop. :mad:

---

### Post by catzlai on 2010-05-05
Oh dear. I pressed crtl+C and clicked yes. The installation continued and I installed GRUB on all the partitions. I thought it went ok so I didn't do sudo dpkg --configure -a.

Now when I can't reboot it and the GRUB rescue pops up. What can I do?

---

### Post by jarrarist on 2010-05-07
I had 9.10 installed inside XP, it got broken after an upgrade few weeks ago, I got hopeless eventually and turned back to windows XP... now I uninstalled 9.10, installed it again from my 9.10 CD which I ordered by post (thank you guys), then after successful install I rebooted, entered Ubuntu, then upgraded to 10.04

got stuck at the same point with preparing memtest86+ and it keeps saying found the image... 

pressed Ctrl+c, skipped and everything went fine, installed Grub to all 3 locations... it's working well, haven't rebooted yet tough and kind of don't want to :D

UPDATE: I did the sudo dpkg --configure -a in terminal after it was done, then rebooted, and it works perfectly well and fast!

---

### Post by eatloaf on 2010-05-09
Wow.  Just wow.  I've got the same deal.  If this hoses my machine then I'm giving the boot to ubuntu.

you get what you pay for, i guess.

---

