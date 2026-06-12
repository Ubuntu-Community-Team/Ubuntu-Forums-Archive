---
title: "LUCID-Confirm Live CD's &quot;Test CD&quot; feature not working"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-01-25
I have tried this on 2 machines a ISO image of the Alpha2 X86.  I get the disk activity light, then a transition to the Ubuntu monochrome logo screen, and then nothing further.

Yes I know it's Alpha, but this may be a bug to report.  Anyone else seeing this?

Thanks

---

### Post by VMC on 2010-01-25
> **emarkay said:**
> I have tried this on 2 machines a ISO image of the Alpha2 X86.  I get the disk activity light, then a transition to the Ubuntu monochrome logo screen, and then nothing further.

Yes I know it's Alpha, but this may be a bug to report.  Anyone else seeing this?

Thanks

Is the "Test CD", the verify cd? If so, I had that also. I removed quiet to see what's happening. Its been a while but I used md5sum to verify. I believe there's a bug report against this.

---

### Post by phillw on 2010-01-25
> **VMC said:**
> Is the "Test CD", the verify cd? If so, I had that also. I removed quiet to see what's happening. Its been a while but I used md5sum to verify. I believe there's a bug report against this.

Indeed there is, it lives over here --> [https://bugs.launchpad.net/ubuntu/lucid/+source/cdrom-checker/+bug/500198](https://bugs.launchpad.net/ubuntu/lucid/+source/cdrom-checker/+bug/500198)

Regards,

Phill.

---

### Post by emarkay on 2010-01-25
> **phillw said:**
> Indeed there is, it lives over here --> [https://bugs.launchpad.net/ubuntu/lucid/+source/cdrom-checker/+bug/500198](https://bugs.launchpad.net/ubuntu/lucid/+source/cdrom-checker/+bug/500198)
Regards,
Phill.


Yea, that's it - thanks.

---

