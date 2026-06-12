---
title: "Version confusion"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by boxcorner on 2011-05-02
I was using Ubuntu 10.04 and ran the upgrade.
System > About now says I am now using 11.04
However, System > Administration > Update Manager says New Ubuntu release '11.04' available > Upgrade
Should I run the upgrade again, or is there a quicker way to fix this?
Thanks in advance for any help!

---

### Post by Dutch70 on 2011-05-02
You can only upgrade one distro at a time, so I would have to think you upgraded to 10.10.

What is the output of...
cat /etc/issue

using system > about has a bug & may report that you're using 11.04 when you're not. The above command will tell you which version you are using, however, I think you'd know if you were using 11.04. ;)

---

### Post by boxcorner on 2011-05-03
> **Dutch70 said:**
> You can only upgrade one distro at a time, so I would have to think you upgraded to 10.10.

What is the output of...
cat /etc/issue

using system > about has a bug & may report that you're using 11.04 when you're not. The above command will tell you which version you are using, however, I think you'd know if you were using 11.04. ;)
Thanks for your reply. The output of cat /etc/issue is Ubuntu 10.10 \n \l
Various things changed following the Upgrade, such as the login, icons, Thunderbird has been changed back to Shredder, and Firefox has been changed back to Namoroka.
Without knowing about one distro at a time and without having seen 11.04 it was puzzling.
If I recall correctly, prior to running Upgrade, after doing an update, I changed the Settings, in Update Manager.
I checked Proposed updates, and changed Show new distribution releases from Long term support releases only, to Normal releases.
I'll run Upgrade again as soon as I can spare my PC for several hours.  The bandwidth here is very poor, so downloads take ages.

---

### Post by Dutch70 on 2011-05-03
I wouldn't be in any hurry to go to 11.04. Natty is still buggy, and probably will be for a couple months. Also, every time you upgrade there is less chance that it will be successful. 

If you did so much as 1 successful upgrade, you've done better than me. I've never been able to upgrade successfully, but then the more you change or modify your system from it's original state, the less likely you are to be able to upgrade & mine is always changed quite a bit. 

I would recommend a fresh install. If you have a separate /home, there is nothing to it. Even if you don't have a separate /home, a fresh install is still the way to go in my opinion.

There is some really good info here...
[[COLOR="RoyalBlue"]I upgraded, and now I have this error... [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by boxcorner on 2011-05-03
> **Dutch70 said:**
> I wouldn't be in any hurry to go to 11.04. Natty is still buggy, and probably will be for a couple months. Also, every time you upgrade there is less chance that it will be successful. 

If you did so much as 1 successful upgrade, you've done better than me. I've never been able to upgrade successfully, but then the more you change or modify your system from it's original state, the less likely you are to be able to upgrade & mine is always changed quite a bit. 

I would recommend a fresh install. If you have a separate /home, there is nothing to it. Even if you don't have a separate /home, a fresh install is still the way to go in my opinion.

There is some really good info here...
[[COLOR="RoyalBlue"]I upgraded, and now I have this error... [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")
Thanks again for your reply, and the tip.

I think this was my second upgrade; both times I found it quite nerve-wracking.
This time it seemed to stop more frequently, awaiting replies to various questions.
When it reached the end and tried to re-boot automatically, it seemed to get stuck with just a flashing cursor on the screen.
I left it like that for a very long time and when I was quite sure there was no disk activity I hit reset.
It then booted normally, and has done so since without any problems.  

I just wish it hadn't altered Thunderbird and Firefox, as I can't remember how I managed to change them back last time.
Oh well, yet something else to add to my ToDo list.

Think I'll take your advice and stay with this version for a while, before upgrading again, or maybe do a fresh install later.
Anyway, we're currently experiencing electric storms here, so there's a real risk of a power cut.  
Knowing my luck, I'd lose power at the worst time, part way through an upgrade!

---

### Post by Dutch70 on 2011-05-03
You're welcome

If you decide to reinstall & want to add a separate /home partition, have a look at this link. 
[[COLOR="Red"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Now that ext4 is stable, I would use it instead of ext3 which it recommends.
Also, if you want to hibernate successfully, your swap should be equal to or slightly larger than your physical RAM. 
[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by boxcorner on 2011-05-05
> **Dutch70 said:**
> You're welcome

If you decide to reinstall & want to add a separate /home partition, have a look at this link. 
[[COLOR="Red"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Now that ext4 is stable, I would use it instead of ext3 which it recommends.
Also, if you want to hibernate successfully, your swap should be equal to or slightly larger than your physical RAM. 
[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")
Excellent.  Thanks again for the tips.

---

