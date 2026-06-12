---
title: "Upgrade from 7.04 Ubuntu to 8.04 Xubuntu"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by peter d on 2008-07-09
Hi,

I have an old laptop with 256 MB ram. It's running 7.04 Ubuntu quite happily at present.

I would like to upgrade to 8.04, but am not keen to upgrade the ram. How do I upgrade to 8.04 Xubuntu without doing a clean install from CD?

Any help much appreciated.

---

### Post by avtolle on 2008-07-09
You would need to do a sequential upgrade (from 7.04 to 7.10 to 8.04). [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion) discusses how this is to be accomplished, should you choose to do it.

EDIT: I understand you are using Xubuntu, but the process should be very similar if not identical as that outlined in the link.

---

### Post by peter d on 2008-07-10
> **avtolle said:**
> You would need to do a sequential upgrade (from 7.04 to 7.10 to 8.04). [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion) discusses how this is to be accomplished, should you choose to do it.

EDIT: I understand you are using Xubuntu, but the process should be very similar if not identical as that outlined in the link.

Thanks Avtolle,

I'd kind of assumed that, but what do I do to remove ubuntu-desktop (and kubuntu-desktop) so that I have a clean Xubuntu upgrade? Or do I not need to worry about that, and simply upgrade from within the XFCE desktop?

---

### Post by avtolle on 2008-07-10
If I understand you last question, once upgraded to 8.04, you could install the xubuntu-desktop package from Synaptic, and then, when booting, choose from the options manager to boot in xfce (I think that's how the option is labeled) which would boot you into xubuntu. Let me take a look at something and be back with a link.

EDIT: Take a look at this link [http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce) to get to "pure" xfce once upgraded to 8.04.

---

### Post by peter d on 2008-07-10
I can log into XFCE now by changing session on the log in screen. I have the choice of Xclient, Gnome or XFCE (don't think I have KDE available on the install I have.) If I make XFCE my default will that make any upgrade small enougn to run OK on my 256mb ram laptop.

I'm happy to try that and to take the chance that I will need to do a full install from scratch if necessary - but it would be easier if I didn't have to do that.

The question that bothers me is, should I remove ubuntu-desktop before I do the upgrade?

---

### Post by SkonesMickLoud on 2008-07-10
You should (if you're not going to use them) remove Ubuntu and Kubuntu before you upgrade.  If you don't, your upgrades will take much longer, as you will be upgrading x 3.

Try running the link avtolle gave you before you upgrade.

---

### Post by avtolle on 2008-07-10
You could do so, which likely would speed up the upgrade. Since I presume you installed Ubuntu originally, with the 7.04 installation running Gnome, and then added the xubuntu desktop later, please follow the link in the link I gave you earlier to the discussion under Feisty. As I recall, to remove Gnome in that situation (which is what you really want to do) you will need to follow the terminal command part of the article. Good luck.

---

### Post by snowpine on 2008-07-10
> **peter d said:**
> I can log into XFCE now by changing session on the log in screen. I have the choice of Xclient, Gnome or XFCE (don't think I have KDE available on the install I have.) If I make XFCE my default will that make any upgrade small enougn to run OK on my 256mb ram laptop.

I'm happy to try that and to take the chance that I will need to do a full install from scratch if necessary - but it would be easier if I didn't have to do that.

The question that bothers me is, should I remove ubuntu-desktop before I do the upgrade?

Hi Peter, while I've never done exactly what you're trying to do, here is my understanding of how sessions work. 

When you select an Xfce session, it only loads that environment--it doesn't load Gnome. If you then start up an application that has Gnome dependencies, it's at that point they are loaded. So, having Gnome installed, but not using it, does not tax your RAM usage at all; it only takes up space on your hard drive. I guess a (poor) analogy would be driving to work in a compact car (xfce) vs. an SUV (gnome). If you drive xfce, the gnome-mobile still takes up space in your 2-car garage, but it's not using gas. :)

Logically it makes sense to me that removing ubuntu-desktop prior to the upgrade would save time, since all of those packages would then not need to be upgraded. But that opinion is not based on personal experience. :) Good luck!

---

### Post by peter d on 2008-07-10
Thanks Avtolle, thanks Skones, thanks Snowpine

That's much clearer. I'll give it a go soon. It's all pretty much what I expected but it's good to have some advice.

---

