---
title: "Stuck with Jaunty"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by TheHimself on 2011-08-14
I have Jaunty 9.04 on my computer. I can't install software via synaptic anymore. To add assault to injury, I can't upgrade to Lucid via update manager either. What can I do?

---

### Post by Enigmapond on 2011-08-14
You can't update on Jaunty because it reached End of Life. Your best bet is to save all important data and download the LiveCD of either 10.04 (I recommend) or 11.04 and do a fresh install. There are no more repos for Jaunty. Lucid rocks though..:)

---

### Post by coffeecat on 2011-08-14
> **TheHimself said:**
> I have Jaunty 9.04 on my computer. I can't install software via synaptic anymore. To add assault to injury, I can't upgrade to Lucid via update manager either. What can I do?

Actually, you can upgrade Jaunty and then upgrade to Karmic and then to Lucid, but you need to take a deep breath beforehand. :wink:

Have a look here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Which links to this (which you need to read carefully):

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

The instructions in that link may or may not work as they are, but they may not because Karmic is now also end-of-life. What I did was to trick Jaunty into thinking that Karmic was still supported. Then the upgrade to Karmic was OK and Karmic to Lucid went without a hitch. Here's my secret recipe:

[http://ubuntuforums.org/showpost.php?p=11129193&postcount=8](http://ubuntuforums.org/showpost.php?p=11129193&postcount=8)

As you can see I went all the way to Natty (11.04) which took some time, but it worked.

Good luck!

---

### Post by TheHimself on 2011-08-14
I came up with a low cost solution. In Synaptic, in
 Settings->Preferences->General
I chose
system upgrade: Always ask.
Then in "software sources" I unchecked everything in "Ubuntu software" and then in third party software I added

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe

In "Update" I chose "Only notify about ...".  Then reload and voila! I have a working software channel.  Now I can "upgrade" as I wish; say I would like to upgrade one package to Lucid version and not upgrade another one. :guitar: This is not possible in "system upgrade".

**Important:**If you read this and would like to do the same, you'd better disable Update Manager and if you do "Mark all upgrades"+Apply in synaptic, there is no guaranty that you'll end up with a working Ubuntu.

---

### Post by coffeecat on 2011-08-14
@TheHimself, if it hasn't done so already, your low-cost solution will turn out to be very expensive by breaking your system. Particularly:

> **TheHimself said:**
>  Now I can "upgrade" as I wish; say I would like to upgrade one package to Lucid version and not upgrade another one. :guitar: This is not possible in "system upgrade".

Do this and you will end up in dependency hell. Applications in one version of Ubuntu are mostly compiled to work with particular shared libraries that also come with that version. You will get away with installing some Lucid packages in Jaunty, but then one day - or tomorrow - something will go horribly wrong.

**Also** - you should not upgrade from Jaunty to Lucid directly. You must go via Karmic. Another reason not to be blindly installing Lucid packages in Jaunty.

Finally:

> **Important:** If you read this and would like to do the same - **don't!**

Fixed that for you. :wink:

---

### Post by TheHimself on 2011-08-15
We'll see  coffeecat. Although you are right for the most part.

---

