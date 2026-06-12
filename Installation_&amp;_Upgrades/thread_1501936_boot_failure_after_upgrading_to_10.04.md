---
title: "boot failure after upgrading to 10.04"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Leporello on 2010-06-04
I recently tried to upgrade from Xubuntu 9.10 to 10.04. Unfortunately, the computer now hangs on bootup, and I can't even get a command line. When I try to boot I get some of the following error messages (these are the ones I could catch as they scolled by):

```
mount: mounting none on /dev failed: No such device

/usr/sbin/nmbd: relocation error: /usr/lib/libkrb5.so.3: symbol krb_hmac, version k5crypto_3_MIT not define in file libk5crypto.so.3 with link time reference

* Starting Common Unix Printing System: cupsd
/usr/sbin/cupsd: relocation error: /usr/lib/libkrb5.so.3: symbol krb_hmac, version k5crypto_3_MIT not define in file libk5crypto.so.3 with link time reference


Checking battery state...

end_request: I/O error, dev sr0, sector 1394864
```

And then the boot hangs. Now, I didn't reboot the computer myself, so it's possible (although unlikely) that it was rebooted before the upgrade was finished. The fact that it appears to be searching for libraries that aren't present does seem to suggest that the upgrade got interrupted somehow, but I could be misinterpreting the above. At any rate, it would be great to get this computer working again without reinstalling everything. Is there any hope of doing that?

---

