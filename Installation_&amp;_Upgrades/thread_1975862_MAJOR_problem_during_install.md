---
title: "MAJOR problem during install"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by PfromD on 2012-05-07
OMG I hope someone can help me out of this terrible ordeal!
I had some problems upgrading 10.04LTS to 12.04LTS due to not enough free space. I then freed space enough to satisfy the upgrade routine .. I THOUGHT.
From about 7/10ths of the way it began complaining about lacking space .. again, but by then the process was beyond the point of no return :( and ended up just turning off the computer, and needless to say that any start up in Ubuntu wasn't possible thereafter :'(
And of course I was dumb enough to not have made a backup of my most needed and fairly important documents :(
I attempted to access the document folder via a USB Ubuntu but the keyring (right?) password is not, as I thought, my old log in from Ubuntu as before attempting the upgrade.
Why the h... doesn't the upgrade process identify from the start that there aren't enough space to follow the whole process through and pleeeease tell me anything but that those very much needed documents are bye bye.
The has to be SOMETHING I can do to get out of this very deep hole.

---

### Post by plant on 2012-05-08
While booting from live usb or ubuntu bootable disc, the root password won't be your old login. Just take a terminal and type 'sudo su', usually in terminal it will enter the root(while trying ubuntu without installing). If (in case) password is asked then try the password "linux".  You can then mount your old linux partition and access your important files.

---

### Post by oboedad55 on 2012-05-08
> **PfromD said:**
> OMG I hope someone can help me out of this terrible ordeal!
I had some problems upgrading 10.04LTS to 12.04LTS due to not enough free space. I then freed space enough to satisfy the upgrade routine .. I THOUGHT.
From about 7/10ths of the way it began complaining about lacking space .. again, but by then the process was beyond the point of no return :( and ended up just turning off the computer, and needless to say that any start up in Ubuntu wasn't possible thereafter :'(
And of course I was dumb enough to not have made a backup of my most needed and fairly important documents :(
I attempted to access the document folder via a USB Ubuntu but the keyring (right?) password is not, as I thought, my old log in from Ubuntu as before attempting the upgrade.
Why the h... doesn't the upgrade process identify from the start that there aren't enough space to follow the whole process through and pleeeease tell me anything but that those very much needed documents are bye bye.
The has to be SOMETHING I can do to get out of this very deep hole.

Just boot from a LiveCD of some sort, can really be any Linux distro and copy your files to a USB. You won't need a password.

---

### Post by darkod on 2012-05-08
I don't see why you are blaming ubuntu, you were the one so optimistic to upgrade with the last 1% of your space free. An OS is a complex software and they can't always make it the way we want it to be in the situation we put ourselves in.

As already said, working from live mode should give you full access to any documents/data on the hdd and shouldn't ask you for any passwords etc. Just copy them where ever.

If you could still free some space, and if the upgrade process started configuring the packages but didn't finish all of them due to lack of space, you can also continue the configuration which should finish the upgrade.

But we can talk about that after you copy your data and free some space if you want to continue with it.

---

### Post by PfromD on 2012-05-08
I think it's fair enough to be at least a little annoyed when the upgrade process initially says "680mb free space to little to *complete* the upgrade", then freeing up about a gig, and winding up with this problem anyway.
But the problem is bigger than that, because I had the home folder secured, and now I can't access it because "you're not the owner of this folder".
During the failed upgrade I saw what would very likely end up happening and attempted to move the documents I now fear loosing to another drive, but by then I couldn't open any folders, neither the document folder or the new temp. folder while the upgrading went on... and then shortly after it turned off the computer on its own

---

### Post by darkod on 2012-05-08
By secure you mean encrypted?

If that is the case, you really might be in trouble. I don't have a clue about encryption, sorry.

To receive more attention from someone who might know, it could be better to open a new thread with title like "how to access my encrypted home after failed upgrade and unbootable system".

Not sure if this same section or the Security section would be a better choice. It could fit into both sections really.

---

### Post by PfromD on 2012-05-08
yes, encrypted :( I just hope it's possible to somehow 'log on' the folder using the same login I used on the Ubuntu install as it were before this this botched upgrade.
I've never ever had a problem like this with Ubuntu and thus probably underplayed the (obvious) need for backup and so on.
It's mainly a budget I've tweaked to perfection over something like 1½ years

---

### Post by darkod on 2012-05-08
You can try the option to free some more space from live mode, and try to finish the upgrade. The packages are downloaded, they are just waiting to be configured (usually).

To be honest, I am very surprised you go to the lengths to have encryption but not backup. :)

Try to free some more space, and then to enter with chroot and run:
dpkg --configure -a

If you need help with the chroot we can help.

---

### Post by darkod on 2012-05-08
This seems to have explanation how to enter encrypted home:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Not sure if this can help too, it's a bit old but it says solved:
[http://ubuntuforums.org/archive/index.php/t-1521023.html](http://ubuntuforums.org/archive/index.php/t-1521023.html)

---

### Post by PfromD on 2012-05-08
thanks, I'll try and check it out.
I've learned that I suck at finding the answers I need in this forum no matter how I try to search it out, so hopefully your posted thread will help me out

---

### Post by darkod on 2012-05-08
If it helps you for the future, those two links were google results of a search "getting into encrypted home from live mode in ubuntu".

I also don't search the forum inside it, because it is very well covered by google, including the archived threads, it's better to do it in google. The problem is finding the right search phrase and spotting the good links from the bad ones. :)

---

### Post by PfromD on 2012-05-08
you're probably right there as I usually find what I need using google. just been thinking that searching the source i.e. this forum it self provides more/better results.

---

### Post by Slim Odds on 2012-05-08
> **PfromD said:**
> you're probably right there as I usually find what I need using google. just been thinking that searching the source i.e. this forum it self provides more/better results.

This forum is NOT the SOURCE of Ubuntu.

---

### Post by mips on 2012-05-08
If it was me then I would just backup my /home and start with a clean install.

680MB is not a lot of free space, an iso cd of ubuntu wont even fit into that.

---

### Post by PfromD on 2012-05-08
yup, this was a great .. how do say ... learning experience ;)
I've just never seen any great need for those kind of precautions (backup asf.)as Ubuntu has always just .. *worked* :-)
And if it ain't working as is, then there's always good help to get here. Hooked since 5.something :)
Still annoyed though that the upgrade says it needs 680MB more to work, and then turns out to need more, and smashes up the whole process over probably 50-100MB.
But never mind .. I'm good on my way to getting everything back

---

### Post by PfromD on 2012-05-08
> **Slim Odds said:**
> This forum is NOT the SOURCE of Ubuntu.
I KNOW, but it's the source for the best help IMO

---

