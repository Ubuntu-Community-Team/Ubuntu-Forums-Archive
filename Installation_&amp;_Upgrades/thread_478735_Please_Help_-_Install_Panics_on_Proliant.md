---
title: "Please Help - Install Panics on Proliant"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by RMWChaos on 2007-06-19
I think that I need to modify the bootup files on the installation CD so that it will recognize memory above 16MB on my Proliant 2500. In the past, I could install Linux but then would have to modify the LILO bootloader to include the following commands:

[INDENT]linuxmem=exactmap[/INDENT]
[INDENT]mem=15m@1M[/INDENT]
[INDENT]mem=48m@16M[/INDENT]
[INDENT]mem=64m@64M[/INDENT]

I learned this when running Red Hat 7.3. With Ubuntu 7.04, I keep getting kernel panics with either the Live CD or alternate images right after I select the Install option. I am assuming the problem is the memory limitation.

Can anyone help? I used IZArc to extract the ISO image, and now I just need to know which file(s) to modify, and perhaps what commands to use if it is not the same as above.

Perhaps I should install 6.06 LTS then upgrade to 7.04?

Thanks in advance for any assistance!

---

### Post by RMWChaos on 2007-06-19
Tried 6.06 LTS and had a similar kernel panic. I noticed that I can press F6 to edit what I think are boot options. Perhaps I can add the memory lines here? I will try that next.

---

