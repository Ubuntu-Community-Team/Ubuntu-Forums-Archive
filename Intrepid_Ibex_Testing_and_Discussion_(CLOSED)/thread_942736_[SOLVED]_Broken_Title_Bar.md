---
title: "[SOLVED] Broken Title Bar"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by codemaster on 2008-10-09
I have had an issue since yesterday concerning my setup in Intrepid. I updated and (later) rebooted to find all of my text at a very large size and a very odd setup for my title bar - almost seemed like my themes were broken (although after inspection, they were properly configured).

I was able to fix my "huge text" problem by adding the following to my xorg.conf's Device section
[quote=xorg.conf]
Option         "UseEdidDpi" "False"
Option         "DPI" "96 x 96"
[/quote]
although I didn't think it was a Xorg issue...

Nonetheless, this leaves my only issue being the title bar oddity. I have attached a screenshot for reference.

I am using Compiz and the nVidia 177 driver, if that helps.

---

### Post by codemaster on 2008-10-09
I was able to solve this issue by simply reinstalling metacity such as:
[quote=Terminal]
sudo aptitude reinstall metacity metacity-common
[/quote]

---

