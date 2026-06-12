---
title: "Partition mount names as shown in Places menu"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Lantesh on 2008-05-01
I've got a question pertaining to a change I noticed in Hardy.  Let me give you my setup first.  I am running a Tri-boot system with Windows XP, Edubuntu 8.04, and Linux Mint Daryna (based on Gutsy Gibbon).

In the past with both Gutsy Gibbon and Mint Daryna I have always mounted my other partitions in /media in folders named after what they are.  For example in my Mint installation I have my Windows partition mounted in /media/Windows.  So in the Places menu it simply says Windows.  When I open a Nautilus window over in the left pane under places in says Windows.  I like this.  It makes it easy to identify what partitions are what by having the mounted folder names display in this fashion.

Now here is my problem.  In Hardy (my Edubuntu installation) in the Places menu, and in the Nautilus Places pane it is not displayed this way.  It just says something like "35 gig partition" for Windows, instead of "Windows".  All my partitions are doing this.  Yet when I look in /media all are mounting in the correct folders just as I've assigned in fstab.  So what gives with the Places menu.  Does Hardy no longer use the mount folder name in Places?

Any guidance is appreciated, and if you are having the same issue let me know here.  If I find the answer somewhere else I'll post back.

---

### Post by Lantesh on 2008-05-01
Well nobody chimed in here, but I thought I'd post back with the solution I came up with in case it will help someone else.


I actually found an interesting work around for this. What I did was change the folder where the drives are mounted to from /media to a new folder I created called /partitions (updated fstab of course). By doing this the system no longer puts drive icons in the "Places" menu for the partitions at all. I then simply did a click and drag on the new sub folders I'd made inside /partitions, which were /partitions/Windows, /partitions/Mint, and /partitions/Storage, and drug them over to the Places menu to create shortcuts. These new shortcuts show in both the "Places Menu", and the "Places Pane" in Nautilus.  The only difference is that instead of looking at drive icons I am looking at folder icons, which makes no difference to me, and if I really wanted to I could change the icons.  Anyway I hope this helps someone else.

---

### Post by mikewhatever on 2008-05-01
That looks like a very nice trick. I'm definitely going to try it when installing Hardy.:KS

---

### Post by Lantesh on 2008-05-02
mikewhatever, thanks for the reply.  I'm glad this info will help someone else.

---

