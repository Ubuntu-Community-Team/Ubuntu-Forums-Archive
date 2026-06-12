---
title: "Feisty Un-Installer"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2007-05-02
Hi

Having converted so many people over to Ubuntu (Dual Boot) since the Feisty launch I guess it had to happen...

One of the Philistines wants to have it un-installed :( 

I guess like all well thought out programs the development gurus will have already addressed this and have it as a standard 'Click a Button' option

Can you tell me where it is please?

Thanks

W@LT

---

### Post by Tomosaur on 2007-05-02
> **W@LT said:**
> Hi

Having converted so many people over to Ubuntu since the Feisty launch I guess it had to happen...

One of the Philistines wants to have it un-installed :( 

I guess like all well thought out programs the development gurus will have already addressed this and have it as a standard 'Click a Button' option

Can you tell me where it is please?

Thanks

W@LT

You can't uninstall an Operating System as there's nothing to revert to. You just have to format the partition it is on, this can be done through the LiveCD.

---

### Post by ajgreeny on 2007-05-02
> **Tomosaur said:**
> You can't uninstall an Operating System as there's nothing to revert to. You just have to format the partition it is on, this can be done through the LiveCD.

Be warned, however, if you are dual booting, doing this will remove the grub menu.lst which grub uses to boot into either windows or ubuntu.  You will then need to restore the windows MBR in order to boot into windows again.

---

### Post by W@LT on 2007-05-02
sorry... should have mentioned they are dual boot

Just let me know what button to press to recover back to the original XP state.

Thanks

---

### Post by Tomosaur on 2007-05-02
> **W@LT said:**
> sorry... should have mentioned they are dual boot

Just let me know what button to press to recover back to the original XP state.

Thanks

It is more than one operation:

1) First of all, ensure you have some method of booting into XP. If you have the Windows XP Recovery disk, boot from that, enter the recovery console, and type 'fixmbr'. This should stop grub from booting, and only Windows will boot next time. If you don't have the Recovery disk, you need to look up about bootloaders on the net. I reccommend GAG.

2) After you have ensure you can boot into XP without Grub, boot from the Ubuntu LiveCD, and open up the partitioner (It is in the system menu). Simply select the Linux partitions (the one(s) with the system on, and the swap) and format them to some other filesystem. Hey presto, Linux is gone.

---

### Post by W@LT on 2007-05-02
Not the easiest of tasks then? .. I guess the developers did not reckon any anyone not liking it!!

I had Beryl working a treat for them ... emails and contacts migrated etc ..etc ... etc...

Anyway.. all this seems within my basic understanding and I will give it a go later

Thanks for all your help

W@LT

---

### Post by crane on 2007-05-02
I don't think it's a question of the developers thinking no one would like it Like mentioned earlier, there is nothing to uninstall to. But once you  repair Windows MBR, be sure to format the partition Linux was on. Windows cannot read linux formats. Reformating to to NTFS would allow them to use the partition.

---

### Post by Tomosaur on 2007-05-02
> **W@LT said:**
> Not the easiest of tasks then? .. I guess the developers did not reckon any anyone not liking it!!

I had Beryl working a treat for them ... emails and contacts migrated etc ..etc ... etc...

Anyway.. all this seems within my basic understanding and I will give it a go later

Thanks for all your help

W@LT
That's not the case at all - the developers don't assume everyone is running Windows, and they don't supply a method to fix the MBR because a) it's not their responsibility, and b) they'd probably get sued by Microsoft.

---

### Post by ajgreeny on 2007-05-02
Just remember there's no "One click" method of removing windows either, so it's not just ubuntu that has this "problem"

---

### Post by Herman on 2007-05-02
I'm not sure it's a problem, it could be a feature. :) Imagine the caos if there *was* a button people could push to uninstall?  :lolflag:

Edit: Sorry for my sillyness, possibly I'm the only one who thinks that's funny. Actually I partially agree with you and I anticipated that problem a long time ago when I was making my Ubuntu install web site for the 'Alternate CD'. If you click on my first sig link you will see that in the index of my home page I have placed the link for how to ininstall Ubuntu first, above the installation links. I thought it seemed logical that people would first want to know how to undo what they were thinking of doing before they would want to go ahead. 
You will find it well explained there and several methods are even ilustrated, or else at least have good links to other sites. If you find anything lacking in that page, just let me know and I'll try to improve it.

Regards, Herman :)

---

