---
title: "A cleaner Nautilus computer"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pt123 on 2009-12-12
In Jaunty the computer:/// of Nautilus was very neat. It only showed you the name of the partition and not the size of the hard disk it is on (like KK and LL)

Is there anyway of removing the eyesore "500 GB Hardisk:" in front of the drives. It is rather unnecessary and takes the focus from most info the Name/Label/MountPoint of the partition. Or it should be shown in a smaller and lighter text below the Name/Label/MountPoint.

attached are screenshots of now (KK LL) and before (on Jaunty)

---

### Post by emigrant on 2009-12-12
im using jaunty and still i have the drive size infront of the drive name :confused:
is that becaume im using humanity icon of karmic?

---

### Post by pt123 on 2009-12-12
sorry the thumbnails were in the wrong order it is fixed now

---

### Post by Gina on 2009-12-12
Particularly annoying with only one drive! :(

---

### Post by pt123 on 2009-12-12
true even if you have more drives, when one has given a label for a partion there is no need to mention how large the drive the partition sits on, after all it is limited by the partition side.

---

### Post by pt123 on 2009-12-29
added a bug report
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/501440](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/501440)

---

### Post by sudoer541 on 2009-12-29
> **emigrant said:**
> im using jaunty and still i have the drive size infront of the drive name :confused:


I dont

---

### Post by pelle.k on 2009-12-29
> **emigrant said:**
> im using jaunty and still i have the drive size infront of the drive name :confused:
is that becaume im using humanity icon of karmic?

Labels! Read up on e2fslabel, or ntfslabel if that is what you are using...

---

### Post by durand on 2009-12-30
Totally agree with the OP. Those labels are completely pointless and really annoying. They don't even tell you the size of the partition, just the drive. I don't want 15 icons telling me that I have a 250GB hard drive :(

---

### Post by pt123 on 2009-12-30
^ add your comment to the bug report 
[https://bugs.launchpad.net/bugs/388904](https://bugs.launchpad.net/bugs/388904)

---

### Post by Seventh Reign on 2009-12-31
I disagree.  When you have 5 or 6 different USB Drives along with 3 or 4 internal ide and sata HDDs connected all with different drive sizes.  Those numbers become very important.  Would you rather have to open each drive individually to see what is in each one?

---

### Post by dino99 on 2009-12-31
> **Seventh Reign said:**
> I disagree.  When you have 5 or 6 different USB Drives along with 3 or 4 internal ide and sata HDDs connected all with different drive sizes.  Those numbers become very important.  Would you rather have to open each drive individually to see what is in each one?

Report your opinion against the bugs order listed above before devs revert it.

---

### Post by philinux on 2009-12-31
> **pt123 said:**
> In Jaunty the computer:/// of Nautilus was very neat. It only showed you the name of the partition and not the size of the hard disk it is on (like KK and LL)

Is there anyway of removing the eyesore "500 GB Hardisk:" in front of the drives. It is rather unnecessary and takes the focus from most info the Name/Label/MountPoint of the partition. Or it should be shown in a smaller and lighter text below the Name/Label/MountPoint.

attached are screenshots of now (KK LL) and before (on Jaunty)

Use System>admin>Disk utility and change the labels.
Simples

---

### Post by durand on 2009-12-31
> **philinux said:**
> Use System>admin>Disk utility and change the labels.
Simples

That doesn't help. Most of my partitions are already labelled.

See the screenshot attached.

---

### Post by pt123 on 2009-12-31
> **Seventh Reign said:**
> I disagree.  When you have 5 or 6 different USB Drives along with 3 or 4 internal ide and sata HDDs connected all with different drive sizes.  Those numbers become very important.  Would you rather have to open each drive individually to see what is in each one?

If you haven't set up a label then it should use the drive sizes for the main info. Also it is possible to have the parttion sizes as secondary info.

There is suggestion that the current form is a result of an ugly hack to group all partitions on one drive next to each other. 

Even then it would better to have line of text with the drive info then with the partitions below icons.
```

500 GB Hard Disk
------------------------------
[icon1]  [icon2]   [ icon3]
Label1   Label 2  Label 3

```

---

### Post by pt123 on 2009-12-31
> **philinux said:**
> Use System>admin>Disk utility and change the labels.
Simples
I already had labels setup up that is why I don't need to have the useless 500GB repeated everywhere.

---

### Post by ranch hand on 2009-12-31
> **philinux said:**
> Use System>admin>Disk utility and change the labels.
Simples
I have no problem with the way this is now.  The only place this comes up is under "computer" which I never go to anyway.

However, I am not sure that we understand exactly what you are suggesting here.  All my partitions (used ones anyway) are labeled or I would have no clue where I was at any time in nautilus so I need this in the left panel.

It does leave the drive size on the partitions under computer.  Like I say I don't use that anyway.  I think that the best thing would be to be able to delete "computer" from the menu.

---

### Post by pt123 on 2009-12-31
^ not everyone uses the side pane in Nautilus, and there by Computer toolbar button is used to switch partions

---

