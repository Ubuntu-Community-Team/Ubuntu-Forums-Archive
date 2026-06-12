---
title: "Ubuntu not Booting from Promise mb133 Raid"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by tcjmiami on 2007-08-21
I have installed Ubunto version 6 on Tyan 1u servers with Promise MB133 Lite Raid 1 controllers.
The OS installs properly but the system will not boot from the array.
I can boot from the CD with no problem and the OS is on the array.
I have also apllied all current patches and it made no difference.
I am downloading version 7 now but I do not know if it will make any difference.
Any help would be appreciated.

Thank you 

Tom

---

### Post by heimo on 2007-08-21
> **tcjmiami said:**
> I have installed Ubunto version 6 on Tyan 1u servers with Promise MB133 Lite Raid 1 controllers.

It's a fake raid controller, isn't it? Requires driver to work? See this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

