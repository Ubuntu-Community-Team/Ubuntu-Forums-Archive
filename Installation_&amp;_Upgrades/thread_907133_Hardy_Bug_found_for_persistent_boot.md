---
title: "* Hardy: Bug found for persistent boot *"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-09-01
Hi,
After going bonkers as to why the 'casper-rw' partition wont mount on boot up, i found a bug in the 'casper-helper' script, in the 'initrd'.

The function 'find_cow_device' has the following:

[COLOR="DarkRed"]echo "$device"
return[/COLOR]

Obviously, you see it should have been 

[COLOR="darkred"]echo "${device}"[/COLOR]

After making this fix, my persistence works!!!

But I have _never_ seen this fix, for all the amount I have googled.

So does it work for some?!@:confused:

Anyways, for me, I had to make this fix, after sifting and debugging through a lot of code.

I think my Kernel is: 2.6.18 (Will confirm in sometime, when I boot into it, On Kubuntu 8.04).

Please let me know if this indded is a bug, and we need to raise it.

---

