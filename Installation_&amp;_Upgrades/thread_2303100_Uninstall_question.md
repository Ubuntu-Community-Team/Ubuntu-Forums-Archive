---
title: "Uninstall question"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by DonBucknall on 2015-11-16
Hi all!

I followed this guide:
[http://www.radiusdesk.com/getting_started/install_ubuntu_freeradius](http://www.radiusdesk.com/getting_started/install_ubuntu_freeradius)

But I want to undo the installation, how do I make sure everything unuseful is deleted?

Cheers,

Don

---

### Post by ian-weisser on 2015-11-19
Very slowly and painfully.
You must work backwards though your install guide, manually uninstalling each component you installed, manually undoing each setting you changed, manually deleting each file you created.
There is no way to be *sure* you deleted it all beyond meticulousness, and an understanding of your system. You chose an install method that requires those.
You may get a better answer in the FreeRadius forums, if any.

The long and complex process of installing and uninstalling software manually is why we generally use *software packages*.
Had you used the fine version of Freeradius in the Ubuntu Software Center (yes, it's there), then install and uninstall would be trivial for you.

A disposable VM is another useful way to experiment with unpackaged software.

---

