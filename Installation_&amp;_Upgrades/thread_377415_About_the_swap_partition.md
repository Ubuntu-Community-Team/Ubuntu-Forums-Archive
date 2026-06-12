---
title: "About the swap partition"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by GeertPoels on 2007-03-06
Hi all,

I'd like to have some facts nailed down about the need, the location and the size of a swap partition. :) 

Google is filled with HOWTOs and manuals from the 90's where the general rule of thumb is swap size = MEM * 2.  With today's hardware, this no longer seems to be necessary.
Also on the forums, there are just too many opinions and suggestions floating around, some of which are contraditory.

This interesting read dates already from 2004
[http://sourcefrog.net/weblog/software/linux-kernel/swap.html](http://sourcefrog.net/weblog/software/linux-kernel/swap.html).

I'd like to know the 2007 rule.  
- new computers have 1 and even 2 and more GB RAM.
- kernelversion is 2.6

I suppose there's quite some difference for somebody just surfing and writing documents (a regular desktop system) or someone doing video manipulation or a loaded server.

Apparently, even with a very large memory, swapspace still makes a difference.
Can swap space reside at any location of the HD ?
Any limit to the size of the swap partition ?

Geert

---

### Post by Kateikyoushi on 2007-03-06
Of course swap useage is determined by what do you do on the machine and the ram the double the ram rule should be forgotten.

I have 256 MB swap for browsing email and wordprocessing and other common things on my notebook with 512Mb ram and it is enough.

Because diskspace is so cheap set it for 1GB and should be more than enough, you can resize it later anyway.

Swap can be anywhere on the disc but as I remember needs to be 256MB at least the installer insists. Of course only if you want one, can live without as well.

---

