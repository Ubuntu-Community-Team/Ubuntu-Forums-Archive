---
title: "Linux-generic update problem and sound/wifi broken"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by hotdoog on 2011-03-07
Hi,

I just upgraded (included kernel updates) using the normal update manager on my wife's Dell 1420 Inspiron Ubuntu 8.04.4 LTS with security, proposed and backports. After the upgrade reboot the sound and wifi were broken--- the system reported there was no hardware. I suspect this is simply a bug with the new kernel. A couple years ago a similar bug to the sound driver forced us to skip a kernel. I suppose I should file a bug report about this somewhere?

It is simple enough to boot into the previous kernel where sound/wifi do function, for now.

However I'm also getting a strange dependency problem for the packages **linux-generic linux-image-generic linux-restricted-modules-generic**

These packages "have been kept back" according to aptitude. They are stuck at 2.6.24.28.30. I'm unable to force install them to the newer  2.6.24.29.31 to match the other latest installed packages and the latest kernel listed on the GRUB menu. I wonder if the reason the sound and wifi are broken is that these won't update.

If I try to update the aptitude dialogue gives me solutions with +259 to remove the linux-generic package. But isn't that an important package that I need? Why is it suggesting I remove these? Maybe they are obsolete meta-packages? I can't get it to install 2.6.24.29 no matter what I do. I removed and then installed these packages and none of that get the sound working. To remove and install I had to run aptitude and it would give me solutions saying -29000 but I did it anyway to try and force it. None of it worked so I just put it back to the way it was, with the "held back" 2.6.24.28. I don't really understand package dependency.:confused:

Any help would be appreciated.

Thanks.

---

### Post by Dutch70 on 2011-03-07
Sorry I can't help you with your problem, but before you spend too much time on it, being here since 2006, you do know that support/security updates for Hardy end next month right? :)

---

### Post by nss0000 on 2011-03-07
Yes:

UBUNTU 10.04 has taken a while(too long)  to stabilize, yet right now it is robust and complete. I will even say "helpful" for any usrland tasking. With zero talent and little more than mouser copy/paste skills I just installed a scanner and headphones ...   

True enough, you can reject automagic pleasure and conjure misery  by insisting on dual-boot or laptop-install ... but, that's a neo-puritan thingy that many reject on principal. Huge screens, fat-boxes, smoking graphics cards and retro 15-lb Toshiba keyboards make a real man happy.

---

### Post by hotdoog on 2011-03-07
> **Dutch70 said:**
> Sorry I can't help you with your problem, but before you spend too much time on it, being here since 2006, you do know that support/security updates for Hardy end next month right? :)

I thought LTS was 5 years. I know that upgrading is the eventual route but this seems like a straightforward bug I should be able to fix before having to do that. Just because the latest security isn't installed I still think aptitude should upgrade kernels properly.

nss0000 I have no idea what you are talking about. Are you recommending I dump a laptop for a Desktop? I have both. I use Ubuntu on both. I've avoided updating the OS for my wife's laptop because it works for her now, I thought the LTS means 5 years, and right now I don't have the time to do a very careful update to make sure none of her functionality breaks during that upgrade.

---

### Post by Dutch70 on 2011-03-08
> **hotdoog said:**
> I thought LTS was 5 years. I know that upgrading is the eventual route but this seems like a straightforward bug I should be able to fix before having to do that. Just because the latest security isn't installed I still think aptitude should upgrade kernels properly.

5 years for servers, 3 years for desktops. 
[[COLOR="Blue"]http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.04_LTS_.28Hardy_Heron.29[/COLOR]]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.04_LTS_.28Hardy_Heron.29")

If you created a separate /home partition when you installed Ubuntu, it just takes about 30min to an hour for a fresh install. 
If you didn't create a separate /home, within the next month would be a good time to do that. 

You never mentioned which kernel you had or which one you updated to. AFAIK when kernel updates come out, they usually are a little buggy. 
Some people totally block them. Not to sound mean, but if I was short on time & I could still log into my old kernel. 
I wouldn't waste any more time worrying about this one. 

You can try to upgrade to 10.04, but unless you have a very basic system, you'll probably have problems. 
This is why so many people recommend a separate /home. 
It makes the install process like a walk in the park.

Good luck

---

