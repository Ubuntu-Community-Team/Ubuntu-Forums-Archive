---
title: "Downgrade from 11.04 alpha to 10.10?"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by donalgodon on 2011-03-12
First post. 

Is there anyone who can give me some help on how/if I can downgrade my dual-boot partition (win-7/11.04) to 10.10 without having to reformat the entire disk?

Can I use the same partition I installed the alpha 11.04 on to install 10.10 and save myself a lot of work?

Is it possible to simply reformat the Ubuntu Linux partition and re-install 10.10 there while preserving my Windows 7 installation?

Can I keep the newer GRUB boot loader for 11.04 (I like it better), or will I be forced to downgrade that as well?

I just tried the alpha, and I can't use it. It's still too green, so I want to go back to 10.10 the easiest way possible, but I'm new to Ubuntu, so I'd need a little detail on the process of using the advanced partition features (if this is even possible).

Thanks in advance to any and all responders.

---

### Post by Frogs Hair on 2011-03-12
I'm afraid down grades are not possible , you will have reformat the Ubuntu portion of the disk . See the Ubuntu after Widows section at the link. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by donalgodon on 2011-03-12
Okay, I don't mind having to reformat the Ubuntu partition, but I tried it once and ended up unable to do anything, and having to reformat the entire disk and start again.

Is there a simple way to reformat the partition from the Live install CD and re-install to it?

I've tried (and failed) to do this, so I'm here asking. :)

---

### Post by donalgodon on 2011-03-14
Solved. I realize why I failed. It's that I was not aware that you needed to select the FIRST option in the drop down menu of the advanced formatting section that is labeled simply "/" (no quotes)when selecting the existing ext.4 partition to reformat and install. Simply selecting the partition alone, even with reformat, does not allow installation until the sub menu is selected.

I also did not know that one may change distros in this way as well, if one chooses. 

Might help other noobs like me in the future.

---

### Post by Frogs Hair on 2011-03-14
Glad it is sorted out , thanks for posting your solution .

---

### Post by asalina on 2011-04-30
It's not sorted out for me. I'm just now learning that 11.04 is an ALPHA. This is after I got a
pop-up window on my desktop (for the first time ever) advising me to upgrade to 11.04.

Why is this pop-up advising people to upgrade when the upgrade is still just an ALPHA
release?

Now I can't run any of my OpenGL applications (not even fgl_glxgears or glxinfo will run)
and I can't compile anything because of libraries that can't be found (they are installed,
they just cannot be found).

I had a perfectly good installation with 10.10 and now I'm going to have to wipe my hard
drive because of an ALPHA release. Nice going, Ubuntu team.

---

### Post by AlanPo on 2011-05-18
Sad that downgrade from 11.04 is not possible. This is weird. Now all my 10.10 desktop is gone.  and email data in evolution is gone too.

Hope next time canonical will at least pop up the message that upgrade will permanently delete all you have had and change your desktop to weird thing.

---

### Post by donalgodon on 2011-05-18
> **AlanPo said:**
> Sad that downgrade from 11.04 is not possible. This is weird. Now all my 10.10 desktop is gone.  and email data in evolution is gone too.

Hope next time canonical will at least pop up the message that upgrade will permanently delete all you have had and change your desktop to weird thing.

Realistically, I don't consider the 'downgrade' possible option when I think about how much of the core components change each time a major revision comes, but yeah, I do think they should warn the user, particularly with Ubuntu's market target for new users who might not understand that risk of data loss.

---

