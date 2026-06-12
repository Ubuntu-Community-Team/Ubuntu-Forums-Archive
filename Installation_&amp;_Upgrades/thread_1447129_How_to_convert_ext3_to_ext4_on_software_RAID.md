---
title: "How to convert ext3 to ext4 on software RAID"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by rgotten on 2010-04-04
i have being testing a server for the past 4 moth. i have the boot on raid 1 and the swap on raid 1, the fylesystem on raid 5 and the data on raid 5. All of this is the ext3. this are my questions:
1) Is ext4 really superior to ext3
2) I have not found a lot of in formation on how to convert from ext3 to ext4 on software raid

Maybe i dont  need to do the conversion, but if there is a good moment to do it...this is it since i have not place any important data on the server, So if somebody can give me some guidance on how to do this, i will apreciate it

rgotten

---

### Post by rgotten on 2010-04-09
sony days and no replys..does anybody has an idea on how to do this..Thanks

---

### Post by Slim Odds on 2010-04-09
The fact that you're using RAID should be completely transparent to the file system.

But changes like this are always dangerous, so take the proper precautions.

---

