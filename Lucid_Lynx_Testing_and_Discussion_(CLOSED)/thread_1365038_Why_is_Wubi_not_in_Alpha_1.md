---
title: "Why is Wubi not in Alpha 1?"
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phrostbyte on 2009-12-26
I'm just curious, why is Wubi missing from Alpha 1? Will it be in future builds?

---

### Post by vrkalak on 2009-12-26
Lucid is still pretty early on in the development cycle.
[I]
**"All in due time, my pretty. All in due time."**[/I]

I am getting on average 15-30 upgrades/updates from the daily-builds of Xubuntu-Lucid.
And, so far, have not seen any changes to the themes and artwork.
However, some programs that were included in the Alpha 1, release have already been changed to another App. entirely.
We'll see what other changes are coming for Lucid?  :P

Watch and see what comes about the closer we get to the Final release

---

### Post by ranch hand on 2009-12-26
You know it amazes me how folks do not read the release infor in the sticky area of this forum.  The FIRST art drop, for instance is 2-25-10 which is also the release date for A3.

With a little search one could find this too;

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

for more details.

This stuff is not a secret.  If you follow the detailed links on the wiki you will probably find out when wubi is due.  Or you could use a search engine and find it.

As for me, I think it should be left out but then I won't have my box polluted with MS products.

---

### Post by Seventh Reign on 2009-12-26
> **ranch hand said:**
> You know it amazes me how folks do not read the release infor in the sticky area of this forum.  The FIRST art drop, for instance is 2-25-10 which is also the release date for A3.

With a little search one could find this too;

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

for more details.

This stuff is not a secret.  If you follow the detailed links on the wiki you will probably find out when wubi is due.  Or you could use a search engine and find it.

As for me, I think it should be left out but then I won't have my box polluted with MS products.


Its fairly common knowledge that no one reads or uses the search feature.  They avoid it like the plague.  There are always 10-15 of the exact same topic on the EXACT same page.  :confused:

---

### Post by garvinrick4 on 2009-12-26
Use karmic wubi and:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade


Will do until they put Wubi on the installation Disk.

---

### Post by ranch hand on 2009-12-26
What is that called - kwubi?

---

### Post by phrostbyte on 2009-12-27
I'm sorry, I didn't see anything about Wubi in the release notes.

Wubi is useful for converting a machine running Windows to Ubuntu which lacks a CD drive (ie. netbook), and you don't have any spare USB keys lying around.

---

### Post by theozzlives on 2010-01-04
> **garvinrick4 said:**
> Use karmic wubi and:

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade


Will do until they put Wubi on the installation Disk.

This don't help when Karmic WUBI don't boot. It just goes to the GRUB prompt.

---

### Post by phillw on 2010-01-04
> **theozzlives said:**
> This don't help when Karmic WUBI don't boot. It just goes to the GRUB prompt.

Would that be **> [B]sh:grub >**[/b]
?

If it is, head over to posting #62 here --> [http://www.ubuntuforums.org/showthread.php?t=1314064&page=7]("http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7")

Do pop back on & let me know how you get on.

Regards,

Phill.

---

### Post by wilee-nilee on 2010-01-04
> **phrostbyte said:**
> I'm sorry, I didn't see anything about Wubi in the release notes.

Wubi is useful for converting a machine running Windows to Ubuntu which lacks a CD drive (ie. netbook), and you don't have any spare USB keys lying around.

But leaves you without a live ISO to repair with.

---

### Post by theozzlives on 2010-01-05
> **phillw said:**
> Would that be ****
?

If it is, head over to posting #62 here --> [http://www.ubuntuforums.org/showthread.php?t=1314064&page=7]("http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7")

Do pop back on & let me know how you get on.

Regards,

Phill.

I just installed Jaunty and upgraded. My goal was to try to get Lucid in WUBI, but it choked on my nVIDIA drivers and wouldn't start X.

---

### Post by Brinstar on 2010-02-28
maybe this should be a new thread, but i have just downloaded the Lucid 64bit Alpha 3 iso, and wubi wants me to download the Jaunty iso! what is wrong?

edit: just checked md5sum , its fine, so thats not the problem

---

