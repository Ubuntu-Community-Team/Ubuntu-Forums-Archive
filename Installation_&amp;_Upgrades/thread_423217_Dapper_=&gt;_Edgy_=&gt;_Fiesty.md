---
title: "Dapper =&gt; Edgy =&gt; Fiesty"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by ronb on 2007-04-25
I need to upgrade from Dapper, and according to these instructions [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") I need to upgrade to Edgy first then Fiesty. But the instructions don't say how to upgrade to Edgy.:confused: 

Now that Fiesty is out, there are no links to the Alternate Installation CD for Edgy. I have update manage 0.42.

Does anyone know how to go from Dapper to Edgy without the alternate CD? I'd prefer not to do a clean install.

Thanks for any ideas.

rb

---

### Post by mrpaco on 2007-04-26
[Try method b in this post.]("http://ubuntuforums.org/showthread.php?t=227052").  No guarantee that it will work, but it is worth a shot.  Just be sure to back everything up.

---

### Post by ronb on 2007-04-26
Thanks. I'll give that a try over the next couple of days and let you know how it went.

---

### Post by ronb on 2007-04-26
I wasn't able to upgrade with those instructions. Fortunately, I did backup my home directory and much of var because my system is a mess now. I think that if I could delete some files and get more space on the hard drive that I might be able to complete the upgrade, but I can't get nautilus to start.

I tried to re-install nautilus, but that doesn't seem to work. Every once in a while I get a message saying, "can't set the locale." Beats me why it didn't use what was there. It must have been right once.

---

### Post by aysiu on 2007-04-26
I don't know if you care, but my two cents--upgrading from Dapper to Edgy and then from Edgy to Feisty will take a *really* long time, even if you have a fast internet connection. And you can't even walk away and leave it overnight. You have to answer questions. I'd give it a minimum of five hours... a *minimum*... for downloading the packages and/or Alternate CDs and then unpacking the packages and setting up the packages, etc.

You'd be better off [creating a separate /home partition](http://www.psychocats.net/ubuntu/separatehome) and then reinstalling Feisty instead of doing two upgrades.

If you're worried about having to figure out all the packages to reinstall, try this:
[Save state of installed packages?](http://ubuntuforums.org/showthread.php?p=1069593#post1069593)

---

### Post by ronb on 2007-04-27
Thanks anyway for the shortcut tips, but I had already started down the road. I had a lot of interuptions and problems, but I finally made it to Edgy. Somehow I fixed the locales problem. I was trying many different things from the forums. I don't know what did it.

I've been very busy, and I haven't gotten to Feisty yet. But Edgy seems to be working reasonably well at the moment.

Next week I'll start on Feisty. I can't recommend that anyone try long-term support if there isn't an easy way to upgrade after skipping one or more versions.

---

