---
title: "New Install or Upgrade from 9.10"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2010-03-12
I was wondering if I wanted to load 10.04 Alpha 3 now, would it be better to do a fresh install or an upgrade from 9.10...  I have files I don't want to loose such as documents, graphics and photo's.  I intend to back those up.

What is everyone's opinion on upgrading versus new fresh install.

---

### Post by jppr on 2010-03-12
It is always better do new and fresh install ;) You can do /home and copy there your photos and whatever you have

---

### Post by Bochonok on 2010-03-12
> **alienexplorers said:**
> I was wondering if I wanted to load 10.04 Alpha 3 now, would it be better to do a fresh install or an upgrade from 9.10...  I have files I don't want to loose such as documents, graphics and photo's.  I intend to back those up.

What is everyone's opinion on upgrading versus new fresh install.
It's best to have separate partition for your /home.

---

### Post by alienexplorers on 2010-03-12
I currently have a seperate /home partition in Ubuntu 9.10. Can I leave it and just load the main partition /root with the new version of Ubuntu 10.04 Alpha 3.

---

### Post by phillw on 2010-03-12
> **alienexplorers said:**
> I currently have a seperate /home partition in Ubuntu 9.10. Can I leave it and just load the main partition /root with the new version of Ubuntu 10.04 Alpha 3.

When I first wanted to test 10.04, it was advised to me that I should not 'share' my 9.10 /home with 10.04, in case 10.04 did something untoward. I have maintained two homes. Periodically I rsync the 10.04 one to 9.10 (As I use 10.04 99% of the time now). This keeps things like bookmarks, documents etc available on each system, but a catastrophic mis-hap within 10.04 would not be able to wipe-out my 9.10 /home.

Regards,

Phill.

---

### Post by VMC on 2010-03-12
This is just me, but I have never had but one partition and /home is embedded into the "/" partition. If I feel the need to just upgrade then I don't format the partition and /home is left intact, with all the settings.

I do make backups of my home folder for future reference.

---

### Post by grandtoubab on 2010-03-12
> **jppr said:**
> It is always better do new and fresh install ;) You can do /home and copy there your photos and whatever you have
Urban legend !!! upgrade is ok and is the official way.
refer to
[http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3)

---

### Post by Tikkyca on 2010-03-12
Upgrade,because i will save all my files.

---

### Post by phillw on 2010-03-12
> **alienexplorers said:**
> I currently have a seperate /home partition in Ubuntu 9.10. Can I leave it and just load the main partition /root with the new version of Ubuntu 10.04 Alpha 3.

Further to my earlier reply, this is the advice I was given ..

[http://ubuntuforums.org/showthread.php?t=1351477](http://ubuntuforums.org/showthread.php?t=1351477)

Regards,

Phill

---

### Post by Vanishing on 2010-03-12
> **alienexplorers said:**
> I was wondering if I wanted to load 10.04 Alpha 3 now, would it be better to do a fresh install or an upgrade from 9.10...  I have files I don't want to loose such as documents, graphics and photo's.  I intend to back those up.

What is everyone's opinion on upgrading versus new fresh install.

I wouldnt reinstall..just backup and update?
maybe you can reinstall when lucid finally comes out..

---

### Post by teh603 on 2010-03-12
To be honest, I'd suggest waiting for Beta 1. Its only about six days out now. Alpha 3 still has some issues to be worked out, particularly the Plymouth/ureadahead "broken pipe" issue.

Guess the devs should've used iron pipes instead of steel ones, eh?

---

### Post by wilee-nilee on 2010-03-12
Personally I have been using Lucid since it was available, but I have all my stuff on a external HD, rather then a separate home. I also have 2 other operating systems on my computer so I can mess with Lucid with no worries. 

If all I had was one OS then I would not upgrade/install to a development unless I knew I would not lose anything and I had my trusty install disc ready in case of problems.

If you are familiar with installing and partitioning and other system adjustments then go ahead, but be careful not to leave yourself in trouble losing any important personal data.

The fresh install especially if done with a USB thumb is very fast, a upgrade could take 2-4 or more hours. You have to update the fresh install with the extras you had in 9.10 though, so this does add a little time but is still less time in my experience then upgrading.

OP is the 9.10 you have running grub2 and using ext4?, or was this a upgrade?

---

### Post by alienexplorers on 2010-03-13
I decided to triple boot Win 7, Ubuntu 10.04 and Ubuntu 9.10....  I now can check out Lucid without messing with my 9.10 installation.  Thanks for all the info.

---

### Post by awi on 2010-03-13
If you have only software  provided by ubuntu official repositories, do an upgrade and you will be fine (but a backup never harmed anyone :).
I personally install lots of software from other repositories, and always had problem with upgrade, because sometimes those softwares "breaks" ubuntu's base system (i.e. official Sun/Oracle java).
So rule of thumb, from my experience:
- Fresh install if you do personalization and third party installations
- Vanilla upgrade if you are a vanilla user :)

---

