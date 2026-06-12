---
title: "Recover overwritten partition with Testdisk"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by IreneLing on 2013-04-12
Hello all.

I accidentally overwrote my partition from Ubuntu to Android-x86. I used testdisk to search for the previous partition while using Ubuntu  from USB , and here is the result :

**After quick scan:**

[IMG]http://img545.imageshack.us/img545/222/quickscan.png[/IMG]
[B]
Deeper scanning: [/B]

[IMG]http://img12.imageshack.us/img12/5961/deeperscan.png[/IMG]


**After Deeper scan:**

[IMG]http://img707.imageshack.us/img707/6137/finishdeeperscan.png[/IMG]

**Deeper scan results:**

[IMG]http://img19.imageshack.us/img19/2060/deeperscanresult.png[/IMG]


**Only second row able to list its files , the rest are damaged:**

[IMG]http://img27.imageshack.us/img27/6647/resultp1.png[/IMG]


**Before reboot :**

[IMG]http://img801.imageshack.us/img801/8249/aftersetl.png[/IMG]

Since only one partition is available , so I changed it to L and reboot , but it shown Error 17.
And I read some thread regarding the error and changed the partition to P , reboot again , but it is the Android-x86 again.

This is the first time I use Testdisk , and do not understand much about partition,disk drive etc....Wonder is my overwritten Ubuntu still exist ? is it still able to be recovered ? If not , I will need to reinstall Ubuntu with tears now.

Thank you.

---

### Post by darkod on 2013-04-12
When changing the characteristic of the Linux partition, make it * (primary bootable). For the Linux Swap partition make it L (logical).

In any case you will need to reinstall grub2 since it was probably destroyed. I suggest to first recover the partitions and see if you can access the data from live mode.

If you can, reinstalling grub2 on the MBR is easy to do.

But why aren't there more folders when listing the content of the Linux partition? I'm afraid this linux partition might be from android and your ubuntu data might be lost.

---

### Post by IreneLing on 2013-04-13
> **darkod said:**
> When changing the characteristic of the Linux partition, make it * (primary bootable). For the Linux Swap partition make it L (logical).

In any case you will need to reinstall grub2 since it was probably destroyed. I suggest to first recover the partitions and see if you can access the data from live mode.

If you can, reinstalling grub2 on the MBR is easy to do.

But why aren't there more folders when listing the content of the Linux partition? I'm afraid this linux partition might be from android and your ubuntu data might be lost.

Thank you so much for your reply.

I'm not sure why there is so less folders listed , and yes I think the Linux partition is already completely deleted....I follow your instruction but it still direct to Android.

Guess I need to reinstall Ubuntu , and really thanks for your instruction which might be useful for me in future.

---

