---
title: "URGENT: problems after installing Ubuntu"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by Kuo000 on 2010-12-22
Hi all,
 
I just installed Ubuntu (with wubi) an hour ago on my Fujitsu laptop which had only Windows XP Pro. Everything was good, and I started using the Ubuntu. I saw there were some updates in the Update Manager, and I chose to install them all. But after installing the updates and rebooting my computer, I couldn't even get to the place where I can choose between Windows XP Pro and Ubuntu. Instead, I got to a screen like:
 
error: no such device: 3681b168-edf4-495a-b7a9-9392b6ac7085
grub rescue>
 
 
No matter what I typed at the command prompt, I couldn't proceed. I think the problem is that during the updates I chose to install something like GRUB and Fujitsu device....
 
Now, I cannot even log in any operating system and am very anxious about this. Can anyone save me, please? Many many thanks.

---

### Post by Chazz44able on 2010-12-22
exactly that happened to me when I was running WUBI with the updates, I was able to still access the grub. What I would do is to Re-install the GRUB2 (or if there isn't one, then install one off a Live CD

---

### Post by Chazz44able on 2010-12-22
Here's the link to the post explaining it: [http://ubuntuforums.org/showthread.php?p=9884063#post9884063](http://ubuntuforums.org/showthread.php?p=9884063#post9884063)

---

### Post by Kuo000 on 2010-12-22
> **Chazz44able said:**
> exactly that happened to me when I was running WUBI with the updates, I was able to still access the grub. What I would do is to Re-install the GRUB2 (or if there isn't one, then install one off a Live CD
 
First, thank you for the fast reply.
 
Do you mind giving me the steps in installing GRUB2. (Also I have absolutely no idea what GRUB is. Can you enlighten me a bit?)
 
Btw, how would installing the GRUB2 solve the problem? Would I be able to get back to my windows operating system and ubuntu as before after installing this?
 
Thank you.

---

### Post by Chazz44able on 2010-12-22
okay, the link I gave you explains it all (in terms or installing GRUB2). GRUB is basically like a menu that gives you links to the different operating systems on your system as soon as you boot-up. You'll have to talk to the guy who made the post that I linked you to as to whether it will work with WUBI, although if I remember correctly, he explains that... so ask him/her on that post and it'll get worked out for you.

TBH, I'd recomend that you dual-boot anyway, it'll give you access to other useful functions (Hibernation isn't available in WUBI) and be the proper, stable OS that Linux is.

---

### Post by kansasnoob on 2010-12-22
If this is a Wubi install reinstalling grub is the wrong thing to do. Here's an example of a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If it is a Wubi install this thread should be helpful:

[http://ubuntuforums.org/showpost.php?p=10207564&postcount=1](http://ubuntuforums.org/showpost.php?p=10207564&postcount=1)

If you're totally unsure what's up please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by wilee-nilee on 2010-12-22
> **kansasnoob said:**
> If this is a Wubi install reinstalling grub is the wrong thing to do. Here's an example of a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If it is a Wubi install this thread should be helpful:

[http://ubuntuforums.org/showpost.php?p=10207564&postcount=1](http://ubuntuforums.org/showpost.php?p=10207564&postcount=1)

If you're totally unsure what's up please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

+1 no grub installing in a Wubi, don't accept update/upgrades for grub-pc or grub-common.

Post the script we can see whats up if you need and if you don't have a XP recovery or install disc there is a handy Linux bootloader that works, not grub though.

---

### Post by Kuo000 on 2010-12-22
> **wilee-nilee said:**
> +1 no grub installing in a Wubi, don't accept update/upgrades for grub-pc or grub-common.
 
Post the script we can see whats up if you need and if you don't have a XP recovery or install disc there is a handy Linux bootloader that works, not grub though.
 
Hi,
 
I did use wubi to install the ubuntu. Yea, I think the sad thing is I accepted the grub-pc update.
 
Now, when i boot my computer, right after the Fuhitsu screen, I got a black screen with prompt:
 
error: no such device: 3681b168-edf4-495a-b7a9-9392b6ac7085
grub rescue>

Any help from there?? Thanks.

---

### Post by wilee-nilee on 2010-12-22
If you don't have a XP recovery or install disc, a way to get to the repair command line you can fix this with a Ubuntu cd. So weigh your choices here; and download the Ubuntu ISO and burn it to a cd or load a thumb if you need it.

If you have a XP recovery disc, follow this link.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

I learned a lot of this from watching kansasnoob so we have a killer back up here amongst many others.

---

