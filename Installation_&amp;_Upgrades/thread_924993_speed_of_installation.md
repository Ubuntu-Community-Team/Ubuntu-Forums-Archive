---
title: "speed of installation"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-09-20
Hi,
Recently a friend of mine asked me the question 

Will Increasing swap space increases the speed of installation of ubuntu ? (systems having >= 512 mb of RAM)

what exactly is the correct answer ?

---

### Post by Sef on 2008-09-20
With 512 mb ram, have your friend make their swap partition 1 GB.  No more will be needed.  If a bigger one is needed, then get more ram.

---

### Post by wpshooter on 2008-09-20
> **Sef said:**
> With 512 mb ram, have your friend make their swap partition 1 GB.  No more will be needed.  If a bigger one is needed, then get more ram.

I don't exactly understand how this answers the posters question.

---

### Post by Pumalite on 2008-09-20
I think it answers it great. I GB of /swap is enough and it doesnt have anything to do with speed of installation. That depends more on a good CD and the speed of your CPU.

---

### Post by wpshooter on 2008-09-20
> **Pumalite said:**
> I think it answers it great. I GB of /swap is enough and it doesnt have anything to do with speed of installation. That depends more on a good CD and the speed of your CPU.

Sef, did not say one way or another as to whether a greater amount would speed up the **INSTALLATION** of the O/S.  They just gave a recommendation as to HOW MUCH they thought should be alloted to the swap !!!

I think the posters question was, would the O/S **installation** (as opposed to the actual operation of the O/S) be accomplished quicker if say 5gb was alloted to swap as say opposed to 2gbs.  Or at least that's what I interpreted the question to be.

---

### Post by manishtech on 2008-09-20
I am unable to figure out how swap space can increase installation. As Pumalite said, it depends on the quality of CD, its absolutely correct.

If you are using LiveCD cum installer, you can boost up the installation process a bit by first partitioning the disk with required space for / and swap. The swap should be formatted with required fileystem. Now reboot again from the LiveCD, ubuntu detects the swap partition and uses is to run in Live mode also. It gives it a bit performance edge. So now atleast during installation something called freezes cant be encountered.

---

