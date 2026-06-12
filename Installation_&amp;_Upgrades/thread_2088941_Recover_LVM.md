---
title: "Recover LVM"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Sam1994 on 2012-11-27
Hi,
 
Need help.
 
I setup LVM on a box and transferred some files to a logical volume. Installed Ubuntu on the box after exporting the volumegroup. So, I have no backup of LVM.
 
Now, on my box, I did this:
 
vgimport vg01
 
vgdisplay shows no PE allocated and no volumes available.
 
Anything I can do to get the volume back?

---

### Post by darkod on 2012-11-28
I haven't tried export/import procedure of LVM, but in order to use LVM you need to activate it with something like:
sudo vgchange -ay

Provided all the necessary info is there, it should activate it and list the available LVs.

---

### Post by Sam1994 on 2012-11-28
> **darkod said:**
> I haven't tried export/import procedure of LVM, but in order to use LVM you need to activate it with something like:
sudo vgchange -ay
 
Provided all the necessary info is there, it should activate it and list the available LVs.
 
I have tried this and it tells me 0 logical volumes available. lvdisplay shows no logical volumes available either.

---

### Post by darkod on 2012-11-28
lvdisplay is after they are activated. For searching before LVM is activated you use pvscan, vgscan and lvscan.

But even without any search vgchange should activate all LVM devices it finds.

It seems the export/import process was not done successfully. So because of that, vgchange is not activating any LVM because there is none to activate. See if pvscan can detect any physical devices at all.

---

### Post by Sam1994 on 2012-11-28
> **darkod said:**
> lvdisplay is after they are activated. For searching before LVM is activated you use pvscan, vgscan and lvscan.
 
But even without any search vgchange should activate all LVM devices it finds.
 
It seems the export/import process was not done successfully. So because of that, vgchange is not activating any LVM because there is none to activate. See if pvscan can detect any physical devices at all.
 
I have done the respective pvscan, lvscan, vgscan. The vg was detected automatically as exported so I imported it. But no lvs are showing. I'm wondering why the heck it's disappeared, along with a good 2TB of data

---

### Post by darkod on 2012-11-28
I have no clue. Maybe the export procedure was missing something, for example it might not have exported the LVs as you expected.

I assume you no longer have the original disks?

---

### Post by Sam1994 on 2012-11-28
> **darkod said:**
> I have no clue. Maybe the export procedure was missing something, for example it might not have exported the LVs as you expected.
 
I assume you no longer have the original disks?
 
I do not, no.

---

### Post by darkod on 2012-11-28
In that case it doesn't look good. If the LVM was OK, then vgchange would activate it and the LVs would be ready for use. There is not much procedure to it.

I am surprised you decided to do export instead of simple copy of the data. You still needed space to guard the export, so it would have been much better to simply copy the data there.

---

### Post by Sam1994 on 2012-11-28
> **darkod said:**
> In that case it doesn't look good. If the LVM was OK, then vgchange would activate it and the LVs would be ready for use. There is not much procedure to it.
 
I am surprised you decided to do export instead of simple copy of the data. You still needed space to guard the export, so it would have been much better to simply copy the data there.
 
So you are using it's against LVM best-practice to export and import? How can you transfer, using same set of drives, to another box then

---

### Post by darkod on 2012-11-28
I'm not sure I understood correctly. You are talking about moving the same disks from one machine to another?

Simply connect the disks into the new machine and activate the LVM with the already mentioned:
sudo vgchange -ay

That's all. The LVs with all data will be available.

If the OS is actually onto the LVM you would need do few more steps but the principle is the same. If the LVM is only for data, no OS, then only moving the disks and doing the vgchange should be enough.

---

### Post by Sam1994 on 2012-11-28
> **darkod said:**
> I'm not sure I understood correctly. You are talking about moving the same disks from one machine to another?
 
Simply connect the disks into the new machine and activate the LVM with the already mentioned:
sudo vgchange -ay
 
That's all. The LVs with all data will be available.
 
If the OS is actually onto the LVM you would need do few more steps but the principle is the same. If the LVM is only for data, no OS, then only moving the disks and doing the vgchange should be enough.
 
0 lvms available. Physical extent allocated is 0. It is messed up

---

### Post by darkod on 2012-11-28
> **Sam1994 said:**
> 0 lvms available. Physical extent allocated is 0. It is messed up

We agree on that. It seems it got messed up sometime during the export/import.

My previous post was about how would I move disks with LVM to another machine. I wouldn't use any export/import, only moving the disks and reusing them again in the new machine.

As for your current situation, it sounds like there is nothing much that can be done. Nothing that I know about.

---

### Post by Sam1994 on 2012-11-28
Hi
 
You are missing my point. I've tried this. The volume group shows, but when I perform the defacto method for importing I get
 
No logical volumes

---

### Post by darkod on 2012-11-28
Well, there seems to be a serious misunderstanding. When you use terms like export and import, that means actually doing an export and import procedures.

What I am talking about is simply activating existing LVM devices with vgchange which I do not consider as import operation. You are not exporting anything, and not importing anything.

In your very first post you actually said you used vgimport, which is not what I am talking about.

Right now, doing vgchange could be pointless if the vgexport/vgimport procedure didn't transfer the data as you expected, right? And it obviously didn't.

If you did have the original disks moved to a new machine, vgchange would be enough to get the LVM device going, I'm sure of that. That's what I am talking about. But you don't have them any more.

The export/import messed you up somehow.

Look what this article says: The export/import procedure is NOT to move the data, it is to simply block the LVM from being used until you move it. But you DO physically need to move the disks to another machine. Is that what you did?
[http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

---

