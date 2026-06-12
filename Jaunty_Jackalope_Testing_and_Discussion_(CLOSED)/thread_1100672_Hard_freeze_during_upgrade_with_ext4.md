---
title: "Hard freeze during upgrade with ext4"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-03-19
I got a hard freeze during upgrade of libvolume_id today with ext4. It made my system unusable and I had to reinstall it, then I used ext3 instead and was able to fully upgrade. Anyone else noticed this? Is it likely is it because of ext4?

---

### Post by taavikko on 2009-03-19
Didn't notice anything like that...

But the latest libvolume_id upgrade was on the 13.03.2009.
At least on my setup...
**grep -i libvolume /var/log/dpkg.log**

Could the hdd just hit a bad block, so that triggered the freeze?

---

### Post by olskar on 2009-03-19
> **taavikko said:**
> Didn't notice anything like that...

But the latest libvolume_id upgrade was on the 13.03.2009.
At least on my setup...
**grep -i libvolume /var/log/dpkg.log**

Could the hdd just hit a bad block, so that triggered the freeze?

Perhaps, I did run a fsck afterwars however but id said it was clean.

---

